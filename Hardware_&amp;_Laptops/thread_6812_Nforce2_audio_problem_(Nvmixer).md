---
title: "Nforce2 audio problem (Nvmixer)"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by lagartija on 2004-12-01
hi, 

i've recently installed Ubuntu and i'm currently try to tweaking my system...
i've a little problem with the proprietary sound driver (OSS, not ALSA) from Nvidia (Linux IA32 Drivers Version: 1.0-0292) on an ABIT AN7
drivers installs correctly but i'm not able to adjust the volume ONLY for the SPDIF output
seems that both Gnome volume control and Nvidia NVMixer affects only the analog outups of the soundcard (i've verified connecting a pair of stereo analog speaker)

finally, setting the speaker configuration to 5.1 via Nvmixer seems to work as stereo files are mirrored to rear channels
therefore this configuration is lost with each reboot

do you have some suggestion ?

---

### Post by bob k on 2004-12-02
[QUOTE=lagartija]hi,

i've recently installed Ubuntu and i'm currently try to tweaking my system...
i've a little problem with the proprietary sound driver (OSS, not ALSA) from Nvidia (Linux IA32 Drivers Version: 1.0-0292) on an ABIT AN7
drivers installs correctly but i'm not able to adjust the volume ONLY for the SPDIF output
seems that both Gnome volume control and Nvidia NVMixer affects only the analog outups of the soundcard (i've verified connecting a pair of stereo analog speaker)

finally, setting the speaker configuration to 5.1 via Nvmixer seems to work as stereo files are mirrored to rear channels
therefore this configuration is lost with each reboot

do you have some suggestion ?[/QUOTE]


I have had more than my share of nvidia. My last nvidia board became a frisby. They are at least a year behind Linux development, during that year everybody is bitching, and when they release the driver everybody has moved on to greener pastures.

I am currently using the VIA KM400 chip set and every thing works. this is so much nicer than nvidia.

My nvidia board cost @ $100us and the VIA board cost $52us and has a 400 FSB. So go figure.

One thing I have found out is that Nvidia doesn't belong on a Linux machine.

Bob

---

### Post by lagartija on 2004-12-03
[QUOTE=bob k]I have had more than my share of nvidia. My last nvidia board became a frisby. They are at least a year behind Linux development, during that year everybody is bitching, and when they release the driver everybody has moved on to greener pastures.

I am currently using the VIA KM400 chip set and every thing works. this is so much nicer than nvidia.

My nvidia board cost @ $100us and the VIA board cost $52us and has a 400 FSB. So go figure.

One thing I have found out is that Nvidia doesn't belong on a Linux machine.

Bob[/QUOTE]

OK, i will remember your suggestion at my next hw upgrade 
but for the moment I really don't need a frisby
unfortunately i have to use this nvidia board only as a computer board...to browse the web, getting mail, playing some games and looking some films through my TV-Out
i have to confess that the usage you suggest me has been evaluated after i tried Slackware, Red Hat 9 and Fedora 3 (it's my fault...i'm quite new to linux and i'm not used to build modules, compile the kernel, etc...)

but I've recently discovered Ubuntu that seems to work quite well with this chipset and with my radeon 9600 (that seems to be another hw not exactly linux friendly....)
the installation is quite simple for a linux newbie like me and getting ethernet, sound and 3D accelleration working requires only few configuration/download

so, for the moment i'm happy of my new Linux system and this is only a minor problem: 
actually i tune the volume with the remote control of my amplifier (maybe it is simpler than open the mixer...) 
setting the number of the speaker at every boot is quite noisy but not impossible (2 clicks...)

but i would have to have this problem fixed, i think that found what is the problem will help me to better understand how Linux works so maybe i will be able to solve further problems i will found (i've already to try to see a DVD, a divx,  i want to try DOOM3 and UT2004, i will try to use my digital camera and the webcam, and finally install wine: i'm sure that these will be long tasks)

so, if someone have a similar hardware configuration working, or a better knowledge of linux than me, and can give me a suggestion it will be very appreciated

thanks in advance

bye, 
and sorry for my english...

---

