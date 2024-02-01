clc;
clear all; % clear all varaiables
close all; % close all figures
load('111m.mat')
y1=val(1,:);
fs=1000;
ts=1/fs
f0=108;
% Fs=1000;
% ts=1/Fs;
N1=length(y1);
t=((0:N1-1)*ts)/fs;
% fs=540;
% f0=108;
w1=2*pi*f0*t;
x1=30*sin(w1);
x2=x1+y1;
k=fft(x2);
a=[1,-0.618,0.999882];% INITIALISING VECTOR A WITH COEFFICIENTS
OF THE NUMERATOR;
b=[1,-0.5014,0.65835]; %INITIALISING VECTOR B WITH COEFFICIENTS
OF THE DENOMINATOR;
y=filter(a,b,x2); %TIME DOMAIN OF OUTPUT FILTER
w = fft(y);
subplot(2,2,1)
plot(t,x2);
title('Input Of filter');
subplot(2,2,2)
plot(t,k);
title('Input frequency response Of filter ');
subplot(2,2,3)
plot(t,y);
title('Output Of filter');
subplot(2,2,4)
plot(t,w);title('frequency response Of filter o/p');
