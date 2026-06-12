---
title: "Grub error 17 Vista/Linux"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by demorality on 2009-03-15
so im a realative computer noob in terms of bios and OS go-between

i recently installed a copy of Ubuntu 8.10 on a second harddrive and tested it for a while, i decided yesterday that i wished to get rid of it so i just reformatted the drive it was on using Vista disk management, carried on using vista for the rest of the night and copied files onto the other drive then switched it off

so this morning i go to reboot and now Ubuntu is gone and vista is the only operating system but grub will not find it and i get error 17

aside from reinstalling Vista (which i dont really want to do because i have files i need to keep on both hard drives now) is there any way for me to bypass grub and load vista so i can get rid of it or something

---

### Post by mhgsys on 2009-03-15
So actually this is a vista question, 
Anyway, 
Found this for you :
Try to boot with vista cd , select repair/ recovery whatsoever
(I don't boot vista,)


then in "dos"/cmd"
C:\> mbrfix64.exe /drive 0 fixmbr /vista /yes

This wil get your vista bootloader back.
if you don't have vista cd try this link.
[http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc//#more-558](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc//#more-558)

Good luck.

---

