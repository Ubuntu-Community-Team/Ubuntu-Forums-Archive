---
title: "Can't access Hard drive"
date: 2008-11-16
forum: Hardware
---

### Post by Igneo676 on 2008-11-16
Well, my Dad bought a new hard drive and we put it into his compy as a slave. A quick install of Ubuntu brought his computer to new life and things were going fine until today. We can no longer access the original hard drive, which has all his pictures, music, etc. and also has Windows (For my mom). Attempts to access it results in a quick error stating that it was improperly shutoff and tells how to force it but the command doesn't work.

Any attempts to login to Windows ends at the splash screen and it telling me to put in a hard drive.

I have a Windows XP disk around here somewhere, so, no reason to freak if we lose the ability to use XP (Ubuntu works so much better anyway). We NEED those pictures and such though.

Edit: Gparted says it's unable to read the hard disk

Help?

---

### Post by taurus on 2008-11-16
I assume the harddrive that you are talking about is /dev/sda1.  Try mounting it with force option like

```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force
df -h
```
Better back up those pictures from that drive because eventually, the force option will not even work.

---

### Post by Igneo676 on 2008-11-16
I did that, copying over every last little file on the drive. Thank you so much!

So, any idea what's going on and what I can do? Will I need to do a fresh install of XP for my Mom? I'm a bit confused

---

### Post by taurus on 2008-11-16
I assume XP is dead on that drive since you can't even boot from it to get to those pictures.  Therefore, you have to reinstall XP on that drive again if your Mom wants to use XP.  Then, XP will wipe GRUB from MBR so after you've finished installing XP, you need to reinstall GRUB so you can boot both Ubuntu and XP.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Igneo676 on 2008-11-16
Ah, again, thank you so much!

Looks like I've got some work to do >.>

---

### Post by caljohnsmith on 2008-11-16
Igneo676, there are some other options you can try before you do a full reinstall of Windows, because it may turn out your problem is simple to fix. The first place I would start would be to boot your Windows Install CD, go to the "recovery console" and do:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. After that, try booting Windows and see how far you get. There are some other tricks too that might fix your Windows, depending on what errors/behavior you get after doing the chkdsk. And also, you can always do a "Windows Repair" from the Windows Install CD, and that will reinstall all of Windows system files while leaving your installed programs and personal files untouched. If for some reason even a Windows Repair is not enough to salvage Windows (probably not likely), only then would I recommend reinstalling, but it's of course up to you. It mostly depends on whether you want to try and keep the programs you have installed in Windows.

---

### Post by Igneo676 on 2008-11-16
Heh, after I copied all the files onto the new partiton...
...windows decided to boot. Except now it seems completely dependent upon that new partition (which it has adopted as its new C drive) and quite possibly the old C drive (as G). Various programs will display as being in one or another when I hit properties.

This is the wierdest thing, but, i'm gonna see if that windows recovery thing does any good...
...heh....

Thanks for that information!

Edit: Interesting. The OS is dependent upon both the original hard drive and the new partition. Taking away one or the other makes it so it won't boot or operate correctly Running the windows recovery now

---

### Post by Igneo676 on 2008-11-16
Well, now the Windows booting doesn't work at all. It started truncating stuff and said the Filesystem was in disrepair.

And i've no admin password for the Windows recovery

---

### Post by 3bdel7akam on 2010-10-18
I using Ubuntu for the first time I install it with win7 in the same drive and can't access this drive .. plz help .

---

