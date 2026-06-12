---
title: "Asus G50V Problems"
date: 2009-06-01
forum: Hardware
---

### Post by thisnamestoolong on 2009-06-01
Alright, I am admittedly a newb to Ubuntu, but have been making an effort to get things up and running on my own. I have installed Ubuntu on 3 of my own systems so far, as well as one of my friends' systems. Everything has gone very smoothly and I have had no issues that I could not resolve on any machine other than my Asus G50V laptop, so I figured that I would lay out some of the issues I have had so far in the hopes that others had some advice. This machine is running the 64 bit version of Jaunty.

1 -- Hard disk issues during install -- I had numerous issues getting Ubuntu to install, with the install failing at various points (bonus points for the time it failed while installing the grub bootloader, temporarily bricking my machine and blocking me out of my Windows install)

2 -- Sound Problems -- the speaker output works fine, and when I plug in headphones, it mutes the sound to the speakers, but I get no sound in the headphones. Weird.

3 -- Optical Drive -- My DVD burner has developed some serious PMS since I installed Ubuntu. It will fail approximately 80-95% of the time during any sort of data transfer (especially write, but read as well). As soon as the data transfer fails, the contents of the drive will become unreadable, and the drive will spin continuously at full speed. After this, I cannot eject the drive (although I can still unmount the volume) and the only way to stop the disk spinning or eject it is with a full restart, which is aggravating to say the least. This seems like a hardware issue but the drive worked fine under Vista and XP. Has anyone else had anything bizarre like this happen?

Everything else seems to be working great, 3D graphics, wireless Internet, and the like. Even with this little snags, I am loving the freedom I get with an open source O/S, and I am amazed by how much better the O/S is, although these few issues are kind of a big deal for me.

---

### Post by Crunchy the Headcrab on 2009-06-12
1- This is an easy fix.  *see 3

2->  
   While sound works, the headphone jack does not work properly. No sound comes out of the headphones. Adding this line to the bottom of /etc/modprobe.d/alsa-base (it may be called alsa-base.conf on newer distros) may fix this problem:

 options snd-hda-intel model=m51va   
Other options known to work are:

 options snd-hda-intel model=asus-mode3 options snd-hda-intel model=g71v
options snd-hda-intel probe_mask=1   
After editing the file, try the following commands as root in order until one works (or just reboot):
/etc/init.d/alsasound restart
alsa force-reload
update-modules 
  

See this: [http://www.linlap.com/wiki/asus+g50v](http://www.linlap.com/wiki/asus+g50v)

3- I had the same problem.  Not only did it cause read/write problems within ubuntu, it caused installation problems on ubuntu and several other distros.  Follow this:
> In the default configuration you will have a nasty surprise of all kinds of errors sooner or later during the installation process. This is all because of the *Enhanced* SATA setting in the BIOS. Before wasting good CDs trying to burn again the installation kit, try rebooting the laptop and pressing F2 during the flames to open BIOS settings, then from *Advanced* tab switch to *Compatible* mode instead of *Enhanced*See this page: [http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/]("http://www.linlap.com/wiki/asus+g50v")
[]("http://www.linlap.com/wiki/asus+g50v")

---

