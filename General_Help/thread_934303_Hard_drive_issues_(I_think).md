---
title: "Hard drive issues (I think)"
date: 2008-09-30
forum: General Help
---

### Post by Fingbut on 2008-09-30
Ok I've tried this in absolute beginner talk but the more I tinker the more I think I might need help. If anyone could help or has seen something similar that would be great, thanks.  

If you need anymore details I would be happy to provide, all this tinkering makes me want to get out of windows. Getting the 32bit version is an option but I can't download it for a while (see below) and formatting or starting from stratch (while I'd love to) is not an option  .

I've been having some issues with getting Ubuntu running in the gui. I am trying to install as a dual operating system with windows XP, I have tried installing within windows and from the read only Ubuntu CD boot thing. However, in both cases it hasn't worked.

When booting from the cd and installing from that I have issues with the partitioning menu(step 4/7), it always comes up blank. I have tried loading with unpartitioned space and a couple of other things but it doesn't seem to work.

When installing from Windows everything seems to run fine until I reset and when trying to open Ubuntu (I assume) it loads up a dos like linux tool that I am unable to use.

I have checked the quality of my burnt cd and have copied it at low speed with as few errors as possible. I have tried a few other things but didn't want to write a huge post (too late!)


I have found lots of similar issues in forums so if anyone has a link with good instructions that'd be awesome but I've looked for a while with no luck.

Any help is much appreciated.



Update:

I have defragged my primary HD and tried reinstalling. I also updated my Bios and am certain that the linux Kernel works with my system. I have tried Gparted (thx lowsky and shoot2kill) and it cannot detect any devices, I have found similar issues on the forum but they seem to relate to certain PC's (mostly Dell) and I built this one.

I have also performed full checks on both my hardrives and attempted booting Ubuntu from my other HD (not the windows boot.)

Details:

Ubuntu Version 8.04 Desktop 64bit

PC Spec

AMD 3500 64bit
1GB Kingston RAM
(ASUS mobo and graphics)

But I forgot HD details so I'll tack them on here

HD 1 Seagate 160GB (windows is on here and so is Ubuntu in a different 30gb partition I made)
HD 2 Samsung 750GB

And here's the motherboard I'm googling it now to try and find out

Motherboard ASUS AV8 XE Socket 939 (the linux kernel runs on it)
I have updated the bios.


When it restarts after windows it goes into Busybox V1.1.3, I've tried to find commands to help but I don't really understand this tool.

---

### Post by maruthi_s@infosys.com on 2008-09-30
[COLOR="Blue"]
Hi 

I guess you installed Ubuntu properly. Insert the Ubuntu burnt CD in your machine and reboot the machine. 

Choose Ubuntu when it asks for OS selection. 

Press Esc, choose the first option of boot from CD. 

now the process will begin and your ubuntu will get installed properly and you can start ubuntuing .... 

Let me know if that works.

[/COLOR]

---

### Post by Ryadt on 2008-09-30
Try to use the kernel boot options "all_generic_ide" .
Follow this guide as to how to input the parameter: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
substitute the "quiet splash --" and add "all_generic_ide" (without the quotes)

---

