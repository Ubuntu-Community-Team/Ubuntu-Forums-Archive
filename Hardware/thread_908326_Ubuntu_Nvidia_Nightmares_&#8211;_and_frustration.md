---
title: "Ubuntu Nvidia Nightmares &#8211; and frustration"
date: 2008-09-02
forum: Hardware
---

### Post by syborfical on 2008-09-02
I have a TNT2 in server Athlon 2gb ram etc it has run fine for 18 months. I am running Ubuntu 7.10 everything was fine until I did some updates. 

Some how ubuntu wants to keep its CRAP nvidia drivers or thinks I should run them. I don&#8217;t too. If I wanted crap like that I would run windows.

Firsltly I DO NOT WANT TO RUN THE NVIDIA DRIVERS THAT COME WITH Ubuntu they are CRAP!!!!! Nor do not want to install them, or use envy or get told just go to synaptics or apt-get to install drivers. I have tired all of these and EPIC FAIL &#8211; format reinstall windows is almost an option or Free BSD ... 

I want to run the ones off the NVIDIA SITE. I don&#8217;t give a crap about them not being open source.

The drivers I want to run are NVIDIA-Linux-x86-71.86.04-pkg1. 
Secondly everything was working until I did an upgrade -
I can run sudo dpkg-reconfigure -phigh xserver-xorg, it works but when I reboot my machine runs in failsafe mode.

I have though about throwing the machine across the room several times.  I have reinstalled the NVIDIA drivers off their site and it does the same thing. Over and over. 

In my Xorg.conf I have the following 

To get VNC working when the machine boots I have  

Section &#8220;module&#8221; 
Load "vnc"
EndSection

Section &#8220;Screen&#8221; 
Option "SecurityTypes" "VncAuth"
Option "UserPasswdVerifier" "VncAuth"
Option "PasswordFile" "/root/.vnc/passwd"
Identifier	"Default Screen"
Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
Monitor		"Generic Monitor"
DefaultDepth	24
SubSection "Display"
	Modes		"1024x768" "800x600" "640x480"
EndSubSection


This has all worked for 12 months or more. Now it still works but at a whopping 800x600 WOOT 

Has anyone got an ideas???? 
I plan to reinstall ubuntu 8.04 but im PISSED off at the moment.
 
Any idea how to remove / purge the Nvidia crap that comes with ubuntu so there are NO drivers on my system at all???

I know there was a way to do it with fedora 6, I had to purge and delete a heap of Nvida crap that came with the system. 
Then install the drivers off the website and it worked&#8230;. I just cant seem to find it on google. 

Any ideas anyone else had any similar issues?

PS sorry if this offended anyone sort of venting as well. 

Cheers thank you for reading

---

### Post by littletinman on 2008-09-02
honestly, seeing that i use Nvidia cards, I've tryed using the ones from the Nvidia site. And really the Envy ones worked far better. The default Ubuntu ones didn't work to great, i dunno why. But Envy gets them straight from the nvidia site (i believe) which i could never do manually. Envy has fixed all my problems. It really has. Have you given it a try? 

 Sorry if this isn't the info you wanted. But, in my all day use for the last 8 months, Envy has taken away those nightmares. thank God. 

I used to have BSOD Fever Nightmares when i  used windows. Oh am i glad i stumbled across Ubuntu.


 the little tin man

---

### Post by in-dust-rial on 2008-09-02
hi,
please clam down =) its just n tnt2, isn't it?

as i understand it you made a system upgrade from 7.10 to 8.04.
with my geforce, i had to discover, that the difference between 
legacy and new and normal nvidia drivers changed!

so ubuntu installed:nvidia-glx packages
, but i needed:
nvidia-glx-legacy

so first of all, there should be somewhere a hint.
i found the hint, that TNT needs "Version: 71.86.06" or older!

here is a howto and a list of driver versions and package name.
you said, you tried everything, did you try the legacy-package?

if you want more(better) help, you should provide more information, so the skilled and trained ones can read your , complete xorg.conf(and xorg log), your loaded 'nvidia' modules, dmesg, glxinfo (first lines)!

but what just maybe do the trick! if your kernel is below 2.6.24,
just try to run a 2.6.24-19!!
did the trick for me - just try it!

.hf and good luck

---

### Post by syborfical on 2008-09-19
Its actacully not the Graphic card is the fact i have no monitor connected.

what tard designed X ? 

if.ubuntu.has no monitor.run is **** **** low graphics mode= frustration

windows server 2003 runs with no monitor attached with a gui why cant ubuntu?

---

