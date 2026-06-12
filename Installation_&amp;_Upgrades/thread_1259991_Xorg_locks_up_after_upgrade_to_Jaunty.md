---
title: "Xorg locks up after upgrade to Jaunty"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by nycgadgetgeek on 2009-09-07
Hello-

I am a bit exasperated as to how to solve the troubles that I have experienced since upgrading from 8.10 to Jaunty.  Basically my screen locks up after the Ubuntu splash screen comes up.  I have researched this issue and tried a number of the documented solutions to no avail.  

The motherboard is a Fatal1ty F-I90HD which includes an ATI Radeon Xpress 1250 video chip. I have also tried an nvidia GeForce 6800 video card. Regardless the end result is always the same the screen goes blank/black after the splash screen.  At this point, the keyboard and mouse seem to be locked and I am unable to move to another window using CTRL-ALT-F1. Actually, none of the keyboard commands work as all.  However, the kernel has not crashed given that the Ubuntu machine will still serve files to other machines in my network.  

Interestingly, the LiveCD works and is able to boot to an actual screen.  

Here is what I have tried:
[LIST]
[*]Tried to reboot X with SysResq commands. 
[*]Tried to login to terminal after CTRL-ALT-F1
[*]Changed boot paramaters to cover each combination of the following: splash, noapic, nolapic
[*]Tried to install NVIDIA drivers(need to be in Telenit 3 which crashes)
[*]Tried driver install using EnvyNG
[*]Modified xorg.conf to use VESA driver
[*]Replaced xorg.conf on my machine with that from LiveCD.
[/LIST]

No matter what option that I have tried it always ends up with X not coming up. Does anyone have any ideas on how I can resolve this?

Thanks-
Rodney

---

### Post by hal10000 on 2009-09-07
Are you able to boot in recovery mode?

---

### Post by nycgadgetgeek on 2009-09-07
Thanks for asking Hal. 

Yes.  I am able to boot to recovery mode.  

I forgot to mention that from recovery mode I have tried the following:
[LIST]
[*]Executed sudo dpkg-reconfigure xserver-xorg with and without the kernel framebuffer device interface option.  
[*]Tried to run xfix from recovery menu
[/LIST]

These options haven't worked either.  

Any ideas are welcome.  

Thanks-
Rodney

---

### Post by nycgadgetgeek on 2009-09-14
I was finally able to resolve the blank screen issue with the following steps.  

[LIST=1]
[*]Boot into recovery mode
[*]From recovery mode menu choose netroot to get networked enabled command line.
[*]Enter the following commands at the prompt.
# sudo apt-get remove xorg-driver-fglrx
# sudo dpkg-reconfigure -phigh xserver-xorg
[*]Exit
# exit
[*]Resume normal boot from the menu
[/LIST]

I found the instructions on how to resolve this issue at the following site:  [http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html]("http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html")

I hope this helps.

---

