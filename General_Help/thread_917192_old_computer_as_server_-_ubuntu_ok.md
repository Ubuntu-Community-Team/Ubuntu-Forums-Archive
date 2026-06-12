---
title: "old computer as server - ubuntu ok?"
date: 2008-09-11
forum: General Help
---

### Post by abazoskib on 2008-09-11
My friends at school and I want to start a filesharing server of our own since a lot of different programs were blocked. I want to setup an ftp server in my room, however we want to make this as cheap as possible. A couple questions:

1. I have an old 486 machine running Windows 3.1. Can I install Ubuntu 8 on it successfully? 

2. Will I be able to find a harddrive that will work with it? I don't have the computer here, I'd have to go home to check it out. But I'm pretty sure it's a Packard Bell computer. I am looking for at least a TB of storage.

3. Should I look into buying another machine?

---

### Post by Sam Lars on 2008-09-11
1. Yes... though I highly doubt you want to be trying the normal install, I'd go with the alternative CD or the server CD to get a text install.

2. Um, yeah, I doubt you're going to get a TB on that old thing.  The BIOS probably doesn't support it.  You would have to check on what types of drives it has.  IDE would be a good sign.
Also, if it has USB, you could use USB hard drives to add some space, a couple 500 GB drives would get you there nicely.  It just wouldn't be very fast.

3. All in all, yes.  You may be able to get the old thing to fit your needs.  But you would probably be better off with a newer machine.  Faster, and more support for your storage needs.
I've got an old Pentium III 500 Mhz, 256 MB RAM, with 140 GB of drives inside and a 500 GB USB drive for storage.  It works nicely for a file server, and I also have it doing apt-caching, NTP server, and it was also an FTP server before we got a new ISP that doesn't expose our connection to the internet for that kind of thing.

---

### Post by abazoskib on 2008-09-11
ok i see your reasoning. is there any way to put this thing to use? its been in my basement for a very long time and i hate holding on to things i dont use. i dont think it has usb though, only serial.

---

### Post by Iowan on 2008-09-11
I have Ubuntu (servers) running on some pretty minimal hardware (P200s), but a '486 might be a li'l tight.  I DID have a Samba server on a '486 using a modified version of [Freesco]("http://www.freesco.org/"). It uses an older (smaller) 2.0 kernel.
There's also [FreeNAS]("http://www.freenas.org/index.php?option=com_frontpage&Itemid=22") - dunno what hardware requirements are, though. (Claims to run in 32M of RAM).

---

### Post by Vivaldi Gloria on 2008-09-11
There is a bug in hardy installer which makes it impossible to install it systems with less then 128 MB ram. See CLI in my sig. See also

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)
[http://www.linuxlinks.com/Distributions/Floppy/](http://www.linuxlinks.com/Distributions/Floppy/)

---

### Post by marshag63 on 2008-09-11
Hey, its good enough for IRC, email and working on your school reports (I recommend Abiword)  :)

I recommend using the Alternate CD and Fluxbox or Openbox for your desktop manager and go easy on the eyecandy.  If minimal Ubuntu does not work, I recommend Damnsmalllinux - there are a lot of programs available for it.

Good Luck!  

MG

---

### Post by Rhyader on 2008-09-11
Well, I'm not a geek of Ubuntu or linux in particular, but I do maintain a
fleet of old computers, ranging from the orginal PC [would you like to buy it
as a museam piece?] to a Pacard Bell 486, a pentium, and the dinosaurs I call
 my regular computers. So I can perhaps advise you. 

First, I doubt if a 486 will be able to handle any system/drive that can store
a Terabyte. In theory it can ... but you better be a much bigger geek than me
if you want to pull that off. Second, my friend the xubuntu user said that I
should have no problem running Ubuntu on my Pentium 100. I didn't ask about
the 486. My PB 486 runs Windows 95 and does it quite well with 20 MB of ram.
But Ubuntu is not something I considered. 

I have tried to install it on the Pentium 100 and failed. This is mainly because
it cannot boot from the CD. If your 486 can't either, you will have to have an
install CD that does not need to be booted. I have an Ubuntu 7.1 CD that should
work - but it didn't on my Pentium - so I can't give an encouraging report.
But in general try an OLD linux version that comes on a CD with linload ...
You should be able to boot DOS 7 (windows 95 command line) from a floppy,
access the CD, and run linload, a DOS program that loads linux. I have a CD
that does this, but it's SuSe linux version 7. Whatever it is, Ubuntu or other,
on your Packard Bell, exit windows 3.1 and look for .exe files on the linux CD.

As for hard drives, you will be limited to standard IDE, I *think*. I've never
tried putting a hard drive larger than 80 Gigabytes in a machine that old.
So good luck!

---

### Post by bingoUV on 2008-09-11
Get IDE hard disks, they may not be available easily in a few years. It will likely be able to handle at least 4 IDE hard disks.

USB hard disks will be very slow as the PC has USB version 1. You will be lucky to get 100kbps from a USB hard disk on such a computer.

damnsmalllinux should work great, along with a UI. There is an ftp server available for it. 20MB RAM is plenty for it, less than 20MB should also be OK.

---

