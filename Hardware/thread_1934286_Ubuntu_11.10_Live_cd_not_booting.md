---
title: "Ubuntu 11.10 Live cd not booting"
date: 2012-03-01
forum: Hardware
---

### Post by alexilni76 on 2012-03-01
I have a Acer netbook aspire one with an Atom 1.6ghz processor, 2gbyte ram, intel gma 500(I think PowerVR gpu licensed) intergrated graphics.  I know that there are developers still working on the drivers for the gma 500 and may come out sometime this summer.  

The problem I have is that Ubuntu 11.10, Kubuntu 11.10, Mint 12, Fedora 16, and Knoppix all can't boot live on the Acer Netbook.  I use a TEAM Team Group Color Turn USB 3.0 key drive with 16Gigabyte storage either FAT or ext4 file system.  I use UNetbootin to create the bootable usb drive.    And I have used the same usb key to install windows 7 and Ubuntu 11.10 on my primary Desktop so there are no issues with the usb key.

Anyway, I put the usb key, turn on the netbook and UNetbootin screen comes up, I select 
Start Kubuntu, I than see Kubuntu 11.10 blue screen and dots moving under the title which means it's running, than takes me to the terminal ubuntu@ubuntu:~$.

I type startx and get this message:
Log file: "/var/log/Xorg.0.log", Time: Thru Mar bla bla bla
Using system config directory "/usr/share/X11/xorg.conf.d" vesa: Ignoring device with a bound kernel driver.  open /dev/fb0: No such file or directory
Screens found, but none have a usable configuration.

"fatal server error", "no screens found".
and below it says:
"ddxSigGiveUp: Closing log", "xinit:giving up", "xinit: unable  to connect to Xserver: connection refused", "xinit: server error"

I used sudo ifconfig eth0, than sudo dhclient eth0, connected to the internet and sudo apt-get --purge remove xserver-xorg-video-nouveau and reinstalled the xserver which did not work so I updated and upgraded to see if it will do anything.  the sudo lightdm start or sudo /etc/init.d/gdm start or sudo gdm start does not work since it cant find /etc/init.d or /etc/x11. 

Anybody know if this is a common issue with the acer netbook and is there a solution to this fix

---

### Post by mastablasta on 2012-03-02
have you tried booting with any of the options such as for example nomodeset or xforcevesa?
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
also title is a bit miselading - the USB did boot, the DE didn't start. suggesting there is a GPU (drivers?) issue.
 
also in kde to restart it:
[INDENT]sudo /etc/init.d/kdm restart
 
[/INDENT]i think for gnome is sudo gdm-restart or maybe in this case *start*
 
*edit*
*try:*
sudo service gdm start

---

### Post by alexilni76 on 2012-03-02
Sorry, I meant to say it does not boot into KDE environment.  It's the same with the gnome in Ubuntu 11.10.  I had ubuntu installed on it a long time ago and i think it was the 9.10 than 10.10 and never had a big issue like this.  Every time something changes in the kernel something else breaks.

  I will try nomodeset or xforcevesa which should work I forgot about these commands.  It's been a while since I have used the terminal to fix major issues.  Like i said the intel gma 500 drivers is really a powervr chipset that intel licensed from powervr so developers have a hard time coding a perfect run video driver.  

Actually, the sudo lightdm start or sudo /etc/init.d/gmd start or other variation does not work since it can't find the init.d even though it's in the /etc/ directory.  These netbooks are crap and should have never been released it does not matter what OS you install if it's XP, vista, 7, linux it just runs slow.  Although with linux it did run faster than windows 7.

Thank You

---

### Post by alexilni76 on 2012-03-02
Nevermind, nothing works.  The poulsbo video driver is installed by default which is causing the problem i just don't understand how Canonical would let something like this happen.  If they know there are gma500 issues why in the world would they allow poulsbo driver installed automatically and not let the vesa run like the old 9.10, 10.10.  I can't even remove the poulsbo video driver.  I actually installed emgd but needs a restart which everything gets lost.  I gave the usb 4gigabytes of extra storage for kubuntu 11.10 to use for saving updates and stuff.  

I even blacklisted the poulsbo drivers and nothing.  I also could not modify the grub.cfg with gksudo gedit because it could not open the gtk it gave a warning.  I could not set write rights using chmod because the file did not exist.  the kdm, lightdm, gdm don't work because you first have to install them and if you try sudo kdm start it loads than stops nothing happens, alt-ctrl-f2.  My head hurts and wasted 3 hours trying to find more solutions which is spread all over the internet.  

I will try tomorrow by editing the grub in the iso before i make the kubuntu 11.10 live usb drive.

---

### Post by mastablasta on 2012-03-02
you need to use command line editor such as for example vim to edit in terminal.

anyway how about looking this from different perspective:
> 
[Joli OS]("http://en.wikipedia.org/wiki/Joli_OS"), a Linux based OS optimized for netbooks, has a driver for the GMA500 built in.

It's Ubuntu based...

I also found info that support in 10.04 and 10.10 is actualyl experimental. so... i would give this Joli a try. maybe it is not so bad.

that is until the new drivers come arround which are already announced.

---

### Post by alexilni76 on 2012-03-02
It does not matter which editor I use in the terminal it just does not work.  During the usb or CD boot it does not take me to the primary kubuntu/ubuntu menu where it gives you the option to "try it live" or "install the kubuntu/ubuntu OS onto the hard drive", It just stops at the terminal.  If I was able to install it on the harddrive with the poulsbo video drivers than I would not have any issue on removing the poulsbo driver and running the vesa or trying out the emgd video driver, but like i said it's running off of the usb. 

I will try out the other OS you recommended.  I will also try out the opensuse.

---

### Post by mikewhatever on 2012-03-02
> **alexilni76 said:**
> I have a Acer netbook aspire one with an Atom 1.6ghz processor, 2gbyte ram, intel gma 500(I think PowerVR gpu licensed) intergrated graphics.  I know that there are developers still working on the drivers for the gma 500 and may come out sometime this summer.

Who are the devs, and what's the source of that info?

> 
The problem I have is that Ubuntu 11.10, Kubuntu 11.10, Mint 12, Fedora 16, and Knoppix all can't boot live on the Acer Netbook.  I use a TEAM Team Group Color Turn USB 3.0 key drive with 16Gigabyte storage either FAT or ext4 file system.  I use UNetbootin to create the bootable usb drive.    And I have used the same usb key to install windows 7 and Ubuntu 11.10 on my primary Desktop so there are no issues with the usb key.

Anyway, I put the usb key, turn on the netbook and UNetbootin screen comes up, I select 
Start Kubuntu, I than see Kubuntu 11.10 blue screen and dots moving under the title which means it's running, than takes me to the terminal ubuntu@ubuntu:~$.

I type startx and get this message:
Log file: "/var/log/Xorg.0.log", Time: Thru Mar bla bla bla
Using system config directory "/usr/share/X11/xorg.conf.d" vesa: Ignoring device with a bound kernel driver.  open /dev/fb0: No such file or directory
Screens found, but none have a usable configuration.

"fatal server error", "no screens found".
and below it says:
"ddxSigGiveUp: Closing log", "xinit:giving up", "xinit: unable  to connect to Xserver: connection refused", "xinit: server error"

I used sudo ifconfig eth0, than sudo dhclient eth0, connected to the internet and sudo apt-get --purge remove xserver-xorg-video-nouveau and reinstalled the xserver which did not work so I updated and upgraded to see if it will do anything.  the sudo lightdm start or sudo /etc/init.d/gdm start or sudo gdm start does not work since it cant find /etc/init.d or /etc/x11. 

Anybody know if this is a common issue with the acer netbook and is there a solution to this fix

AFYI, gma500 is unsupported, so please, don't expect to just stick in a flash drive and boot, let along see the desktop. This is Poulsbo we are talking about! From Natty onward, it's become so incompatible, that even the vesa driver wouldn't work. Reportedly, there is a stub poulsbo module in the kernel that does nothing, and there is also a conflict with plymouth, which needs to be disabled.

Scared yet? :~)

There used to be a custom iso with EMGD, but the download link is now dead. If you are set on 11.10, check out the following thread for tips [http://ubuntuforums.org/showthread.php?t=1792777](http://ubuntuforums.org/showthread.php?t=1792777).
If that's too hard, try 10.04 with the PSB driver.
Precise will, hopefully, have the first decent out of the box experience (doesn't work yet), but no hardware acceleration.

---

### Post by alexilni76 on 2012-03-02
I found the problem.  UNetbooting which i was using to create the live boot drive was not doing it correctly.  It even caused opensuse 12.1 not to boot.  So instead I switched to Universal usb installer and it made a correct and functioning opensuse live boot drive same with ubuntu 11.10 and kubuntu 11.10.  Even though Ubuntu still gives me the video driver problem, now I can actually fix this issue in ubuntu/kubuntu and make changes to the grub or whatever to make it work, before I could not do anything at all including starting and stopping the lightdm which i can do now properly.  I think the UNetbooting did not fully copy the whole iso properly to the usb or cd. 

Thanks everybody.

---

### Post by deepak115 on 2012-03-13
Try nomodeset option while boot. That would solve ur problem. 
After install u may also install the EMGD 1.8 drivers from the ppa to get the best resolution and effects of GMA 500.

deepak

---

