---
title: "Unable to repartition to dual boot!"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by waba on 2009-07-23
hello, could someone please help me? iim installing ubuntu 9.04 to dual boot with Windows XP, so have the live cd. my hard drive is 250gb, with 80gb free. however, when it comes to installing ubuntu, i try and increase its partition to 50gb with the slider, but get the message"an error occured while writing the changes to the storage device. the resize operation has been aborted" and i can't seem to reduce the size of the XP partition. help!
 
thanks

---

### Post by ajgreeny on 2009-07-23
Make sure your windows is defragged a couple of times, preferably in safe mode and with virtual memory/page file turned off, if you know how to do that, though turn it back on again afterwards, before you forget.  Now boot the ubuntu live CD and try again.

Don't forget, however, the fact that you have 80GB free does not mean that you can have 80GB available for ubuntu as windows will insist that there is some free space available to it as well as the space it actually uses.  It may well be that on a 250GB drive with already 170 used the overhead that windows retains is the 30GB that you would prefer for ubuntu.

In summary, try it out, but you may be stuck with what you already have.

---

