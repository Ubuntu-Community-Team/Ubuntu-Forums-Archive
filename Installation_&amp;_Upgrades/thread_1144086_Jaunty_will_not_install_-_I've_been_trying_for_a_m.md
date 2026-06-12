---
title: "Jaunty will not install - I've been trying for a month!"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-04-30
I have tried to install dozens of times (and I posted a prior question in the closed Jaunty testing section). A month ago I also filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/351750](https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/351750)

The install fails at the same point every time. When I switch to the Alt-F4 terminal, here is what I see:

```
Apr 30 16:39:13 preseed: 
Apr 30 16:39:13 in-target: Reading package lists...
Apr 30 16:39:13 in-target: 
Apr 30 16:39:13 in-target: Building dependency tree...
Apr 30 16:39:13 in-target: 
Apr 30 16:39:13 in-target: Recommended packages:
Apr 30 16:39:13 in-target:   pciutils
Apr 30 16:39:13 in-target: The following NEW packages will be installed:
Apr 30 16:39:13 in-target:   installation-report
Apr 30 16:40:33 in-target: 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Apr 30 16:40:33 in-target: Need to get 0B/17.8kB of archives.
Apr 30 16:40:33 in-target: After this operation, 111kB of additional disk space will be used.
Apr 30 16:40:33 in-target: Media change: please insert the disc labeled
Apr 30 16:40:33 in-target:  'Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)'
Apr 30 16:40:33 in-target: in the drive '/cdrom/' and press enter
```

It looks to me like the installer gets confused as soon as it switches to in-target.

It is not possible to navigate in the installer once this error happens. The installer presents two choices: go back or continue. **Neither choice will move away from the screen showing the error.**


 The only way I have found to get out of the installer is to reboot.

I can open another terminal (Alt-F2) and cd to, and ls the cdrom, so it is there and it can be read from.

I'm using the alternate installer amd64 on a computer that is currently running Hardy. I'm installing _**fresh**_ to a different partition (one that used to hold Windows).

I checked the CD. It has no defects.

I would like to get Jaunty installed after trying for one month!!!

---

### Post by MountainX on 2009-05-01
bump

---

### Post by MountainX on 2009-05-09
still can't get it to install...

---

### Post by yogo on 2009-05-09
Why don't you try installing it from a USB drive?

---

### Post by MountainX on 2009-05-09
> **yogo said:**
> Why don't you try installing it from a USB drive?

I thought about that... then I read some stuff here on the forums and a USB install sounds more problematic than the usual CD install. But maybe you are right. I could give that a try, especially since there are no other suggestions. Thanks.

---

### Post by Topsiho on 2009-05-09
You could try to install from the alternate CD. That one has another installer, so maybe that should work.

Anoyher point might be to make sure that you use the right CD, for your platform. Ubuntu runs on a number of platforms, so if you use a PC (on which Windows would run :( , make sure you use the i386 version...

Topsiho

---

### Post by Dr.Vista on 2009-05-09
I don't know if this was the same problem but when I first installed Jaunty it keep stopping at 75% and it wouldn't go on because it said that my cd was not working correctly. After that I burned the disk image again to see if that occurred again but it still would so what I did was install Hardy Heron and then I upgraded to Jaunty.

---

### Post by MountainX on 2009-05-09
> **Dr.Vista said:**
> I don't know if this was the same problem but when I first installed Jaunty it keep stopping at 75% and it wouldn't go on because it said that my cd was not working correctly. After that I burned the disk image again to see if that occurred again but it still would so what I did was install Hardy Heron and then I upgraded to Jaunty.

This sounds similar to my issue. Maybe I will try that too. Or maybe an upgrade from 8.10 to 9.04. I have CDs burned for both of those releases already, so I could do that easier than I could try the USB install.

---

### Post by MountainX on 2009-05-09
> **Topsiho said:**
> You could try to install from the alternate CD. That one has another installer, so maybe that should work.

Anoyher point might be to make sure that you use the right CD, for your platform. Ubuntu runs on a number of platforms, so if you use a PC (on which Windows would run :( , make sure you use the i386 version...

Topsiho

Actually, I ***always*** use the alternate installer. That's the one I'm using now.

My computer has a dual core AMD64 processor, so I can install either i386 or AMD64. I have tried both, but the one I really want to install is AMD64 (now that the Flash player issues seem to be resolved).

---

### Post by Topsiho on 2009-05-09
If you **always** use the alternate CD's, then I should reverse my advice: try the Live CD :) . It has a different installer, so if one installer quits, the other installer may run as it should. It's how I installed some previous versions of Ubuntu on one of my boxes (Live CD -> Alternate direction). Using the Live CD you can see whether Jaunty runs well on your computer before you try to install it. But if I'm not wrong the alternate CD gives you more options. If you need those.

How about memory? Installing from the Live CD you need to have more than 384 MiB of RAM, more is better of course.
How about hard disk space? If you have not enough (what is enough? 4 or 5 GiB maybe?) then of course the install will halt some time.

And always check your CD for errors on the box on which you install, it's one of the options you get. Checking the memory for some hours (all night?) on end is an option too.

I run the 64-bit version of 8.04.1 LTS on my AMD64 Athlon processor on this box, and have no problem at all with Flash (non free plug in).

One thing more: there is more under the moon than Jaunty or even Ubuntu. You could try other distro's. See Distrowatch for inspiration.

Success,

Topsiho

---

### Post by peakshysteria on 2009-05-09
Why not: [**Network Upgrade for Ubuntu Desktops (Recommended)**]("http://www.ubuntu.com/getubuntu/upgrading")

Works like a charm in my end....

---

### Post by MountainX on 2009-05-09
> **Topsiho said:**
> If you **always** use the alternate CD's, then I should reverse my advice: try the Live CD :) . It has a different installer, so if one installer quits, the other installer may run as it should. It's how I installed some previous versions of Ubuntu on one of my boxes (Live CD -> Alternate direction). Using the Live CD you can see whether Jaunty runs well on your computer before you try to install it. But if I'm not wrong the alternate CD gives you more options. If you need those.

How about memory? Installing from the Live CD you need to have more than 384 MiB of RAM, more is better of course.
How about hard disk space? If you have not enough (what is enough? 4 or 5 GiB maybe?) then of course the install will halt some time.

And always check your CD for errors on the box on which you install, it's one of the options you get. Checking the memory for some hours (all night?) on end is an option too.

I run the 64-bit version of 8.04.1 LTS on my AMD64 Athlon processor on this box, and have no problem at all with Flash (non free plug in).

One thing more: there is more under the moon than Jaunty or even Ubuntu. You could try other distro's. See Distrowatch for inspiration.

Success,

Topsiho

I have to do manual partitioning, and I also use LVM and crypto, so I am not sure I can use the Live CD. I will look into it.

My computer has 4GB of RAM, so no problem. The partition I'm installing to is 30GB, so no problem there either.

The CD has been checked for errors. In fact, I have burned a half dozen CD's and none have disk errors yet all give the exact same install error at the exact same point (when switching to in-target).

The installer error indicates that this is not a RAM problem -- it is a file system problem related to the installer switching (chroot, I presume) to target.

I am running Ubuntu on about 6 computers, so I do not want to switch this one to another distro. I want to keep everything the same so I can manage it easily. Six computers in one house is already a lot to manage!

Actually, I think my best bet is to install 8.10 from the Alternate CD, then install 9.04 from CD or network, as Dr.Vista suggested. That's my plan...

---

### Post by MountainX on 2009-05-09
> **peakshysteria said:**
> Why not: [**Network Upgrade for Ubuntu Desktops (Recommended)**]("http://www.ubuntu.com/getubuntu/upgrading")

Works like a charm in my end....

I'm doing a new (clean) install.

---

### Post by Topsiho on 2009-05-09
The OP wants to install Jaunty fresh alongside of Hardy. So upgrading via a net install is not an option here. From Hardy it should be done twice: first to Ibex and then to Jaunty...
It would take less than a month though:P (if all goes well).

I have one other thought (which is not much, I know): you (the OP) said that you want to install in a partition in which you had Windows. Maybe you should make it free space first, and in it create the necessary partitions (I use /, /home and a swap partition). And there comes another thought: you can not have more than 4 primary partitions on one hard disk, so if necessary you should create some logical partitions (which come into an extended partition, which is itself a primary partition). So: three or less primary partitions, and the rest all logical ones.

Topsiho

---

### Post by backspace on 2009-05-09
> **MountainX said:**
> I have tried to install dozens of times (and I posted a prior question in the closed Jaunty testing section). A month ago I also filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/351750](https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/351750)

The install fails at the same point every time. When I switch to the Alt-F4 terminal, here is what I see:

```
Apr 30 16:39:13 preseed: 
Apr 30 16:39:13 in-target: Reading package lists...
Apr 30 16:39:13 in-target: 
Apr 30 16:39:13 in-target: Building dependency tree...
Apr 30 16:39:13 in-target: 
Apr 30 16:39:13 in-target: Recommended packages:
Apr 30 16:39:13 in-target:   pciutils
Apr 30 16:39:13 in-target: The following NEW packages will be installed:
Apr 30 16:39:13 in-target:   installation-report
Apr 30 16:40:33 in-target: 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Apr 30 16:40:33 in-target: Need to get 0B/17.8kB of archives.
Apr 30 16:40:33 in-target: After this operation, 111kB of additional disk space will be used.
Apr 30 16:40:33 in-target: Media change: please insert the disc labeled
Apr 30 16:40:33 in-target:  'Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)'
Apr 30 16:40:33 in-target: in the drive '/cdrom/' and press enter
```

It looks to me like the installer gets confused as soon as it switches to in-target.

It is not possible to navigate in the installer once this error happens. The installer presents two choices: go back or continue. **Neither choice will move away from the screen showing the error.**


 The only way I have found to get out of the installer is to reboot.

I can open another terminal (Alt-F2) and cd to, and ls the cdrom, so it is there and it can be read from.

I'm using the alternate installer amd64 on a computer that is currently running Hardy. I'm installing _**fresh**_ to a different partition (one that used to hold Windows).

I checked the CD. It has no defects.

I would like to get Jaunty installed after trying for one month!!!
I had similar install problem with 8.10 . . . just screen full of code.

Checked out my BIOS config and noticed CDROM drive was "secondary master" and my Ubuntu disk was "secondary slave".

Once I switched the jumpers and made the CDROM drive "secondary slave" and the hard disk "secondary master", the install went without error.

My "primary master" on the first IDE was my XP HD and "primary slave" on the first IDE was a spare 84 GB storage.

It's worth a check.

---

### Post by MountainX on 2009-05-10
Here is where I stand so far.
1. The 8.10 alternate CD gives almost the exact same error. The message is slightly different but the installation fails just after the installer switches to in-target.

2. I made a USB installer. Unfortunately, I found out that the Live CD does not support LVM or crypto, so I cannot install from either the Live CD or the USB stick. (Unless there is a way to make an Alternate installer on USB.)

So, what next?

(BTW, my HDD is first SATA master. My CD is on IDE as primary IDE master. There are no other disks, and I did install Gutsy with these BIOS settings.)

---

### Post by MountainX on 2009-05-10
> **Topsiho said:**
>  Maybe you should make it free space first, and in it create the necessary partitions (I use /, /home and a swap partition). 
Topsiho

I did this. I have exactly 4 partitions and I'm trying to install into the first one. It is empty and the installer gets paste creating the LVM and crypto on the partition without problems. The grub boot partition is the 2nd one. Hardy is on the 3rd partition and the 4th is just data.

---

### Post by MountainX on 2009-05-11
Success! :)
I made a USB installer with the Alternate CD image and it worked.

Thanks for all the suggestions here.

EDIT: unfortunately, the existing Hardy installation will no longer boot. However, I think I can probably fix that with a little help. I'll make a new post.

---

### Post by orange-wedge on 2009-05-11
BTW:  You can install packages within the Live CD... such as LVM.  That's how you can setup LVM from the Live CD, and from there you can use gparted to setup up your partitions.

I really do not understand why LVM does not come standard with the Ubuntu installation disks.

---

### Post by sloggerkhan on 2009-05-11
> **MountainX said:**
> Success! :)
I made a USB installer with the Alternate CD image and it worked.

Thanks for all the suggestions here.

EDIT: unfortunately, the existing Hardy installation will no longer boot. However, I think I can probably fix that with a little help. I'll make a new post.

Unless you mis-partitioned your new install, it's just a grub issue. Should be a quick fix.

Speaking of which, I usually never upgrade to the next ubuntu version, instead doing a clean install, but I did this time and the 8.10 to 9.04 upgrade went great.

Likewise, I find that using a USB key is faster and easier than CD booting these days thanks to unetbootin, which I think is in the repos.

---

### Post by MountainX on 2009-05-11
> **sloggerkhan said:**
> Unless you mis-partitioned your new install, it's just a grub issue. Should be a quick fix.

Speaking of which, I usually never upgrade to the next ubuntu version, instead doing a clean install, but I did this time and the 8.10 to 9.04 upgrade went great.

Likewise, I find that using a USB key is faster and easier than CD booting these days thanks to unetbootin, which I think is in the repos.

Thanks. I think this is just a grub issue. I will look into it and then post my questions.

---

### Post by MountainX on 2009-05-11
Here's my thread explaining that Hardy will no longer boot after I installed Jaunty:
[http://ubuntuforums.org/showthread.php?p=7258911#post7258911](http://ubuntuforums.org/showthread.php?p=7258911#post7258911)

I tried the most obvious grub fix, but it did not resolve the problem.

---

### Post by 720iD on 2009-05-28
i have this exact same problem. i am installing 9.04 server. i get to a point in the install and i am asked to insert the disc 'ubuntu-server 9.04....'
i cannot continue and i cannot go back, i cannot open my cd drive. it seems to be disconnected. 

i dont know what to do, what do i do? 

:confused:

---

### Post by MountainX on 2009-05-28
> **720iD said:**
> i have this exact same problem. i am installing 9.04 server. i get to a point in the install and i am asked to insert the disc 'ubuntu-server 9.04....'
i cannot continue and i cannot go back, i cannot open my cd drive. it seems to be disconnected. 

i dont know what to do, what do i do? 

:confused:

In my experience the CD drive is not disconnected. Using Alt-Fn to open a terminal will probably show that you can cd to the CD-Drive and browse the files on it. That's how it is with me.

I never resolved the problem with the CD installer. The way I finally got it installed was by installing Jaunty from a USB flash drive. To do that, boot from the Live CD, use it to make a USB installer, and then install from USB.

---

### Post by 720iD on 2009-05-28
> **MountainX said:**
> In my experience the CD drive is not disconnected. Using Alt-Fn to open a terminal will probably show that you can cd to the CD-Drive and browse the files on it. That's how it is with me.

I never resolved the problem with the CD installer. The way I finally got it installed was by installing Jaunty from a USB flash drive. To do that, boot from the Live CD, use it to make a USB installer, and then install from USB.

is it possible to do this with ubuntu-server edition? i dont think it runs live ??? 

if i could get an image file of the server edition i might be able to do it. 

it is strange that i can install 9.04jaunty desktop from the installer, no problems. just cannot get the server edition  past this point. odd!

---

### Post by MountainX on 2009-05-28
> **720iD said:**
> is it possible to do this with ubuntu-server edition? i dont think it runs live ??? 

if i could get an image file of the server edition i might be able to do it. 

it is strange that i can install 9.04jaunty desktop from the installer, no problems. just cannot get the server edition  past this point. odd!

My problem was with the alternate CD, which has an installer just like the server edition. So we are probably seeing the same thing. I made an alternate installer on USB, so I bet you can do that with the server edition too.

---

### Post by 720iD on 2009-05-29
i am wondering about installing 8.04 instead. i remember you saying this was an change of verison for you. did you have 8.04 installed on your machine prior to the version change. any problems with this?

---

### Post by MountainX on 2009-05-29
> **720iD said:**
> i am wondering about installing 8.04 instead. i remember you saying this was an change of verison for you. did you have 8.04 installed on your machine prior to the version change. any problems with this?

I was doing a clean install. I actually got the exact same install error with both 8.10 and 9.04. I did not try 8.04.

---

