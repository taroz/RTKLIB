# Improvement of velocity estimation of RTKLIB
- Estimation of inter-system bias of Doppler frequency
- Validation of velocity estimation
- Output of valiance of velocity
- Output velocity even when position cannot be computed

# Setting1
<img src="https://user-images.githubusercontent.com/7933764/58242274-7812cb80-7d89-11e9-8879-9c2363810951.png" width="600px">

## Inter System Biases of Doppler Frequency
- **DISB**: This option estimates GPS-GLO, GPS-BDS, and GPS-GAL inter system biases of Doppler frequency (**pos1-posopt6 = ON**)

- Horizontal velocity error (Static test, GPS+GLO+BDS+GAL)   
![result](https://user-images.githubusercontent.com/7933764/58296100-51967400-7e0d-11e9-98fc-531a690757f6.png)
- Note: Additional observations are needed to estimate the bias. The availability of velocity will be decreased in urban environments.

# Output
<img src="https://user-images.githubusercontent.com/7933764/58243490-b4dfc200-7d8b-11e9-8dca-a8b1596e5723.png" width="600px">

## Output Velocity
- **Out Vel**: Output velocity in .pos file (**out-outvel = ON**)
- Format: ```vn(m/s) ve(m/s) vu(m/s) Q ns sdvn sdve sdvu sdvne sdveu sdvun```
![format](https://user-images.githubusercontent.com/7933764/58296331-455ee680-7e0e-11e9-9efc-cc025ba46450.png)

## Output All Solutions
- **Out All**: Output every solutions even when position cannot be computed (**out-outall = ON**)
- **Q=0**: Position or velocity cannot be computed due to lack of observations.The previous position or velocity is outputted.
- **Q=-1**: Position or velocity is rejected by validation (e.g. chi-square test)
![outall](https://user-images.githubusercontent.com/7933764/58296514-e8176500-7e0e-11e9-8c7d-975bef44c0e3.png)

# Statistics
<img src="https://user-images.githubusercontent.com/7933764/58295565-e3e94880-7e0a-11e9-8f6c-eb4a2b4af570.png" width="600px">

## Doppler frequency (Hz)
- Standard deviation of Doppler frequency error (Hz) : SD_Doppler
- Current error model is as follows: ```sd = SD_Doppler/sin(elevation)```
