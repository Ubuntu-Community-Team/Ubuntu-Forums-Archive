---
title: "[SOLVED] cant boot from live usb"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by plasmarox on 2009-01-01
Hello, ive recently purchased a toshiba nb100  netbook, and since it doesnt have a cd drive, i need to boot USB. Ive booted from USB before, with no problems, but i cant now. I choose USB device in boot menu, and get a flashing dot. What now?

---

### Post by sandman652001 on 2009-01-02
are you shure your pendrive is not corrupt?

---

### Post by plasmarox on 2009-01-02
Thanks for your reply.
Highly unlikely, i made the pendrive only minuites before inserting it, although i will make it again.

---

### Post by 5BallJuggler on 2009-01-02
How did you make the pen drive? from the option on the admin menu?
What size is the drive?
Have you updated it, is it a persistance version?

---

### Post by plasmarox on 2009-01-02
The drive is a 1GB datasafe drive, persistence IS enabled, but only 128MB.

Yes, i used system>administration>make USB startup disk i ubuntu on my other PC (the M70 in my sig)

Ive booted from thi device before, at school and other pcs, i dont understand why its not working on my new PC.

---

### Post by 5BallJuggler on 2009-01-02
I know it should work on a drive that small, but i could not get it to work on a 4Gb stick because of the space, i'm currently using a 16Gb stick and still having some issues

I see your from the UK, did you use the method to make the live USB from "Linux Format" magazine?

---

### Post by plasmarox on 2009-01-02
What kind of problems do you have? Not booting or just being weird? If you think its the device, ill try with my 2GB stick...

---

### Post by 5BallJuggler on 2009-01-02
it wouldn't allow updates, when i first made the Stick I set aside 2Gb to my own files and 2Gb for linux. it kept failing on boot up, when i looked deeper it was because during the update the USB stick ran out of space.

I tried to run the install again on the same disk, allowing 4Gb to be allocated to Linux and Ubuntu, exactly the same issue.

I've installed it on a 16Gb Stick this morning, it is persistant, but it says the system as recovered from a crash or crash detected whenever i boot up, when i check it something to do with the new linux kernel not installing, i've reported the error to launchpad, hopefully they can assist.

---

### Post by plasmarox on 2009-01-02
Thats odd, using this stick ive been able to update, install programs etc. The only thing ive not been able to do is get rid of the default ubuntu user :(.

Anyway, i just tried the stick in my other pc, the M70, and i did check for defects, which worked just fine, no errors or anything. 

The only other thing i can do is buy a USB CD drive, but idk whether it would work natively, (ie able to boot from it)

---

### Post by 5BallJuggler on 2009-01-02
> **plasmarox said:**
> The only other thing i can do is buy a USB CD drive, but idk whether it would work natively, (ie able to boot from it)

I'm not sure either, sorry

---

### Post by davidshere on 2009-01-02
I know your laptop has a "boot from USB" option, but here's a solution for computers that don't:

[http://www.pendrivelinux.com/2008/11/15/usb-boot-cd-for-ubuntu-810/#more-680](http://www.pendrivelinux.com/2008/11/15/usb-boot-cd-for-ubuntu-810/#more-680)

You use a Boot CD in conjunction with the live thumb drive.  The boot CD does the initial load, and then hands everything off to the thumb drive.  (This is not the same as using the live CD with a thumb drive with persistence.)  I've been using this option on a Compaq Presario M2010US for a couple weeks.  Thumb drive is a 4MB Sandisk Cruzer Micro.

I did have one problem ... and had to format the thumb drive and start over.  I think this was because I removed the thumb drive while it was writing.

Something to try anyway.  Let us know if you do and how it goes.

---

### Post by plasmarox on 2009-01-02
Thanks for link.

The reason i want to do liveUSB is because i dont have a CD drive, and actually want to do a full install of ubuntu :P

---

### Post by davidshere on 2009-01-02
I wonder if you can make a thumb drive disk of the alternative install CD.

Or you could use WUBI to install from Windows.

---

### Post by plasmarox on 2009-01-03
Update:

Ive made my 2GB stick into a boot device. Now, i boot and i get:
```

SYSLINUX 3.63 Debian-2008-07-15 EBIOS Copyright (C) 1994-2008 H. Peter Anvin
boot:
Could not find kernal image: vesamenu.c32

```

I have no idea what to do next :'(

---

### Post by plasmarox on 2009-01-03
Sorted.

Reformatted the USB stick as a primary partition instead of an extended partition. (?).

Rebooted, works perfectly.

Marked as solved.

---

