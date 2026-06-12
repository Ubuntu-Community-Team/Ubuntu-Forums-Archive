---
title: "Ubuntu 15.05 blackscreen after changing Nvidia drivers"
date: 2016-11-07
forum: Hardware
---

### Post by tekkitbyte on 2016-11-07
Hello everyone 

Ill say it here im new to ubuntu 

lets start installed ubuntu 15.05  for the first time and everything goes well after the install i reboot and start installing updates and then reboot again after rebooting i go to change the Nvidia drivers form the default nouveau drive to Nvidia 304 for my geforce 6150 le and after that i reboot again after the reboot i log into ubuntu and it shows nothing but a black screen amd my mouse pointer and its stuck like this so i did Ctrl+Alt+F1 to get into a TTY and did sudo apt-get update and sudo apt-get upgrade then rebooted and still the same black screen :mad::sad: so back to TTY i typed sudo apt-get remove nvidia-304 and rebooted and got to log in but im stuck on the nouveau drive ive tried to set it back to the 304 drive but it does the same thing just a black screen after logging in is there any way to fix this because i cant find anything when looking it up 



PC Specs 

Dell Dimension E521
AMD Athlon X2 X64 4000+ @2.10Ghz
4GB of DDR2 C51 GeForce 6150 LE
250GB HDD


tried ubuntu 14.04 and linux mint 17 17.2 17.3 and does the same thing any ideas on what this is

---

### Post by bearlake on 2016-11-07
Hi,

The first thing to do is get rid of 15.xx version as it has reached [End Of Life]("https://www.ubuntu.com/info/release-end-of-life").

Try 16.04LTS and goto additional drivers and select your graphic card there.

---

### Post by ajgreeny on 2016-11-07
I presume you are using either 15.04 or 15.10 as there never was a 15.05 version of Ubuntu, but whichever it is you should move to a supported version, either 14.04, 16.04, or maybe 16.10, though personally I recommend the LTS (long term support) versions, which would be 16.04 at present.

You will not be getting any upgrades or updates of packages using either 15.## versions as they are now unsupported so will be a very real security risk for you.

---

### Post by tekkitbyte on 2016-11-07
Hey thanks for the reply i just got done with installing ubuntu 16.04 install went fine but after updating rebooting and changing the driver i get a login loop and the only way is to go back to nouveau via TTY after i got rid of the 304 driver i didnt even get a chance to reboot the system crashed and i was greeted with the grub menu after reboot from the crash after hitting enter to boot to ubuntu i am greeted to a few popups from ubuntu asking for me to report the problem so i clicked yes then a second popup heres photos of the log 


[http://imgur.com/a/AuDlN](http://imgur.com/a/AuDlN)

---

### Post by mörgæs on 2016-11-08
The 6100 and 6150 cards often appear in Ubuntuforum. They need some special treatment.

I suggest that you use a light desktop environment like X/Lubuntu and accept closed-source drivers during installation (not after a reboot).

---

### Post by tekkitbyte on 2016-11-08
> **mörgæs said:**
> The 6100 and 6150 cards often appear in Ubuntuforum. They need some special treatment.

I suggest that you use a light desktop environment like X/Lubuntu and accept closed-source drivers during installation (not after a reboot).


Thanks for the reply going to try Xubuntu first then lubuntu

---

