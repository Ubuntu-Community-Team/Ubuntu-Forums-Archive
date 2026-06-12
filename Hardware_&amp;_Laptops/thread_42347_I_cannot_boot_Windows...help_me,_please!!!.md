---
title: "I cannot boot Windows...help me, please!!!"
date: 2005-06-17
forum: Hardware &amp; Laptops
---

### Post by bobmario on 2005-06-17
Hello everybody!
I have a really serious problem. This is the third time that i'm asking for help here... i don't know how to do anymore. I hope that this time someone could help me!!!

Since i installed Linux (Ubuntu version) in my laptop (Fujitstu Siemens Amilo), i cannot boot windows anymore!  ](*,) 
If i try to boot Windows in the menu, what i have is a blinking cursor on the top on the left in my screen (i have than to restart my computer...). In my grub (that i wrote even here) everything seems to be good:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

In fact i have my windows partition in hda1, so the command is right.

I can see my windows partition from linux (i used the command mount), but of course i can only read those files.

I tried even with rootnoverify instead of root, and i even try without makeactive or chainloaer, and all the possible combinations, but nothing happened.

Linux is working without problems, but i don't know how to do to have my Windows again. Even because if i try to put the Windows installation CD, it doesn't work.
In fact if it starts form CD, it says “Verifying the hardware configuration...” and than it stops without saying nothing (just black screen). So i don't know even how to reinstall windows.

I hope there is someone that had my same problem and can help me...

Thanks a lot!!!

---

### Post by frodon on 2005-06-17
Does this link help you ? [http://www.frankandjacq.com/ubuntuguide/5.04/index.html#addwindowsentrygrubmenu](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#addwindowsentrygrubmenu)

---

### Post by bobmario on 2005-06-17
No, i'm sorry, but it doesn't help, because that's exactly what i have in my grub, so that's why isaid that everything is ok in the grub's configuration...

thank you anyway for your answer

 :-?

---

### Post by luca_linux on 2005-06-17
First of all, it's "rootnoverify".
Then do this:
```
sudo fdisk /dev/hda
```
Then type:
```
p
```
And see if the windows partition has the boot flag.

If not:
```
a
```
And then write the number of your windows partition.
Finally confirm the action.

---

### Post by bobmario on 2005-06-18
Thanks!

I followed your suggestion, bu still windows doesn’t boot.
First of all I changed root (hd0,0) in rootnoverify (hd0,0),
Then I did the command sudo fdisk /dev/hda

And when I digited p it was written:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
16 heads, 63 sectors/track, 116280 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30489    15366141    7  HPFS/NTFS
/dev/hda2           30489       46028     7831687+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3           46761      116280    35037765    7  HPFS/NTFS
/dev/hda4           46028       46761      369495    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/hda5           46028       46761      369463+  82  Linux swap / Solaris

I think that the flag that you were talking about is the star near to /dev/hda1, so once again everything seems to be good.

I tried anyway to press a and digit 1, the star disappeared and when I tried to boot windows I had the same problem.

I don’t know if you have some other suggestions…

---

### Post by luca_linux on 2005-06-18
Don't you get any error?

---

### Post by bobmario on 2005-06-19
What do you mean be "any errors?"

when restarting the computer and trying to boot windows i have just a black screen and blinking cursor!

---

### Post by Gezzer on 2005-06-19
when booting into linux hit the ESC key this will bring up the recovery mode use this mode to see if there are any error messages

Q. u did load grub to the MBR and not a separate partition ...

---

