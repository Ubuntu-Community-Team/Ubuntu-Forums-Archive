---
title: "Files are saved to USB then dissappear..."
date: 2010-01-07
forum: Hardware
---

### Post by gatorbrit on 2010-01-07
I am running 9.10 64 bit on a toshiba laptop using a WD passport external hard drive.  The drive is plugged in all the time.

I do programming in kate.  When I save a file the file is visible in the folder on the usb drive.  Then when I shutdown and reboot and go to see the file it isn't there.  The same effect also happens if I update an existing file.  The changes appear to be made and the programs run as if the changes are, but they are not permanently saved to the hard disk.

However, I am able to make new folders on the hard disk. 

Any ideas - ?

Update:  If I "safely remove hardware" by left clicking on the drive icon on the desktop, this problem doesn't seem to occur.

Seems that I should be able to just turn off the computer without unmounting the drive without the risk of loosing my data.

---

### Post by SecretCode on 2010-01-07
Answer 1: You should always unmount any external drive before removing it or powering down. (Safely remove goes one step further, powering down the drive device as well.)

If you don't like answer 1, you'll need to investigate answer 2, which involves disabling write caching on the device - at some cost in performance.

---

### Post by gatorbrit on 2010-01-07
> **SecretCode said:**
>  write caching on the device 


"write caching"   I wasn't aware that was going on. Now that I know I understand a bit better.  I just wish I had known this before!

But thanks for the answer.  I'll make sure I unmount.

It would seem that a prompt like "do you want to unmount before shutdown" would be useful though.

---

### Post by SecretCode on 2010-01-07
Or an automatic unmount during shutdown. Now that you mention it, I'm pretty sure Windows safely unmounts any USB devices during a normal shutdown.

*off to do some tests*

---

