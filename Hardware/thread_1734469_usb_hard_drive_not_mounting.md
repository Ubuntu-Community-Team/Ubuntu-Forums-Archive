---
title: "usb hard drive not mounting"
date: 2011-04-20
forum: Hardware
---

### Post by digitalrealm on 2011-04-20
Hello all

First time using the Forums but it dose not feel that way.  Can't wait for 11.04

I hope this is the best place for this post.

For a while I have had a usb hard drive that has not mounted at all.  Everything I have come across that may help requires the drive to mount on the system.  There is a light on the drive so it appears to be working.  Hose anyone have any ideas about how I can get the system to reconnoitre the drive.

Thanks

Dan

---

### Post by collisionystm on 2011-04-20
open terminal, unplug your flash drive, plug back in.

type dmesg

do you see output about the drive being connected?

do lsusb (LSUSB) and see if it lists your drive.

Try running System, Administration, Disk utility

Do you see your drive there? It may have a broken partition and thats why it wont mount.

---

### Post by digitalrealm on 2011-04-20
thanks for the quick reply

dmesg has output that a high speed drivce was detected.
[10847.892120] usb 2-1: new high speed USB device using ehci_hcd and address 7

But lsusb dose not list the drive

Dan

---

### Post by zorkerz on 2011-05-02
I am having the same problem in ubuntu 11.04 its occurred since I switched over in alpha3. The drive worked fine in ubuntu 10.10 on the same computer and still works on xp machines.

The only usb reference in dmesg is similar to digitalrealm's.
lsusb does not have it it all. 

Any idea what else we can do to try and figure this out?

---

### Post by aleolivat on 2011-05-02
I am having the same problem in natty.   I too did not have any trouble in maverick.   With lsusb command it does not show any usb hdd (and takes very long time to show the result).   When I tried dmesg it shows "new high speed USB device using ehci_hcd".    

I can use an usb stick stick with no problem, the usb hardrive seems to be the only affected with this problem.

---

### Post by zorkerz on 2011-05-02
Ive posted a question on launchpad answers here[ https://answers.launchpad.net/ubuntu/+question/155446]("https://answers.launchpad.net/ubuntu/+question/155446") no response as of yet. Hopefully we can get to the bottom of this.

---

### Post by Philip Farrugia on 2011-05-02
Have found my HTC Desire phone won't mount. It worked a few weeks ago and assume 11.04 has somehow broken usb detection. At least for my phone. Posting this so I can follow any developments.

---

### Post by Moloch85 on 2011-05-03
My Archos mp3 player has the same problem, it doesn't show up with lsusb since i uprgraded to natty (and the same thing with the live version)

---

### Post by zorkerz on 2011-05-03
Ok I got this fixed on my computer, through my question here [https://answers.launchpad.net/ubuntu/+question/155446](https://answers.launchpad.net/ubuntu/+question/155446)

Basically install and open mountmanager then use the usb wizard to add your drive. Now your usb drive should automount and you can remove mountmanager.

---

### Post by aleolivat on 2011-05-04
I tried to follow the instructions, but I could not get it to work on my computer.    I will try to keep searching for a solution.   Thank you anyway.

---

### Post by zorkerz on 2011-05-04
Ill try to give some more precise directions of what worked for me because I had a hard time figuring it out myself. It would be great if somebody would try this to see if it is a reproducible workaround.

In mountmanager select USB Wizard in the tools menu. 
**Introduction**
Just press Next.
[B]Choose Device to Configure
[/B]I left  "Device is not Connected" selected (this was the only option available even though my drive was connected) and hit next.
 **Device Definition** 
Here I did a lot of guessing after reading the information about each field. Non of it is very clear, I expect many of these fields should need inputs specific to your usb drive if the inputs are required at all.
Device Name: I put "sdb2"
Vendor: I suspect this is an unnecessary field I put in "Western Digital" for the manufacturer of my drive.
Model: Again this may be unnecessary but I put in my drives model number. "WD10000S1H-00"
Subsystem: The information discusses two options here I put in "block"
Bus: "usb" as they say in the information.
Then press Next[B]
Configure Device Mount Point[/B]
I set my mount point to "/media/testusb" I believe any location you specify would be  fine.
**Configure Auto Mounting Options**
I set the filesystem to ext3 because there was no ext4 option then clicked next
**Access Options**
I just clicked next through this leaving the defaults
**Results**
I just clicked finish to get through this.

Finally I unplugged my usb drive then plugged it back in, ubuntu automounted it to the unity launcher and I was able to delete the mount point I had added through mountmanager and remove the application entirely from my system.

---

### Post by aleolivat on 2011-05-06
Zorkerz, thank you very much for the detailed explanation.   I followed your instructions and tried many times, but I still failed to mount my hard drive.     

I needed to take out the data, so I used a live usb with Lucid, and it mounted with no problem.    So even if I cannot use the usb hard drive immediately, I at least have the data out.    

I have been researching a little more and it seems some people have reported similar problems on previous versions of Ubuntu.    So I still do not know what the problem really.  It seems people have mixed results when it comes to fixing this problem.  

Anyway, thank you again.

---

### Post by mojoeschmoe on 2011-05-21
Did the mountmanager solution work for you? I'm experiencing the same problem with my HTC Desire

---

### Post by mcgavinz26 on 2011-09-17
Hi, long time reader, first time poster.  

Nothing previously mentioned in this thread worked for me.  After much searching I ended up here: 
[http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html](http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html)

That says that you need to disable the "Legacy Floppy" option in the BIOS of your PC.  I have an Intel D510MO and in my BIOS the option was called "USB Legacy" not "Legacy Floppy".  It was found in Advanced->USB (something like that).  I've plugged in 3 different flash devices now and have had no problems.

I hope this helps someone else as well... and I hope it keeps working for me.

---

### Post by aleolivat on 2011-09-17
Thank you very much mcgavinz26 !

I had some time, so I tried immediately, and it worked!, finally.   Up until today the usb hdd was just collecting dust in some corner of the room.

I can use again.   I hope it works for everyone.=D>

---

### Post by mcgavinz26 on 2011-10-01
Still working for me after a lot of rebooting.  Still can't believe I helped someone with linux stuff!

---

### Post by Lexyboy on 2012-03-22
> **mcgavinz26 said:**
> Hi, long time reader, first time poster.  

Nothing previously mentioned in this thread worked for me.  After much searching I ended up here: 
[http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html](http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html)

That says that you need to disable the "Legacy Floppy" option in the BIOS of your PC.  I have an Intel D510MO and in my BIOS the option was called "USB Legacy" not "Legacy Floppy".  It was found in Advanced->USB (something like that).  I've plugged in 3 different flash devices now and have had no problems.

I hope this helps someone else as well... and I hope it keeps working for me.

Yay!  Finally a solution - I've had the same problem as OP (same dmesg messages, seen is lsusb but can't mount) and nothing seemed to work - reformatting the disk on a PC, mountmanager... until this!  Strangely USB disks used to work fine, don't know why this would have changed :-k

---

### Post by mnkymnky on 2012-10-04
thank you. using mount manager fixed my problem and i can now access my backup files.

---

