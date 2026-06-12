---
title: "Fan runs at greater speed in Karmic Core i3 CPU , ATI  4530"
date: 2010-02-16
forum: Hardware
---

### Post by spiritson on 2010-02-16
I purchased a new DELL laptop with the following configuration

Intel Core i3 350M @ 2.27ghz , 4GB RAM
Manufacturer	
Mother board Model	Dell Inc. 0VF0FR
BIOS version A02
Chipset vendor	Intel ID0044
Southbridge vendor	Intel ID3B09 (rev 05)
ATI Mobility Radeon HD 4530  

The problem is fan speed. In Karmic[Kernel 2.6.31] the fan seems to run at higher speed (clearly audible) for idle conditions also.

While in Windows 7 the fan speed do not increase till i stress it with heavy tasks.

I have tried lm-sensors and my CPU is not supported.

I have installed latest ATI drivers which solved the problem partially.

As i could not get lm-sensors work My experimentation goes like this..

I used external decibel meter to know the sound the laptop fan makes.(Fixed the position without altering for whole experiment)

***For windows 7:***

Initial boot up process the average sound level of Fan is** 94.4 dB** : MAX STATE

When OS completely loads and comes to idle state the dB level comes down to **84.3 dB** average. : MEDIUM STATE

And with a 2 minutes of idle state the sound level of fan comes down to **74.5 dB** and stays there. : LOW STATE

When i stress the cpu like watching encoding video the dB level rises to MEDIUM STATE and immediately comes down to LOW STATE when process ends.

The cpu temperatures are for 
MAX : 51-55 C 
MEDIUM : 46-49 C 
Low: 39-41 C 

***For Karmic 9.10 :***

Boot up process gives sound levels of 93.8dB : MAX STATE

When OS completely loads gives 84.1 dB : MEdIUM STATE

then even when the system remains IDle for 15 minutes also it does not LOW STATE and the sound levels do not decrease 82 dB.

For 3-7 seconds the dB levels come to LOW STATE ( happens every 1 minute roughly) and go back to 84 dB without any user interaction and stays there even if system is IDLE.

My point is in windows 7 the Fan and CPu remain in LOW STATE for all the time except for stressful tasks.

And in Karmic The Fan and CPU remain in MEDIUM state for all the time except few seconds.

This means my CPU is burning with 49 C [MEDIUM STATE] even in IDLE conditions in KARMIC 9.10. Other tasks like surfing etc; fire up CPU much more.

But in Windows 7 the CPU mostly remains near 39 C [LOW] even while surfing,typing etc; tasks.

This alone reason is stopping me to use UBUNTU in fear of burning my hardware. 

: I reproduced the same results by conducting above experiment 5 times.

HOW TO HAVE BETTER POWER MANAGEMENT in UBUNTU??.{tried KUBUNTU suspecting GTK cpu usage but found same issues}

---

