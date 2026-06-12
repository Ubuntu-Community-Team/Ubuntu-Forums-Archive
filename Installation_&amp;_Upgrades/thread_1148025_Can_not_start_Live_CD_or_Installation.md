---
title: "Can not start Live CD or Installation"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by sinmpae on 2009-05-03
[FONT=Arial][SIZE=3]When I boot ubuntu 8.10 or 9.04 from CD & select English on first screen & try to install or run Live CD from menu, my PC hangs at the booting screen. It just shows logo of ubuntu (see attachment) & status bar then suddenly hangs, keyboard & mouse freezes I have to restart PC by pressing reset button. The same problem occurs in Safe Graphics Mode.:([/SIZE][/FONT]
[SIZE=3][FONT=Arial]I checked CD for errors & also perform memory test -> No errors found.[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Although previous versions like 8.04 & 7.10 work very well.[/FONT][/SIZE]
[SIZE=3][FONT=Arial]I also requsted free CD of 8.10 from ubuntu, but hopeless, same problem occures.[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Same CDs work very well on my laptop & on my friend's PC.[/FONT][/SIZE]
[SIZE=3][FONT=Arial]So, what can be the problem?:confused:[/FONT][/SIZE]

[FONT=Arial][SIZE=3]Hardware Configurations :-[/SIZE][/FONT]
[SIZE=3][FONT=Arial]Pentium 4 - 2.40 GHz Processor[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Mercury 845GL-AGP Motherboard[/FONT][/SIZE]
[SIZE=3][FONT=Arial]1GB of RAM (512+512 in two slots) (DDR1)[/FONT][/SIZE]
[SIZE=3][FONT=Arial]IDE0 Master -> 80GB Samsung HDD (PATA)[/FONT][/SIZE]
[SIZE=3][FONT=Arial]IDE0 Slave -> 160GB Western Digital HDD (PATA)[/FONT][/SIZE]
[SIZE=3][FONT=Arial]IDE1 Master -> LG DVD-RAM driver[/FONT][/SIZE]
[SIZE=3][FONT=Arial]nVidia GeForce FX5500 256MB AGP Graphics Card[/FONT][/SIZE]
[SIZE=3][FONT=Arial]AMIBIOS Version 1.21.12[/FONT][/SIZE]

[FONT=Arial][SIZE=3]HDD Structure :-[/SIZE][/FONT]
[SIZE=3][FONT=Arial]HDD0[/FONT][/SIZE]
[SIZE=3][FONT=Arial]1GB Primary FAT32 -> MS-DOS 7.10 Installed[/FONT][/SIZE]
[SIZE=3][FONT=Arial]50GB Logical1 NTFS -> Vista Installed[/FONT][/SIZE]
[SIZE=3][FONT=Arial]13GB Logical2 NTFS -> XP Insalled[/FONT][/SIZE]
[SIZE=3][FONT=Arial]12GB Logical3 ext3fs -> fedora 9 Installed[/FONT][/SIZE]
[SIZE=3][FONT=Arial]2GB Logical4 LinuxSWAP[/FONT][/SIZE]
[SIZE=3][FONT=Arial]HDD1[/FONT][/SIZE]
[SIZE=3][FONT=Arial]2GB Primary FAT32 -> DATA[/FONT][/SIZE]
[SIZE=3][FONT=Arial]50GB Logical1 NTFS -> DATA[/FONT][/SIZE]
[SIZE=3][FONT=Arial]100GB Logical2 FAT32 -> DATA[/FONT][/SIZE]

---

### Post by bigboy_pdb on 2009-05-04
Unfortunately, I can't help you with this, but if you don't get a response, you should consider filing a bug report on launchpad.net. Granted that you were able to use previous versions of Ubuntu, it might be a regression problem.

I searched your chipset (845GL) in launchpad and on google and it appears that there have been problems with that chipset in the past, but I couldn't find any recent reports. You might have better luck searching.

---

### Post by rebski on 2009-05-04
Hi sinmpae, nicely detailed post.

You might like to check out another recent thread on 9.04 install/liveCD problems here
[http://ubuntuforums.org/showthread.php?t=1134107](http://ubuntuforums.org/showthread.php?t=1134107)

Have you filed a bug report yet. It is not something I have ever done but if no one else is going to do it then I might give it a shot.

I see that the thread dedicated to the Install & Upgrade experience poll has been taken down so this forum is not the place for help with this.

IMHO it is a Linux bug issue.

---

### Post by emp on 2009-06-16
OK.. bumping this, as I have the same issue.
(Ubuntu 9.04 , 64 bit)

I get to the same screen, and help (F1) section as well as alternative methods (F6), as well as all other function keys work.

"Running from CD" or "Install Ubuntu" do not seem to do anything, though, the system accesses the CD (sometimes) and nothing happens.

Here are my system specs:

Intel Core Duo E8400
8 GB of RAM
Asus p5Q Pro Motherboard
Ati Radeon 4800

::emp::

---

### Post by rbueno on 2009-06-16
I don't think it is a bug. kindly burn your cd by its lowest mode. I have encountered this problem before but i've found solutions over the internet. Why not try using USB instead of CD? it works fine and smoothly..

---

### Post by raymondh on 2009-06-16
Would you like to try the alternate (text based) install? 

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Good luck.

---

