---
title: "USB Storage Issues"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by ItaniKnight on 2007-05-20
It seems that there's a LOT of people out there who are having trouble with their removable media. Apparently, what happens is this: Files are copied to / from the disk, the dialog box goes away... But, when you try to remove the disk, it comes back, and should you remove it anyway the whole thing goes write-protected in a way that has yet to have a solution. I realise that there are many other threads and topics on this, but it's only because of those that I make this one. I'm hoping that some kind of universal solution can be found, one that will work for any USB drive. And, on top of that, I've been searching for a long while, so I know what doesn't work...

**The Symptoms:**
Complete loss of control over the USB drive seems to occur. Even the root user can't do anything to it, as the permissions are forced into the "read-only" mode. Worse, actually; I've found that it will tell me that I've copied files, let me eject the disk, then not remember the changes when it comes back in again. *Thunar* crashes any time I try to change them, and I can do absolutely nothing to it.

**Solutions that didn't work:**
Every single one that's been suggested so far. OS X can't even see it until I've taken it out; Windows will get to 100% formatted before telling me that it isn't, actually; I don't even know HOW to do a format under Ubuntu; I've changed the Windows registry, downloaded several disk-erasing programs, tried every USB slot on the damn thing with no success; Interestingly, Linux will eject it by itself occasionally, just removing it...
The main problem is that NOTHING can be done to the disk. At all.

**Any ideas?**
The drive I'm talking about now is a *Creative Zen Nano Plus*, an MP3 player more than a storage device, but I know for a fact that the same problem is all over the place. If anyone has anything that will definitely work (shoot, anything that might come close to working), PLEASE tell the rest of us!

---

### Post by ItaniKnight on 2007-06-03
Seventy one people have viewed this, and no one seems to have a solution. Great. Thank you SO much for making Ubuntu; I'd never have known just how annoying computers could get until using it.

The hell with this. I'm back on a Mac, and by the Faelkhan it's a damn sight better than Fake Windows.

---

### Post by vanadium on 2007-06-03
This is a known issue with Feisty. It worked well under Edgy. To work around it:
```

sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.backup


```
At that point, the right-click menu will change from Eject to Unmount. For USB sticks (and your Creative Zen) this isn an issue at all. After unmounting, you can safely remove the device.

Obviously, you probably won see this reply anymore, but it can be usefull for other people. This worked well under Edgy and I agree with you that it is very unfortunate that such a visible bug could make it into a stable version of Ubuntu.

---

