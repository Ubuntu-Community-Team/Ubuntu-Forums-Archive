---
title: "Windows wants continuously runs chkdsk at startup.."
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by killians31 on 2009-09-02
Hello,

recently i have been trying to quad-boot my Asus G50vm-x1 with windows seven, ubuntu studio 9.04, fedora 11 kde, and backtrack 4 pre-final.

I finally got three of the four OS's to work properly, but that's a whole other story!

anyways, it seems that every time i boot into my windows partition via grub, windows wants to run a check disk. even when i try to abort the function, it will continuously count down and attempt to run a check disk. sometimes windows will boot up momentarily after the timer hits 0, but other times it will lock up. It seems to be somewhat inconsistent!

Is there anything i can do to disable this check disk at boot-up?

Any help is appreciated!

Thanks,
Ben

---

### Post by Mark Phelps on 2009-09-03
Have you actually let the chkdsk finish, or did you cancel it every time?

If it finished, did it report fixing anything?  Did it report any bad blocks?

If it's running every time you boot into Win 7, there are a couple of possible causes:
1) Failing drive
2) Bad drive-controller drivers.

To check the first, you can check the driver manufacturer's website for disk analysis utilities. They typically provide a way to scan the drive for errors, and do a much more through job than chkdsk.

I actually had the second happen to me on Vista because I had carelessly allowed Windows Update to automatically update my SATA controller drivers.  After that, I got forced chkdsks on every boot.  Had to rollback the drivers and use an third-party utility to recover the damaged files.

---

### Post by killians31 on 2009-09-03
It seems somewhat strange because the other day it was complaining about the D: drive, so i skipped the check and logged in and did a manual check disk on the D: drive, and no errors were found. When i rebooted, it wants to check disk on C: now. So i logged in and tried to do a manual check disk on C: but windows wont let me because it is already logged into C:, but it wants me to schedule a event for it (which never occurs).

When i do leave the check disk screen at boot, it just sits there with no advancement. I left it sit for 8 hours yesterday, and it didn't do anything!

i hope its not a failing drive (the laptop is only a year old), but i did perform many partitions which might have been overload on the drive when attempting my quad-boot.

---

### Post by Mark Phelps on 2009-09-04
Unfortunately, it's going to keep prompting you to run chkdsk until it successfully completes a run of it.  You should never opt out of chkdsk as that's an indication of possible file system corruption that needs to be fixed.

Don't know what OS you're running, but in XP and Vista there are ways to boot into a command line and from there, you should be able to run chkdsk.

---

### Post by Partyboi2 on 2009-09-04
If you know what brand your hard drive is go to their website and download the diagnostic tool to check the hard drive and see if your hard drive is ok.

---

### Post by ministoat on 2009-09-13
I'm having this problem since installing Karmic and setting mount-manager. I've completed four faultless chkdscks now, and it has only occurred since setting some permissions in karmic.

Could there be some flagging problem on the disk that is causing this?

---

### Post by newsoft on 2009-09-13
Download a diagnostic tool and check if your hard is compatible first

---

### Post by Partyboi2 on 2009-09-13
> **ministoat said:**
> I'm having this problem since installing Karmic and setting mount-manager. I've completed four faultless chkdscks now, and it has only occurred since setting some permissions in karmic.

Could there be some flagging problem on the disk that is causing this?
I have been having to run fsck a lot with karmic as well, maybe we should start a new thread in [Karmic Koala Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=359")

---

### Post by don242 on 2009-09-18
I just put Windows 7 on a couple of computers as well and am having the same issue with both. At boot up it wants to do a chkdsk about 50% of the time. I have let it complete the whole check but it still does it. This is happening on two computers so it is not an issue of failing hard drives but something to do with Windows 7.

---

### Post by Mark Phelps on 2009-09-19
Don242:

OK ... so go to a Windows Seven forum and post your question there.  I recommend the sevenforums site.  Has excellent support and lots of tutorials.

What about the name "Ubuntu Forums" is so hard for everyone to understand?

---

### Post by pickledegg on 2012-05-25
Hi, sorry to "bump the thread that's long since dead" but I thought I'd mention that I have a similar problem and although its obviously occurring in Windows 7, I think there's a possibility that its root cause is the Linux install.

I say this because a year ago (on a completely different machine than the one I use now), I set up a dual boot Win7/Ubuntu system. I had the annoying problem of windows 7 running a check disk every time I booted back into it after using Ubuntu. 

Initially I dismissed it as user error, but just yesterday I decided to set up a new dual boot system, and I have the exact same problem: Every time I exit Linux and reboot into Windows 7 it runs a CHDSK. Now is Ubuntu perhaps changing a part of the drive that windows expects to remain the same? If I could track it down it may help others in the same situation.

---

### Post by nothingspecial on 2012-05-26
Hi, rather than bumping an old thread to the top, please start a new one. Thanks :)

---

