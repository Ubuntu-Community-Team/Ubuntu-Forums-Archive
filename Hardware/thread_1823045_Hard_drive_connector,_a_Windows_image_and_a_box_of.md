---
title: "Hard drive connector, a Windows image and a box of puppies."
date: 2011-08-11
forum: Hardware
---

### Post by 1clue on 2011-08-11
Hi,

Trying a first install on a laptop.  I've been using Linux forever, but to date I have never had a Windows image to preserve or the funkiness of laptop hardware to deal with.  I'm lost on that.

My girlfriend has a Toshiba Satellite A305-S6905 laptop.

It came with Vista on it, and she has some sort of virus or malware on it that TrendMicro isn't picking up.  I run the program and it speeds things up, and then a few days later it's slow as heck again.

I put her on my Ubuntu box upstairs and she's had a month or two to play with it.  Then I booted off the installation CD on her laptop to make sure she really understands what it is I'm proposing.  She is fine with it.

So I got a USB drive of the same form factor and tried the old drive switcharoo trick to preserve her Windows drive as it is now just in case.

The problem is, the connectors are different.  The Toshiba has a fairly large connector that I'm unfamiliar with, and the USB drive looks to have either USB directly or maybe a micro e-sata or something on it.  The USB cable hooks directly to the drive rather than going through an intermediate cable and/or circuit board.

Likewise with the motherboard on the laptop, the drive hooks straight to the board with what appears to be a soldered-on connector.

So I guess I'm at a loss as to what to do next.

Ideally, I would be able to get a converter just for this to wedge in between the drive and the motherboard.  There's a cm or so to play with.

Failing that, if I could find the receipt I could exchange it, but what do I get instead?

Also failing that, can I copy /dev/sda2 /media/Elements/vista.raw and expect something useful I can copy back over at some point to get a real image?  That used to work with older stuff but I have no idea now.

---

### Post by Blasphemist on 2011-08-11
So you have a bad OS (vista) that is hosed in one way or another and you are trying to keep a copy of it as it installed now. Is that right? 

I'd look hard at just dumping what you have and starting clean with ubuntu but there are other options. From what I can see on that satellite, and I have a L505 that appears to be very similar, you can attach an external usb drive. You could do that and create a number of different backups. An actual backup, a copy of files that need saved, a copy of the partitions, etc.

My satellite came with vista just before Win 7 came out. As soon as possible I upgraded to win 7. I had defrag running nightly. When I first installed ubuntu I allowed it to shrink the existing windows partition and install dual boot. I've since shrunk windows further by trying to use win 7 to do that but eventually had to use gparted. With the additional space available I created a shared data partition for pictures, music, documents, etc. and 6 new distro partitions. I now have 7 linux flavors some of which change frequently and win 7. 

You sound linux literate and could do all of this and see what distro rocks her boat. Since she has vista now and not win 7, unless she has some specific need for windows, I'd blow it away and start over with linux. Next best would be to get installation media for windows and any needed windows specific software, then blow it away and start over. Copy any files that need saved and copy them back later.

---

### Post by 1clue on 2011-08-11
> **Blasphemist said:**
> So you have a bad OS (vista) that is hosed in one way or another and you are trying to keep a copy of it as it installed now. Is that right?


Exactly, as ridiculous as that sounds.  I need to keep the license and keep the files.  This is not my hardware.

> 
I'd look hard at just dumping what you have and starting clean with ubuntu but there are other options. From what I can see on that satellite, and I have a L505 that appears to be very similar, you can attach an external usb drive. You could do that and create a number of different backups. An actual backup, a copy of files that need saved, a copy of the partitions, etc.


I have the external attached now, trying the copy of the partition over to a raw file from the Ubuntu CD boot.

What sort of program do you use to back up a Vista system?

> 
My satellite came with vista just before Win 7 came out. As soon as possible I upgraded to win 7. I had defrag running nightly. When I first installed ubuntu I allowed it to shrink the existing windows partition and install dual boot. I've since shrunk windows further by trying to use win 7 to do that but eventually had to use gparted. With the additional space available I created a shared data partition for pictures, music, documents, etc. and 6 new distro partitions. I now have 7 linux flavors some of which change frequently and win 7. 


My goal was to have a complete drive for Vista and another for Ubuntu.  I have no desire to try a million distros.  I've already been through that, and anymore if I want to try a new distro I'll put it on a VM to see if I like it.

> 
You sound linux literate and could do all of this and see what distro rocks her boat. Since she has vista now and not win 7, unless she has some specific need for windows, I'd blow it away and start over with linux. Next best would be to get installation media for windows and any needed windows specific software, then blow it away and start over. Copy any files that need saved and copy them back later.

The need for Windows is simply to have an "undo" in case this one doesn't work out, I can put everything back exactly the way it was.

---

### Post by Blasphemist on 2011-08-11
OK then. There should be a backup built into vista. I don't have vista so I can't verify that or tell you how to get to it. I'd use that to back up the drive to other media, then I'd blow it all away and start it over with linux.

---

### Post by 1clue on 2011-08-11
Thanks, I'll check into it when this backup finishes.

---

### Post by oldfred on 2011-08-11
Does the System have a vendor recovery partition. If so you need to make the set of DVDs. That is just an image of the drive as purchased, not an install disk. You also should make a Windows repairCD as you should have a repair CD/USB for every system you have installed.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by 1clue on 2011-08-11
Went out and got another drive.  Ubuntu is installed, and the old drive is in an external enclosure.

Thanks for the help, I just saw what you're talking about and had a sudden uncontrollable urge not to boot back into Windows.  Ever.

---

### Post by 1clue on 2011-08-11
BTW I am pretty sure there was a virus on it now.  I browsed around from Linux, saw a folder with a random string of characters as a name, saw some files in there and searched on the names.  Don't recall what they were, but they were associated with a virus that Norton and similar don't know how to get rid of.

---

### Post by Blasphemist on 2011-08-12
Sound plan in my opinion. Good work! I do easily find things to learn in the linux and open freedom world but am much happier here!

---

### Post by 1clue on 2011-08-12
Yah, to be perfectly honest I don't so much mind paying for software.  My only thing is I don't like using an operating system which was designed to facilitate the distribution of malware, with the primary side effect of making you spend extra time to perform simple tasks.

---

