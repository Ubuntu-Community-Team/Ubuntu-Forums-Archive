---
title: "mkusb questions"
date: 2020-11-11
forum: Hardware
---

### Post by jgw on 2020-11-11
I have been trying to figure out how to use msusb.  I have read several articles on this one and they tend to confuse.  What I am trying to do is to take a curretn usb stick and return it to its initial settings (1 partition, no nuthin - as bought).  this is a 62gb sandisk stick, single partition.  The stick I am dealing with was a bootable ubuntu iso file with 3 partitions.  Disks showed it with three partitions (1 at /dev/sdd1, 2 at /dev/sdd2, and 3 at /dev/sdd3).  I am simply trying to make the stick go back to original settings.  I read man mkusb first.  That even had me confused.  There were 2 places that said it would reset the stick.  Apparently I can run it as plain mkusb, then I choose 'd' for 'dus' (dus 12.6.4) got a message that it will deal with the whole stick.  Now, apparently, I have two choices, the first might be dus s /dev/sdd (assuming that sdd without the 1,2,3 means the whole stick)  OR I can say dus-restore which will, in theory, restore the stick to its initial state.  I have tried both to no avail.  on one I got a message that said "no pff input" which I have no idea what that means.  I tried to find it but failed.  Basically the stick remained the same throughout and i still have the three partitions.  

then I found; [http://www.linuxandubuntu.com/home/restore-corrupted-usb-drive-to-original-state-in-linux](http://www.linuxandubuntu.com/home/restore-corrupted-usb-drive-to-original-state-in-linux)  which had a completely different way to do the the restoration with mkusb.  This wants me to reinstall mkusb (its already installed) and then proceed to just run it and it will magically restore the offending stick.  that one is, apparently magic.  I tell it nothing, just run it and it does it.  I don't tell it anything, don't tell it what stick to deal with, etc.  It scares me so I have not messed with that one.  

There are others but, hopefully, somebody will understand my concerns and aim me at the correct solution.  I have two hard drives on this machine and really don't want to do anything to them.  Just fix the usb stick.

Thank you....................

---

### Post by rbmorse on 2020-11-11
Here's the MKUSB Wiki:


[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)


It'll tell you everything you want to know.

---

### Post by C.S.Cameron on 2020-11-12
This will pinpoint the info you seek from rbmorse's link:

[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)

Select "restore to a standard storage device"

---

### Post by sudodus on 2020-11-12
> **jgw said:**
> I am simply trying to make the stick go back to original settings.  I read man mkusb first.

Yes, this is possible (and easy) as described in the previous answers. You had bad luck because you got started in a complicated way.
> 
Apparently I can run it as plain mkusb, then I choose 'd' for 'dus' (dus 12.6.4) got a message that it will deal with the whole stick.

So far it is correct.
> 
Now, apparently, I have two choices, the first might be dus s /dev/sdd (assuming that sdd without the 1,2,3 means the whole stick)  OR I can say dus-restore which will, in theory, restore the stick to its initial state.  I have tried both to no avail.  on one I got a message that said "no pff input" which I have no idea what that means.  I tried to find it but failed.  Basically the stick remained the same throughout and i still have the three partitions.  

1. [FONT=Courier New]**dus**[/FONT] wants you to select target device in dialogue, and does not accept the target device as a parameter,

so [FONT=Courier New]**dus s /dev/sdd**[/FONT] does not work.

2. [FONT=Courier New]**dus-restore**[/FONT] is supposed to be called from [FONT=Courier New]**dus**[/FONT], where the target device is selected. The reason is to avoid selecting the wrong target device (and avoid destroying valuable data).
> 

then I found; [http://www.linuxandubuntu.com/home/restore-corrupted-usb-drive-to-original-state-in-linux](http://www.linuxandubuntu.com/home/restore-corrupted-usb-drive-to-original-state-in-linux)  which had a completely different way to do the the restoration with mkusb.  This wants me to reinstall mkusb (its already installed) and then proceed to just run it and it will magically restore the offending stick.  that one is, apparently magic.  I tell it nothing, just run it and it does it.  I don't tell it anything, don't tell it what stick to deal with, etc.  It scares me so I have not messed with that one.  

There are others but, hopefully, somebody will understand my concerns and aim me at the correct solution.  I have two hard drives on this machine and really don't want to do anything to them.  Just fix the usb stick.

Thank you....................

```

$ **dus**
[sudo] password for sudodus:   {Enter password here; there is no echoing; then press the Enter key}
live system or temporary superuser permissions
{You should see a dialogue window ...}

```

The solution is to let mkusb-dus reach a dialogue window. Select OK to continue until a dialogue window where you select

**'restore to a Standard storage device'**

press OK and continue to the next dialogue window ...

See the attached screenshot of the crucial dialogue window.

---

### Post by jgw on 2020-11-12
Thank you for the information - I will study it!

thanks again!  will mark this one as solved..............

---

