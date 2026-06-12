---
title: "grub error 13"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by tadpole1954 on 2009-10-16
Hi.  I installed Jaunty a week or so ago in a dual boot with xp home edition.  Each os is one its own hard drive.  Now, I never use windows anymore, but my wife does on occasion.  Today, she tried to boot xp and grub gave her the error 13.  I went to menu.lst and this is what it says about my windows.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Windows NT/2000/XP
rootnoverify    (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

Can someone help me to get this going for her.  I honestly don't know what to do.  My search for the error 13 showed me different solutions.  Thanks.

---

### Post by tosk on 2009-10-17
If XP is on it's own drive, try booting directly from that drive. You may need to change the boot order in the BIOS. If XP won't boot directly from that drive then it might be an issue with the drive itself and not GRUB.

You might also try altering your menu.lst entry for XP to the following and seeing if that allows GRUB to pass control to NTLDR on the other drive:

```
title Microsoft Windows XP Home Edition
rootnoverify (hd1,0)
savedefault
makeactive
chainloader +1
```

---

### Post by tadpole1954 on 2009-10-18
Thank you Tosk.  Neither of those suggestions got me anywhere.  However, I changed (hd1, 0) to (hd0, 0) and everything now works like it should.[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

