---
title: "messed up MBR"
date: 2008-05-19
forum: Hardware
---

### Post by starvingartist on 2008-05-19
Setup:
One laptop with unpartitioned HDD, one Xubuntu 8.04 on a USB drive.

Problem:
GRUB doesn't work for XP. The only option I get when booting is Xubuntu. Great OS, but I need XP for work tomorrow. :)

My HDD isn't recognised at all when I use Super Grub Disk. Gparted does recognise it in Xubuntu, but shows a warning sign (doesn't explain it, unfortunately).

Any attempt at reinstalling the MBR (syslinux) through Super Grub Disk have failed. When trying to access XP the only output is:
makeactive
chainloader +1
boot
GRUB

... and that's it. As this is a company laptop, I do not have the XP disc. I would love to be able to try 'fdisk /mbr' or NTLDR somehow. Any help is greatly appreciated.

And yes, I know I shouldn't have done this without adequate recovery gear handy.:(

---

### Post by nick_h on 2008-05-19
You can restore a Windows MBR using the ms-sys package. Have a look at the following howto - [HOW TO: Recover Windows MBR using Ubuntu LIVE CD](http://ubuntuforums.org/showthread.php?t=622828)

---

### Post by starvingartist on 2008-05-19
hmmm... even with all software sources open it cannot find the file ms-sys.:confused:

---

### Post by d-mart on 2008-05-19
I always use the super grub live cd when I have any grub issues

Sorry didn't read post carefully enough

however i did have this problem before and i believe i fixed by following this 

[http://mandrivausers.org/lofiversion/index.php/t46674.html](http://mandrivausers.org/lofiversion/index.php/t46674.html)

---

### Post by starvingartist on 2008-05-19
> **d-mart said:**
> I always use the super grub live cd when I have any grub issues

I seem to have used that CD to break my MBR, or more specifically: I removed the MBR completely from hd0. However, for some reason it won't reinstall.

---

### Post by d-mart on 2008-05-19
the only thing i could think of off the top of my head to fix it is to remove the usb and run supergrub just trying to just get windows to boot by using the options on supergrub if you can get that done then you just need to change your bios to boot from the usb before your hdd and install grub on your usb so it only uses grub when the usb is inserted.

Sorry if this doesn't help but its all i can think of right now and i have to leave in a sec.

ps here are two more links that discribe using "zero fill" to fix your boot of xp
[http://www.codeproject.com/KB/work/installwindowsxp.aspx?df=100&forumid=334362&exp=0&select=1764691#xx1764691xx](http://www.codeproject.com/KB/work/installwindowsxp.aspx?df=100&forumid=334362&exp=0&select=1764691#xx1764691xx)

[http://ubuntuforums.org/archive/index.php/t-593740.html](http://ubuntuforums.org/archive/index.php/t-593740.html)

however i would be real carefull using "zero fill" sounds sketchy to me

---

### Post by starvingartist on 2008-05-20
SGD doesn't help at this moment, my mistake was obviously major. Apparently I removed all the boot info from the XP drive.

One thing I was thinking (long shot): if I want to run fixmbr, could I install XP Home on my thumb drive, then boot from that and fix the MBR of the original XP corp from there?

Getting desperate here... does it show? ;)

---

### Post by nicedude on 2008-05-20
You could use an Ubuntu Live disk to boot to a working environment and then run grub and have it reinstall its self to your MBR. If I read your description of your problem correctly then you have XP on your laptop hard drive and you have installed Xubuntu to a USB stick if that is the case then when you installed Xubuntu grub rewrote your laptop hdd mbr and that is where your trouble lies. Your usb drive should have a directory /boot/grub/ on its root that will contain your Grub menu.lst which is the list of available systems to list at boot time if you edit that file correctly you should be able to boot to XP again. Also there is a way to use advanced grub commands at boot and thereby call the chainloader but I don't know them off the top of my head so maybe someone here can chime in with that info.

You could also get a bootdisk from [http://www.bootdisk.com/](http://www.bootdisk.com/) for XP that might let you fix MBR if my other advice is unworkable

Sorry to hear you goofed up your work PC :-( hope you get it fixed before work :-)

If I am wrong about your predicament sorry.

---

### Post by starvingartist on 2008-05-20
> **nicedude said:**
> You could use an Ubuntu Live disk to boot to a working environment and then run grub and have it reinstall its self to your MBR.Well, Xubuntu is working fine. That's what I'm using right now. IT's just that the HDD with XP isn't recognised at all any more -- not even by Super Grub Disk. However, when checking with gparted I can see that it still exists.

> If I read your description of your problem correctly then you have XP on your laptop hard drive and you have installed Xubuntu to a USBPrecisely.

>  if that is the case then when you installed Xubuntu grub rewrote your laptop hdd mbr and that is where your trouble lies. Your usb drive should have a directory /boot/grub/ on its root that will contain your Grub menu.lst which is the list of available systems to list at boot time if you edit that file correctly you should be able to boot to XP again.I'd be happy to if I knew how. :) The current situation: the GRUB menu loads fine for Xubuntu, but doesn't display XP at all. Booting XP directly from SGD doesn't work, reinstalling the MBR with SGD doesn't work. It seems I have manually removed something (?) which was critical.


> Also there is a way to use advanced grub commands at boot and thereby call the chainloader but I don't know them off the top of my head so maybe someone here can chime in with that info.That's about the time where I messed it up. After the chain loader thingy was done, neither OS would start. Had to reinstall Xubuntu completely to get that functioning on my USB again.

> You could also get a bootdisk from [http://www.bootdisk.com/](http://www.bootdisk.com/) for XP that might let you fix MBR if my other advice is unworkableInteresting, will look into that right away!

> Sorry to hear you goofed up your work PC :-( hope you get it fixed before work :-)My fault for not leaving well enough alone.:lolflag:  Thanks for the input!

---

### Post by nicedude on 2008-05-20
OK starving artist here is some advice for if your 

Reboot the pc and press escape to see the grub menu if it is not displaying , then press "c" to get a grub command prompt

NOW TYPE THESE COMMANDS ONE AT A TIME
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

Enjoy XP as that should work assuming XP is installed on your laptops first partition. Please report your results.

---

### Post by starvingartist on 2008-05-20
entering these commands gives me:

Starting up...
GRUB

... and then nothing happens. No drive spin or anything. :(

---

### Post by nick_h on 2008-05-20
I have just checked and the ms-sys package is not yet available in Hardy. The [www.bootdisk.com](www.bootdisk.com) idea is a good one.

I assume you cannot mount your XP drive in Xubuntu to check that the XP system files are still there.  The fact that neither SGD nor gparted can see your HDD is bad news.

---

### Post by starvingartist on 2008-05-20
> **nick_h said:**
> I have just checked and the ms-sys package is not yet available in Hardy. The [www.bootdisk.com](www.bootdisk.com) idea is a good one.
I'd be happy to reinstall Gutsy just to get this to work. Is that feasible?


> I assume you cannot mount your XP drive in Xubuntu to check that the XP system files are still there.  The fact that neither SGD nor gparted can see your HDD is bad news.SGD doesn't see it (or I'm using the wrong functions), but it does show up in gparted. That's why I haven't let go of all hope yet. Just most of it. ;)

As for those boot disks: There are so many to choose from! Would DOS 6.0 be sufficient? All I supposedly have to run is 'fdisk /mbr'.

---

### Post by cb951303 on 2008-05-20
correct me if I'm wrong but if you have windows and xubuntu on HDD and MBR is somehow gone and if you **can** boot to xubuntu, it should be enough to type ```
grub-install /dev/XXX
```
if you can't boot to xubuntu, use a live disk and chroot to your xubuntu system and then type the same command in console :)

---

### Post by nick_h on 2008-05-20
> I'd be happy to reinstall Gutsy just to get this to work. Is that feasible?

It would be easier to try the gutsy deb file or even download it and compile the source.  Here is a link - [http://packages.ubuntu.com/gutsy/ms-sys](http://packages.ubuntu.com/gutsy/ms-sys)

---

### Post by starvingartist on 2008-05-20
> **nick_h said:**
> It would be easier to try the gutsy deb file or even download it and compile the source.  Here is a link - [http://packages.ubuntu.com/gutsy/ms-sys](http://packages.ubuntu.com/gutsy/ms-sys)
hmmm... I'm a MS drone through and through. If it doesn't have a GUI I don't know what it does (and even then it is doubtful). I've just reinstalled Gutsy, which was something I could do by myself. :) Tried the ms-sys solution, but it didn't work: "unable to open /dev/sda, permission denied".

Guessing here, but could this be because it isn't mounted? How do I check? How do I mount?

---

### Post by nick_h on 2008-05-20
You can see what drives are mounted by typing:
```
mount
```
If you can mount the drive you should check that the XP system files are still there.

I don't think that you need the drive mounted to write the MBR though.  Have you tried with sudo?
```
sudo ms-sys -m /dev/sda
```

---

### Post by d-mart on 2008-05-20
I have a question when you use sgd with the commands sgd - english - windows -fixboot of windows - also might have to choose syslinux after this since thats what you installed grub with what exactly did it output just sgd failed or mbr corrupted? 

Also if you just want to verify windows is still a ok you should be able to boot from sgd using commands sgd - english - windows - boot windows does it just totally not recognize it or does it say an error.

but also as far as you asked earlier about mbrfix.exe this website explains how to use it from linux so if you can get to your windows partition from xubuntu since you said it still boots correct then you should be abled to follow this.

[http://users.bigpond.net.au/hermanzone/p18.htm#Restore_your_MBR_from_a_backup](http://users.bigpond.net.au/hermanzone/p18.htm#Restore_your_MBR_from_a_backup)

---

### Post by starvingartist on 2008-05-20
> **d-mart said:**
> I have a question when you use sgd with the commands sgd - english - windows -fixboot of windows - also might have to choose syslinux after this since thats what you installed grub with what exactly did it output just sgd failed or mbr corrupted? No, oddly enough it says that SGD has succeeded. 

> Also if you just want to verify windows is still a ok you should be able to boot from sgd using commands sgd - english - windows - boot windows does it just totally not recognize it or does it say an error.This just gives me the same output every time:
rootnoverify (hd0,0)
makeactive
chainload +1
boot
GRUB
... and then it stops completely.

> but also as far as you asked earlier about mbrfix.exe this website explains how to use it from linux so if you can get to your windows partition from xubuntu since you said it still boots correct then you should be abled to follow this.

[http://users.bigpond.net.au/hermanzone/p18.htm#Restore_your_MBR_from_a_backup](http://users.bigpond.net.au/hermanzone/p18.htm#Restore_your_MBR_from_a_backup)
I can still get into my Xubuntu USB drive, so I will give this a shot too.



nicedude has a lot of suggestions, and I've tried implementing them. The latest was using Trinity Rescue Disk, using 3 different approaches.

ms-sys:
it says "MBR succesfully written to /dev/sda", but the boot problem remains.

testdisk:
also claims success, but also doesn't solve the problem.

relocntfs:
at least it doesn't claim succes here: "Device does not appear to be a real NTFS volume". There was an option to force write. Should I try that, or will that hurt more than it helps?

---

### Post by nick_h on 2008-05-20
Did you manage to mount the drive to check that XP system files such as IO.SYS and ntldr are still there?

When you used ms-sys I assume it overwrote grub so you had evidence that it did something.

Does the output of fdisk look OK?
```
sudo fdisk -l
```

---

### Post by d-mart on 2008-05-20
hey what happens if you try to boot without the usb inserted.

---

### Post by adrian15 on 2008-05-27
> **d-mart said:**
> hey what happens if you try to boot without the usb inserted.

starvingartist finally decided to make this same question in the [Super Grub Disk forum: I messed up my MBR](http://www.supergrubdisk.org/forum/index.php?topic=75.0).

I am still waiting for him to try my suggested dd command.

adrian15

---

