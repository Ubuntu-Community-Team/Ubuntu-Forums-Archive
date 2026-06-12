---
title: "PLEASE!!!! Sis driver help, no video!"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by maxsideburn on 2005-07-11
Well I looked at this post

[http://www.ubuntuforums.org/showthread.php?t=25014&highlight=averatec+6200](http://www.ubuntuforums.org/showthread.php?t=25014&highlight=averatec+6200)

and this should have helped, nope, still having the blank screen or stuck cursor problem. What could I possibly be doing wrong? I've tried everything I can find, why can't Ubuntu just work with my SIS chipset? Or just use the generic VGA or VESA drivers??

Thanks.

---

### Post by varunus on 2005-07-11
Can you post your /etc/X11/xorg.conf file?  Also, your /var/log/Xorg.0.log file.

---

### Post by az on 2005-07-11
Did you try installing without the special parameters?  Are they in your grub menu.list (When you beet, hit escape and go into the grub menu, if it is not shown by default.  Chose the recovery mode optinop and hit "e" to edit it.  Remove those special parameters and hit enter and then "b" to boot.


Boot into recovery mode  and do 
dpkg-reconfigure xserver-xorg
and then 
init 2

---

### Post by maxsideburn on 2005-07-11
well if I try installing without vga=771 then I get just a black screen

and if I try installing without noapic nolapic the computer freezes, so I have to install with those options.

as for the stuff you mentioned it makes no sense to me why that would work, but I will try it and see what happens.

---

### Post by maxsideburn on 2005-07-11
well when I tried to reconfigure it said xserver-xorg wasn't installed. I did apt-get install xserver-xorg and then it installed, then I ran dpkg-reconfigure and configured it all. Then when I did init 2 it installed all kinds of stuff and booted into the GUI after a while. What exactly does the init 2 command do? And why couldn't I just use xorgconfig to configure my stuff properly?

---

### Post by az on 2005-07-12
First, boot back into recovery mode and do

sudo apt-get install ubuntu-desktop
sudo apt-get -f install



Then 

init 2

In recovery mode, you run a lean system.  Your installation had failed to install some packages.  Installing ubuntu-desktop should bring inany other package you do not have.  The -f install fixes unconfigured packages.

Init 2 brings you from recovery mode to full mode.

---

