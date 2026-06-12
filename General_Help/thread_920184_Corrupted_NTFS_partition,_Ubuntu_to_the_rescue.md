---
title: "Corrupted NTFS partition, Ubuntu to the rescue?"
date: 2008-09-15
forum: General Help
---

### Post by evilkarma on 2008-09-15
I have a very tricky problem in which my ntfs partition seems to be corrupted in some unique way in that I cannot boot any windows based software. Booting into windows or safemode causes a BSOD c000021a {Fatal System Error} and I am unable to fix it in my current situation. I've tried [ubcd4win]("http://www.ubcd4win.com/") (based on BartPE) and an oem windows xp disk - here's what happens: as soon as the windows logo screen finishes loading (or in the case of the recovery console, near the end of the loading process before you even reach the menu), the computer just shuts off. This makes it impossible to do anything.. even reinstall windows. Thankfully I dual boot and have Ubuntu installed on a separate partition which is a huge help. Surprisingly, I can mount the ntfs partition from Ubuntu just fine and read/write works 100%.

This all started when I updated the nvidia drivers for the laptop to some ones from laptopvideo2go.com for windows xp - I even matched the drivers to my exact DEV and SUBSYS values of my video card. I'm a big fan of always being up to date, but after an hour or so of World of Warcraft running, the computer shutoff completely. Afterwards, the nightmare i've described has had me trying everything for the past 3 days. After two days, I finally fixed it! Randomly, I was finally able to boot into the recovery console using the windows xp disk. I ran chkdsk and that's it. Booted into windows and problem fixed! But, to my demise, my lovely gf eventually launched and started to play WoW again (i figured the laptop GPU had just overheated and the hard disk was randomly corrupted from the shutdown). Whatya know, a few hours of gaming and the laptop shuts itself off.. SAME **** ALL OVER AGAIN. Once again, nothing windows based will boot. I've tried getting at the recovery console a dozen times and the computer shuts off at the same point. I've tried both these disks on my desktop computer and they work fine. All of this to me that the problem is with the ntfs partition, yet the dilemma is that at the moment only linux can touch it and only windows tools can fix it.

Using Ubuntu, i have tried a number of things to try and fix the ntfs partition. I've ran memtest and hard disk diagnostic utilities that find 0 problems, and i've even used Ubuntu to copy over the registry hives from a system restore backup with no success. I've tried _ntfsfix_ so it marks the drive as dirty so booting to windows will do it's little chkdsk, but i guess the volume dirty chkdsk is not the same as the recovery console's because i did this the first time around with no success. I've tried linux tool _testdisk_ to check the bootsector (which matches the backup) and had it repair the MFT, but no success there either. As far as i've looked there is nothing available for linux that will match chkdsk.

I know you guys are smart so there might be a way to fix this given we know the cause and solution. Any idea?

---

### Post by rraj.be on 2008-09-15
> **evilkarma said:**
> As far as i've looked there is nothing available for linux that will match chkdsk.

I know you guys are smart so there might be a way to fix this given we know the cause and solution. Any idea?


This is the command used to check the whole disk

```
sudo fsck
```

try this for more help and options

```
man fsck
```

---

### Post by caljohnsmith on 2008-09-15
So you have an OEM Windows CD and not a Windows Install CD? So probably the OEM CD won't let you do a "Windows repair"--it will only let you do a full reinstall? If that is true, sounds like you might have to just save all your important Windows files while you are in Ubuntu, and do a full Windows reinstall. I would format your Windows partition first though so you can start clean, and hopefully the OEM CD won't crash then. Let me know how it goes or if you come up with something different.

---

### Post by evilkarma on 2008-09-15
Thanks for the replies.

An OEM Windows XP cd is the same as a windows install disk :P. PC shuts off as soon as it reaches the menu where you choose recovery console or to install windows. So far i've been able to access the NTFS partition from windows using NTFS 4 Dos 1.9 from [Hiren's BootCD]("http://www.hiren.info/pages/bootcd") - the chkdsk it comes with ran and all, but didn't fix it. I found this thread where someone has the same problem as me though and they mention a "private" version for $4.
[http://www.ocforums.com/archive/index.php/t-433782.html](http://www.ocforums.com/archive/index.php/t-433782.html)

This private version supposedly includes a special version of chkdsk that some guy put together, explained [here]("http://www.bootdisk.com/ntfs.htm"). What i'm gonna try is copying over the i386 files from my Windows XP disc to the ntfs partition, then boot into ntfs 4 dos and run the chkdsk that's inside the i386 folder (hope it's the same as the recovery console and it actually runs). If that don't work, i'll shell out $4 for that private version. If that don't work, well i'll have to hope that formatting the partition will let me install XP. Probably would.

Another thing i was thinking.. anyone know anything about vmware? I wonder if i could emulate windows inside of linux in order to boot into recovery console? I've never done any emulating, so i really don't know how it works.

---

### Post by evilkarma on 2008-09-17
I tried the $4 chkdsk private thing, wasn't any different (in fact, it looked like an old version of the one you can get for free). Next I tried vmware and i was actually able to get into the recovery console without the computer shutting down :popcorn:. Very odd huh? Didn't fix it though and i'm positive it was making changes to the partition.

Anyway, I finally said screw it and formated the partition, but to my surprise, I still can't get to the xp install screen before the computer shuts off! I have no idea why this is still happening - it just makes no sense. I completely blanked the ntfs partition so it's not even ntfs format yet. Why is it that it runs in vmware perfectly but not on the host? 

I wish i could install xp onto the harddisk from vmware, but it doesn't work like that I guess. It's like installing xp on one computer then taking out the hard drive and putting it in another - different hardware. Perhaps that is why there's no problems in vmware. Could this be some type of hardware problem? 

I'm really stuck here... stuck with Ubuntu on my laptop isn't a bad thing, but I have to have Winblowz on here for work soon =/. Please, any ideas would be great - i'm totally stuck. :confused:

---

