---
title: "Wow, what is going on with my ubuntu!"
date: 2008-11-07
forum: General Help
---

### Post by heatmaka on 2008-11-07
its been a couple days now since, my computer froze on me, and when i did a reboot. it never would work. So i put my cd in, and i can only go on ubuntu threw the Cd. I can't install nothing!!!! it wont do it for me, and i cant do it manually, because there is not even one partition that shows up! It's a blank screen!! And when i try to do it automatically, it says "```
"no root file system is defined, please correct this from the partitioning menu"
```

And i have searched for hours, but i don't understand nothing!! What do i do? I'm thinking about giving up!

When i do a fdisk this is what shows up: ```
 ubuntu@ubuntu:~$ sudo fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
```

And when i try to enter sudo fdisk -l nothing shows up ?!?! LOL


PLEASE SOMEONE HELP  THANKS

---

### Post by joel@parke.ods.org on 2008-11-07
It is hard to know what is happening.  But it sounds that perhaps you have a hardware failure.  What happens if you attempt to install XP or Vista?  I realize you don't want to go that direction, but perhaps you need to have someone check your hardware first.

Sorry I can't be more help.  What does your bios tell you? Does it have a hard disk check?  Do you have a backup of your data? 

 - Joel

---

### Post by heatmaka on 2008-11-07
everything was working fine, and then i was trying to open a movie file, and BOOM! the screen stopped moving. I reboot, and this happens. But maybe i deleted the patitions my self, when i edited "sudo fdisk -l", because i was reading somewhere, that you delete all of them except one...and i tried that...and then the install still dint work...so i ran ubuntu with the cd, and deleted the last /dev/sda file that was in my fdisk.

I know it was a wrong move, but how can i fix this? 

thx for the quick reply

---

### Post by wirelessmonkey on 2008-11-07
> **heatmaka said:**
> everything was working fine, and then i was trying to open a movie file, and BOOM! the screen stopped moving. I reboot, and this happens. But maybe i deleted the patitions my self, when i edited "sudo fdisk -l", because i was reading somewhere, that you delete all of them except one...and i tried that...and then the install still dint work...so i ran ubuntu with the cd, and deleted the last /dev/sda file that was in my fdisk.

I know it was a wrong move, but how can i fix this? 

thx for the quick reply

If I read this right, your machine crashed, and you are now using the liveCD.

It sounds like you deleted the partitions on your hard drive...

Sadly it sounds like you will have to repartition and reinstall,
but first, do as suggested above, and try: fdisk -l
this will list existing partitions.

If I'm incorrect, please let me know, otherwise post the output of fdisk -l


Good Luck

---

### Post by heatmaka on 2008-11-07
> **wirelessmonkey said:**
> If I read this right, your machine crashed, and you are now using the liveCD.

It sounds like you deleted the partitions on your hard drive...

Sadly it sounds like you will have to repartition and reinstall,
but first, do as suggested above, and try: fdisk -l
this will list existing partitions.

If I'm incorrect, please let me know, otherwise post the output of fdisk -l


Good Luck

When i put fdisk -l, nothing shows up! I dont mind having to repartition and reinstall... just let me know how! thanks again for the quick help 

love it!

phil

---

### Post by heatmaka on 2008-11-07
im 99% sure that i did infact delete the partitions on my hard drive..

---

### Post by tangibleorange on 2008-11-07
well in that case you'll need to re-install :popcorn:!

---

### Post by heatmaka on 2008-11-07
> **tangibleorange said:**
> well in that case you'll need to re-install :popcorn:!

re-install what? I tried everything..can you please explain a bit more :)

thanks so much

phil

---

### Post by cdenley on 2008-11-07
If you run "fdisk -l" and nothing shows up, that means there are no drives detected. Even if you deleted your partitions, it would still show your empty disk(s). You must have a hardware problem.

---

### Post by PCessna on 2008-11-07
> **heatmaka said:**
> its been a couple days now since, my computer froze on me, and when i did a reboot. it never would work. So i put my cd in, and i can only go on ubuntu threw the Cd. I can't install nothing!!!! it wont do it for me, and i cant do it manually, because there is not even one partition that shows up! It's a blank screen!! And when i try to do it automatically, it says "```
"no root file system is defined, please correct this from the partitioning menu"
```

And i have searched for hours, but i don't understand nothing!! What do i do? I'm thinking about giving up!

When i do a fdisk this is what shows up: ```
 ubuntu@ubuntu:~$ sudo fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
```

And when i try to enter sudo fdisk -l nothing shows up ?!?! LOL


PLEASE SOMEONE HELP  THANKS

Seems like your hardware if failing, also, namely graphics. Others too, maybe overheating?

---

### Post by Yellow Pasque on 2008-11-07
It sounds like your hard disk went south for Winter (bad pun intended). See if your hard disk is still detected in the BIOS/system setup.

---

### Post by pcjunkie on 2008-11-07
First try to re-connect the cables on your pc and turn it on, if you can check the hard drive to see if it spins up. You should feel a slight vibration when spins up or hear it.

Check g-parted to see if anything works as hard drives.

If nothing shows I would assume the drive itself has failed. To recheck the drive system on the PC, try an older hard drive and see if it shows up.

If so that reconfirms it for you. 

Things that cause errors other than the drive burning out.
1. Power supply
2 PATA cable placement (BIOS system has fudged the cable - reposition on ribbon)
3 Power cable connection is faulty - replace with a known working connector.
4 System BIOS has a fault - resetting / updating can fix this

Try these first before you trash it and if you can see if it works on another pc or power supply.

If it has died there is a reason and its usually because it got cooked. Try getting a fan behind it to keep it cool. Once you go over 80gb drives work harder, longer and get hotter. More drives = double the heat.

---

### Post by Yellow Pasque on 2008-11-07
> Once you go over 80gb drives work harder, longer and get hotter.
Not true. (Or overly simplified at least)
The amount of power a drive draws is mainly going to depend on its rotation speed, number of platters, and process used on its core logic chips. With perpendicular recording technology, die-shrunk logic chips and increases in areal density, large modern drives are doing much better with power consumption. See silentpcreview.com for measurements on hard disk power draw.

---

### Post by mdurham on 2008-11-07
> **Temüjin said:**
> It sounds like your hard disk went south for Winter (bad pun intended).

Where is the pun?

---

### Post by Yellow Pasque on 2008-11-07
In the U.S. (or at least my part of it), when something goes bad, it is also said to have "gone south" (i.e. down). Also, we are approaching winter (at least in the Northern Hemisphere).

---

### Post by heatmaka on 2008-11-08
I try to put g-parted in terminal and nothing works. I don't really hear any sounds...but my bois said a couple things..

```
Error 2100: HDDO (Hard disk drive) initialization error (1)
```

What does that mean, and how do i fix this?!?!

And why can i still run ubuntu with the CD?

---

### Post by alexcckll on 2008-11-08
Do you hear a clicking sound when you switch the machine on?  Could your HDD have suffered a head crash?

---

### Post by heatmaka on 2008-11-08
no clicking noise. I'm on the computer right now!! running with the cd. hats going on?!?! please someone find me an answer or im going back to ******* windows! lol :(

---

### Post by cdenley on 2008-11-08
> **heatmaka said:**
> no clicking noise. I'm on the computer right now!! running with the cd. hats going on?!?! please someone find me an answer or im going back to ******* windows! lol :(

Replace your hard drive! You won't have any more luck with windows. YOU HAVE A HARDWARE PROBLEM. If your BIOS says it can't initialize the hard drive, what makes you think switching to windows will help?

---

