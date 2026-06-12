---
title: "Dell D800 ACPI"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by Soko on 2005-05-17
I had Hoary running OK on my D800 with WiFi and correct screen res, but ACPI would not work properly for love nor money. Has anyone had success configuring ACPI sleep/suspend on this laptop?

Specs:

1.7Ghz Banais, 1.2Gb RAM
NV4200Go graphics
IPW2100 WiFi
BIOS version A12

Soko

---

### Post by anders.ostling on 2005-05-17
Soko, I have already spent countless hours on trying to tame ACPI on my D800. Have tried both Fedora and now Ubuntu, and I am pretty sure that you can forget about it for the moment. Maybe you can get suspend (to ram) to work, but resume is a completely different story...

However, if you find any solution or hints, I'm all ears.  I will save your mail adress and let you know if I stumble on a solution.

Anders

PS. I have put myself in an extra complex solution since I have my all my partitions in LVM's, and resuming from a swap in lvm is not pretty ... ;-).

---

### Post by Soko on 2005-05-17
That's what I was afraid of.

I place the blame squarely on Dell, and won't purchase another laptop from them. That being said, I still love this beast and would like to get it to play nice with linux. Oh well, might as well load up VMWare again.

Soko

---

### Post by anders.ostling on 2005-05-18
Same here, its a nice machine. However, the boot is quite fast (< 1 min), so I guess I can live without the ACPI stuff anyway, specially considering the alternative ...

Anders

---

### Post by Soko on 2005-05-22
Odd how some things work out. Work made me choose to either keep the D800, or swicth to a Fujitsu P7010d. I took the Fuji, since I know I can get everything working with ubuntu. The D800 is going to a user who'll need Windows only.

Soko

---

### Post by nick1 on 2006-06-20
I write to you all on this thread as a frustrated, buggy-eyed D800 user who's trying to install Ubuntu 6.06 as a virtual machine in VMware workstation 5.5.1 with Windows XP as the host operating system.  PLEASE take a few moments to read over my previous thread regarding this topic:

[http://www.ubuntuforums.org/showthread.php?t=198879](http://www.ubuntuforums.org/showthread.php?t=198879)

I want so badly to get Ubuntu 6.06 server installed but I've hit a brick wall at this point and need some guidance.

Thank you for your time,

Nick

---

### Post by tubo on 2006-06-21
I have a Dell D810 and have all common ACPI services running stable, including Suspend-To-RAM, Wireless, ect. Using the normal gnome-power-managers suspend function. I even use XGL/Compiz, and that works fine after resume on a ATI x300 card

There were two things for me to tackle for a D810:
 - SATA resume
 - ATI resume
 - acpi-support config
i use:
 - custom built 2.6.16ck3 kernel (only needed because of the SATA fixes) 
 - ATI latest proprietary driver
 - a REALLY simple acpi-support config, pasted below:

> 
ACPI_SLEEP=true
ACPI_SLEEP_MODE=mem


NOTHING else is commented in, and that seems to work.

best
Emanuel

---

### Post by nick1 on 2006-06-21
Thank you for your reply.  In the situation I'm in, how do you recommend I proceed?  I'm a newbie to linux so some of this is over my head.

Thank you for your time,

Nick

---

### Post by nick1 on 2006-06-22
*HUGE SIGH OF RELIEF*

Well I think I got it working in my case. I needed to install the 686 kernel for things to work. Below are instructions on how to install Ubuntu server 6.06 as a guest virtual machine in Windows VMware workstation 5.5.1 using the Ubuntu 686 kernel. These instructions may also apply if you're not using VMware.

How to Install the Ubuntu 686 Kernel
====================================

1.) boot to the Ubuntu 6.06 server install cd. Choose 'Rescue a broken system.'

2.) when you get to the Rescue Operations screen choose "execute a shell in /dev/discs/disco/part1", this option may read a little differently on your system.

3.) Click continue if another screen appears.

4.) At the prompt, type: sudo apt-get install linux-686

5.) You will be asked if you want to continue, type: y

6.) The installation of the 686 kernel will begin. It looks like an internet connection is required so the install files can be downloaded from the ubuntu website.

7.) When the installation is done, type: exit

8.) You should be returned to the Rescue Operations screen. Choose the last option: reboot the system. Make sure you're not booting to the install cd!

9.) Give the system a few moments to boot-up. At last, you should be placed at the login: prompt.

10.) Celebrate!

Helpful websites:

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
This is a very nice piece of documentation that explains all of the different Ubuntu kernel versions.

[http://www.tuxme.com/node/544](http://www.tuxme.com/node/544)
This is the website that gave me the idea to try the 686 kernel. This specific document also talks about installing Ubuntu on laptops.

I really wish ubuntu would detect which kernel is best for a system. It's things like this that I think keep people away from linux. Linux definitely requires a lot of patience sometimes but I think it's worth it in the end.

To all of you who replied with suggestions, THANK YOU SOOOOOOOO MUCH! You're truly a demonstration of the Ubuntu spirit.

Now to finish setting up my LAMP server!

Nick

---

