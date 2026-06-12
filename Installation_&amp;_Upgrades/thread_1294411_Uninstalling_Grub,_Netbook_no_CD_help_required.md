---
title: "Uninstalling Grub, Netbook no CD help required"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by denvise on 2009-10-18
Well when you see this topic (again...) you probably will think: Why dont he google it? or something but I have googled the problem of uninstalling Grub in a hundred different ways and have found a 100 000 answers but none of them applies to my problem and that is why I post it now with as much information as possible so that someone here maybe can help me :)

So I got a Netbook, Samsung N120. (No CD/DVD reader/writer)
Since Ubuntu have been working great on my other computers (not netbooks) I decided to dual boot it with Grub.

The installation went fine with Unetbootin so there I had Windows XP and Ubuntu dual booted with Grub.

Then I decided that I no longer wanted to use both Ubuntu and XP on that computer since I use it for my education mostly which is all in windows, microsoft office and so on.

Also I wanted to have another version of Windows XP.

Now when I try to insert the XP iso on a USB (like i did with ubuntu) and then turns the computer on I get a message saying: 

"Remove and movable (external) devices.
Press any key for restart"

(This is with the USB as first boot priority)
(Without the USB as first priority it just loads Grub as usual with the choices and all)

Anything that is on the USB, Windows XP, Supergrubdisk, BootCD just makes it say:

(This is with the USB as first boot priority)
(Without the USB as first priority it just loads Grub as usual with the choices and all)

If I insert the USB with Ubuntu or eeebuntu (those I have tried) it boots from these as it should.
And with no USB it of course starts Grub as it should and loads my options.


Now I have tried to follow this: [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

But when I enter: sudo apt-get install ms-sys          
I get the error:  E: Could now find package ms-sys

I do not have a external CD/DVD reader but if it is absolutely required I will buy one but is there any way to do it without one I would be very glad, also would it really help with a external CD/DVD reader or will it say the same (Remove external device and restart) message?



P.S. 
I can enter Windows XP
I can enter Ubuntu
I can have internet in both OS's (Wired in Ubuntu because drivers are needed)
I have a 4gb USB that I installed Ubuntu with
I have root permission in the terminal atleast

I want to have only windows XP on the computer with the normal Windows boot, not the Grub or the Lilo (Though I have not tried to solve the problem using Lilo because I do not know how to)

Please help me, I have seen atleast some other people having an identical problem as myself.

///Denvise

---

### Post by hal10000 on 2009-10-18
I have no idea on how to get your windows mbr back without a windows cd if you did'nt backup your mbr.

Next time you install ubuntu do
```
sudo dd bs=512 count=1 if=/dev/sda of=/home/yourname/mbr_win_backup
```
before you install grub. This saves the existing mbr on /dev/sda  as a file called "mbr_win_backup" in your home directory.
You can then easily restore this backup with 
```
sudo dd if=/home/yourname/mbr_win_backup of=/dev/sda count=1 bs=512
```

---

### Post by denvise on 2009-10-18
Yes I will do that next time, however it does not solve my current problem :S

I am kinda confused of what to do :S

---

### Post by bulldog on 2009-10-18
If you used unetbootin before you can probably use it again with the systemrescuecd.
Look here to find out how:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by oldfred on 2009-10-18
If systemrescue disk does not have it Supergrub does has a way to restore a XP boot:
[http://www.supergrubdisk.org/w/index.php5?title=UninstallGRUB](http://www.supergrubdisk.org/w/index.php5?title=UninstallGRUB)

It looks like supergrub now has two versions one is old grub legacy and the other is the new grub2. LiveCD, floppy, and USB versions available.

---

### Post by presence1960 on 2009-10-18
> **oldfred said:**
> If systemrescue disk does not have it Supergrub does has a way to restore a XP boot:
[http://www.supergrubdisk.org/w/index.php5?title=UninstallGRUB](http://www.supergrubdisk.org/w/index.php5?title=UninstallGRUB)

It looks like supergrub now has two versions one is old grub legacy and the other is the new grub2. LiveCD, floppy, and USB versions available.

to rebuild your MBR for windows boot from the Ubuntu Live USB. You will want to use testdisk. You may have to install it. Open a terminal and run ```
sudo apt-get install testdisk
```

When install is finished run in terminal ```
sudo testdisk
```
If you get a message that testdisk need 25 lines to work, just enlarge the terminal or maximize it. Now do this:

1. Choose "no log"
2. select your disk with windows installed on it, then select proceed at bottom
3. choose Intel partition table type
4. choose advanced
5. select partition with windows on it & select boot at bottom
6. select rebuild BS

when complete exit and reboot. See if windows boots and GRUB is gone.

---

