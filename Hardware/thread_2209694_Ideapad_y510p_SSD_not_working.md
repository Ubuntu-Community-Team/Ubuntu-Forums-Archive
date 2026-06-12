---
title: "Ideapad y510p SSD not working"
date: 2014-03-06
forum: Hardware
---

### Post by edgar_black on 2014-03-06
[COLOR=#333333][FONT=Arial]I have an IdeaPad Y510P. It comes with an 24GB SSD, and one 1TB hard disk. I had to install ubunuu  twice in this computer.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial] [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]During my first installation I put /boot and /home in the 24GB SSD and use the 1TB disk for everything else. Everything was working smoothly until I begin to notice that the latest Nvidia driver (the one that was released few days ago) was not working properly. Even the cuda compiler (nvcc) was not producing correct results. Then I decided to install linux again (once you know how to do it, is really simple).[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial] [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Here comes my problem. During the second installation, I lost control of the 24GB SDD. I can see that the disk is there, but I can not access it. The linux installation program fails when it tries to access it. I had no other choice than to install linux on the 1TB hard disk. Now Linux is running, but I can not use the 24GB SDD.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]So far I have tried to use "Disk" and "GParted" for format and/or partition it without any luck.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial] [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial] Since I was not able to solve the problem, I called Lenovo and they sent me a new computer. [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial] [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Installation was very simple. Again I was playing with different options for the installation. This time I decided to create two partitions in the 24GB SSD; one of 512 MB for /boot and the second for / (root). I also create two partitions with the 1TB disk one for /home and one for /opt.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial] [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]The computer is very fast loading the OS with this configuration. However, playing with the video drivers I lost the video and decided to reinstall. The installation was so easy the first time that reinstalling was not painful.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial] [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Here comes the problem: I can not longer access the 24GB SDD again. It is exactly the same problem that I have with the first computer. I can see the SDD disk, and I can ask for the disk to be erased during the installation, but the installation frozen. I even load GParted from a bootable USB and try to erase the partitions on the SSD drive without luck. The disk is like frozen. It do not respond to anything.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial] [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Have anyone experience something like this?
Is there any trick to format/partition an SDD drive?
Have anyone experience something similar?

I can not believe that the two SDD disks are wrong is such a short period of time.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial] [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Now that I have installed Linux only on the 1TB disk, I can notice how much slower is the OS loading from it.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial] [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Any help will be appreciated.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial] [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Thanks[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial] [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]

[/FONT][/COLOR]

---

