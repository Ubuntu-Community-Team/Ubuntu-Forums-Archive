---
title: "windiws install after ubuntu install,cant access ubuntu??"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by rixtr66 on 2009-01-17
I installed windows xp after installing ubuntu 8.10 to my 250gb usb hd,i tried using super grub boot disk to restore ubuntu as the mbr,but that didnt work:(so i tried accessing the usb drive but its not showing up in my computer?things where fine till i installed windows!normally im a die hard linux user but ive recently been using tracking and sampling software like lmms,and renoise,and i wanted to use vst's and vsti's,not to mention software thats only available on windows.however now im having second thoughts!anyway can any one help me access my usb hd or better yet help me get ubuntu back to the mbr,i dont want to reinstall,because i have ubuntu set up just right.
any help would be appreciated!!!keep in mind i cant access the ubuntu drive so i cant post outputs.
Rick ](*,)

---

### Post by albinootje on 2009-01-17
> **rixtr66 said:**
> I installed windows xp after installing ubuntu 8.10 to my 250gb usb hd,i tried using super grub boot disk to restore ubuntu as the mbr,but that didnt work

There's this to read.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

And can you boot from the Ubuntu installation cdrom, and post the output of :
```

sudo fdisk -l

```
with your usb-disk attached.

---

