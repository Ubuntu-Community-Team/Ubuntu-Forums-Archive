---
title: "ati proprietary 9.2"
date: 2009-02-22
forum: Hardware
---

### Post by milanlin on 2009-02-22
Hello,

I am getting some new lessons from ati :))

My relevant desktop configuration: 
OS mint 6
mobo with integrated nvidia and pci ati 4850

When ati card is used = desktop is booting to the white screen = dead end.
I have istalled ati proprietary driver 9.2 through nvidia graphics. I have followed ati instruction: uninstall nvidia, install ati driver. After restart I went through ati card and booted again to the white screen. OK, I have changed to the nvidia card but this is now booting to the black screen.
Nothink works in recovery mode and I can not get back to the system = dead end?

I know I need to unistall ati proprietary driver to recover the system. Or maybe change etc/x11/xorg.conf where the problem probably is. But how to access it???
When I will use live cd I do not have root privileges to change etc/x11/xorg.conf or delete usr/share/ati.

I tried to use system recovery cd but I am not able to use it yet.

So before I reinstall the system (not very happy, because it is not backupped) and before I try to install ati driver from repository, is there a way how to safe the system???

If I knew this I would have never buy ATI, I am pretty dissapointed and considering to return it and buy nvidia card.

Any suggestions or link to the solution are very welcomed.
Thank for support.

---

### Post by milanlin on 2009-02-23
Hello forum,

my day 2:
Through nvidia graphics using live cd I have deleted all ati driver instances which were listed. So I have booted back to my system. Now I'll do backup and I will try to istall non-proprietary ati driver.
But here are my questions: Is the ati 4850 unsupported by the latest ati driver? They say that driver for ubuntu is supported...or it has some big bugs?
Should I keep the card or return it and swap it for nvidia? What do you prefer for linux - nvidia or ati?

The ati card is not able to boot even live cds! Just the white screen! So where is the support and compatibility, I am really wondering.

---

### Post by bertolo on 2009-02-23
i don't want to be rude. but mint != ubuntu, they are similar, but are not the same distro.

---

### Post by milanlin on 2009-02-23
Partially resolved: First I have used synaptic to install xserver-xorg-video-radeonhd through nvidia card. Then I switched to ati and it worked. Finally hardware drivers in administration found flgrx.
This is my first ati and the fonts or font rendering is unnatural in linux and in windows as well. 

Many thanks my google friend..

---

