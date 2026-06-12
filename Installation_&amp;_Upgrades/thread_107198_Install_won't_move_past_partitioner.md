---
title: "Install won't move past partitioner"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by rick333 on 2005-12-22
I'm trying to install Ubuntu 5.10 on a AMD Athlon box. I ran the live CD and most if not all things seem to work, so I figured the install would be easy. 

When I run the installer, I get up to the partitioning phase and cannot get past it. I have a WinXP partition and a /home partition (from a MEPIS installation), both of which I want to keep. I've tried deleting the existing root partition (which has MEPIS on it) and recreating it, deleting it and not recreating it, configuring the Logical Volume Manager (whatever is meant by that) -- and I've done each of these things at least twice just to check whether I've missed something. When I select <Go Back> from the partitioner  I'm brought to the main installer menu. I then select the next item in thee menu after the partitioner, "Install the base system". When I do so, Ubuntu brings me right back into the partitioner.  

Any help on this would be greatly appreciated. Thanks.

Rick

---

### Post by az on 2005-12-22
If you do it by hand, you need to assign a partition the / mount point to continue.

If you delete a partition and create free space, pick guided partitioning and it will do it all for you like McDonald's.

---

### Post by rick333 on 2005-12-22
Tried that.. that was the first thing I did. btw, next to the root partition, the partitioner displays a downward pointing jagged arrow. Does this mean anything?

---

### Post by az on 2005-12-22
[QUOTE=rick333]the partitioner displays a downward pointing jagged arrow. Does this mean anything?[/QUOTE]
It means that you set the partition to be formatted (zapped) and then used. 

Do you try to make the partitionner go after you set everything up, or are you hitting "Go Back"?  What happens after that?

You can view error messages on CTRL-ALT-F3

CTRL-ALT-F1 is the console used for the installer.

---

### Post by rick333 on 2005-12-22
I've tried all sorts of things. Would you be so kind as to list out the actions that I should be taking to accomplish this? Remember, I'm trying to overwrite an existing Linux installation, but keep my /home and Windows partitions. Thanks in advance.

---

### Post by rick333 on 2005-12-22
Fixed! The last choice "Finish the partitioning" or whatever it says was not visible on my screen because of the number of partitions on my disk. Hence, I did not know that option was there until I accidentally scrolled down and it appeared! Thanks for the help anyway. Hopefully, the rest of the installation will be smooth.

Rick

---

### Post by az on 2005-12-22
I had that happen to me too, once.

---

