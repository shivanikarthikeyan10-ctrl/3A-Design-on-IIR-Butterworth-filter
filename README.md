# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc ;
close ;
wp=input('Enter the pass band frequency (Radians )= ' );
ws=input('Enter the stop band frequency (Radians )= ' );
alphap=input( ' Enter the pass band attenuation (dB)=' );
alphas=input( ' Enter the stop band attenuation(dB)=' );
T=input('Enter the Value of sampling Time=');
//Pre warping- Bilinear Transformation
omegap=(2/T)*tan(wp/2);
disp(omegap,'omegap=');
omegas=(2/T)*tan(ws/2);
disp(omegas,'omegas=');
//Order of the filter
N=log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap));
disp(N,'N=');
N=ceil(N);
disp(N,'Round off value of N=');
//Cut off frequency
omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N)));
disp(omegac,'omegac=');
disp('Normalised Analog LPF Transfer function H(S)=');
hs_Normalised = analpf(N,'butt',[0,0],1);
disp(hs_Normalised);
disp('Analog LPF Transfer function H(S)=');
hs= analpf(N,'butt',[0,0],omegac);
disp(hs);
z=poly(0,'z');//Defining variable z
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation
disp('Digital LPF Transfer function H(Z)=');
disp(Hz);
HW=frmag(Hz,512); // Frequency response
w=0:%pi/511:%pi ;
plot(w/%pi,abs(HW));
xlabel(' Normalized Digital Frequency w');
ylabel('Magnitude ');
title(' Frequency Response of Butterworth IIR LPF');
```

# OUTPUT: 
<img width="1367" height="621" alt="image" src="https://github.com/user-attachments/assets/5c05820c-0fdb-43a4-9b5a-d9597175ebac" />

# CALCULATION:

<img width="1022" height="1544" alt="image" src="https://github.com/user-attachments/assets/5a4c1d76-5528-432d-93eb-616ffd5f1fef" />

<img width="995" height="1514" alt="image" src="https://github.com/user-attachments/assets/dd51c757-45cf-4183-86e9-dfe22839593b" />

<img width="861" height="1391" alt="image" src="https://github.com/user-attachments/assets/73b92103-5993-42cf-8305-da570e14061a" />

<img width="902" height="1439" alt="image" src="https://github.com/user-attachments/assets/685b29be-be0d-428d-a364-991406e5fe06" />


# RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.

