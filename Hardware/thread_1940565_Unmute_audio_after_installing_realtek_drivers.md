---
title: "Unmute audio after installing realtek drivers"
date: 2012-03-13
forum: Hardware
---

### Post by deepak115 on 2012-03-13
Dear pros!!!!

I have recently installed the realtek drivers for my lubuntu 11.10. Now there isnt any audio.As the audio was choppy before, I had to install those drivers. Below is what the readme file says
------------------------ 
**Manual install**:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure --with-cards=hda-intel
	c. make
	d. make install

Step 3. reboot your machine

Step 4. Use the alsamixer the disable mute (All audio line default is mute)
        Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.6 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.x and alsa-utils-1.0.x form the [www.alsa-project.org](www.alsa-project.org), then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package. 
-------------------------------------------------
Although Ive done the automatic install with ./install, I couldnot get the alsamixer working. This is the alsa output
[http://www.alsa-project.org/db/?f=a13aece0236b63b5fd7b2a8b80a788dbe640e0c5](http://www.alsa-project.org/db/?f=a13aece0236b63b5fd7b2a8b80a788dbe640e0c5)
So, here my soundcard isnt recognised by ALSA. 
Can someone pls help me out?? 
thanks

regards,
Deepak

---

