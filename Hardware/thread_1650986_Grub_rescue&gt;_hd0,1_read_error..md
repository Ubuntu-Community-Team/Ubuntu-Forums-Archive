---
title: "Grub rescue&gt; hd0,1 read error."
date: 2010-12-22
forum: Hardware
---

### Post by razorboy5 on 2010-12-22
Hey
I just booted up to find my netbook (Asus Eee pc) in this state

```
 error:hd0,1 read error.
grub rescue>
grub rescue> ls
(hd0) (hd0,5) (hd0,1)
grub rescue> ls hd0,1
error: hd0,1 read error.
```

read several threads about the topic and different threads was caused due to different problems.

So far I've taken apart my netbook, removed the hard drive and put it back. It gave me the same error. 
Tried to boot up live cd to attempt a re-install that didn't work.
I'm 99% sure at this point it's just the hard drive that's dead can anyone make this a 100% accurate diagnostic? Googled for diagnostic tools but couldn't find one that'd run off a usb stick (most required cd drive which my netbook does not have)

(ps. have to drive 2 hrs to my parent's house after this post but will check back ASAP)

---

### Post by oldfred on 2010-12-22
If you are booting the liveCd from a USB. Look in Disk Utility under System, Administration. If you click on the drive in the left panel,  it should show Smart status as one of the choices on the right.

---

