---
title: "Can't Boot Ubuntu From my USB"
date: 2012-01-21
forum: Hardware
---

### Post by TheMidnightWings on 2012-01-21
Hello everyone, I was wondering if anyone on here could help me with this. I ran Ubuntu on my old laptop for quite a while, no problems. Recently I purchased a new laptop. A Gateway Model laptop NV55C. Now I downloaded the 64bit AMD iso, and burned it to my USB stick for installation, like I normally would. However, when I am a the start menu, I cant acsess the boot menu to boot off the USB. I've tried mashing F12, F8, ESC, and CTRL. None of them work, the only indication of a boot menu is in the bios, but that's just the boot order. Does anyone else who has this model laptop know how to boot off the USB? Please help! I'm so confused...:confused:

---

### Post by carl4926 on 2012-01-21
Try F1 or  F2

---

### Post by TheMidnightWings on 2012-01-21
> **carl4926 said:**
> Try F1 or  F2

F2 opened the bios, F1 did nothing. Anymore ideas? :confused:

---

### Post by carl4926 on 2012-01-21
So check the BIOS settings for USB booting

On my eeepc I have to hit Esc at the bios screen to get the boot device options

---

### Post by TheMidnightWings on 2012-01-21
> **carl4926 said:**
> So check the BIOS settings for USB booting

On my eeepc I have to hit Esc at the bios screen to get the boot device options

Alright, I went into the BIO's and edited the settings to allow booting off of USB's (why it was disabled is beyond me.) Regardless. I booted into Ubuntu 11.10, and played around for a few minutes to make sure everything was going to perform and behave properly. BUT, when I went for the install, the usual "Install alongside Windows 7" wasn't their. It just simply said "Replace Windows 7" which I DON'T want to do, or it said something else. Which took me to some ungodly partition editor that I have no idea how to work. What do I do now?! :mad:

---

### Post by carl4926 on 2012-01-21
Boot the Ubuntu USB and open a terminal
Post the result of

```
sudo fdisk -l
```

---

### Post by varunendra on 2012-01-21
> **TheMidnightWings said:**
> .. BUT, when I went for the install, the usual "Install alongside Windows 7" wasn't their. It just simply said "Replace Windows 7" which I DON'T want to do
If it has Win7 (OEM) preinstalled, then most probably its drive has _already four primary partitions in use_ (boot + Windows + OEM tools + Recovery). If so, you must delete ONE partition (and resize others) to create room for an extended one in which you can create root+swap partitions for Ubuntu.
[COLOR=Red][B]
BE CAUTIOUS! [/B][/COLOR]Whether or not above is the case, you should seriously consider creating backup DVDs (or iso files on an external media) of your windows installation before trying anything that may corrupt windows or partitions!

Please open the disk management tool in Windows and tell us how many partitions it shows and what their names are. We can easily take it from there.

---

### Post by kleeh777 on 2012-01-21
Yeah u need Parted Magic. Its a live tool for partitioning you disks. You have to prepare an ext4 partiton for your Ubuntu. And maybe an nfts for storage which can be reached by both Win7 and Ubuntu And if u dont know what u are doing dont bother about a boot partition. One will do it.

---

### Post by varunendra on 2012-01-21
> **kleeh777 said:**
> Yeah u need Parted Magic..
Nope!

Don't ever do this yourself or recommend others to do so IF it is a Win7 (or its boot) partition you are going to resize.

While tools like Parted Magic or Gparted most often do it safely, there is always a fair chance of ending up with a screwed windows if you used such tools to resize/manipulate win7 partitions.

The recommended method is:

[LIST=1]
[*]Defragment the partitions from within windows,
[*]use windows' own disk management tool for resizing partitions to obtain free space,
[*]Then boot with live cd and use gparted (which is already on the ubuntu live cd) to create an extended partition in the empty space obtained in step 2 above
[*]Create logical partitions in the extended partition - as many as you wish - including one ext3 or ext4 for Ubuntu (20+GB) and one swap (2GB or equal to the amount of RAM).
[/LIST]


@TheMidnightWings,


If you are doubtful, it is best to post the windows' disk management info I asked for in my previous post. Depending on that info and your requirements, we can suggest the best options for you.

---

### Post by TheMidnightWings on 2012-01-22
> **varunendra said:**
> Nope!

Don't ever do this yourself or recommend others to do so IF it is a Win7 (or its boot) partition you are going to resize.

While tools like Parted Magic or Gparted most often do it safely, there is always a fair chance of ending up with a screwed windows if you used such tools to resize/manipulate win7 partitions.

The recommended method is:

[LIST=1]
[*]Defragment the partitions from within windows,
[*]use windows' own disk management tool for resizing partitions to obtain free space,
[*]Then boot with live cd and use gparted (which is already on the ubuntu live cd) to create an extended partition in the empty space obtained in step 2 above
[*]Create logical partitions in the extended partition - as many as you wish - including one ext3 or ext4 for Ubuntu (20+GB) and one swap (2GB or equal to the amount of RAM).
[/LIST]


@TheMidnightWings,


If you are doubtful, it is best to post the windows' disk management info I asked for in my previous post. Depending on that info and your requirements, we can suggest the best options for you.
Thank you, I was able to figure it out on my own. Thanks for all of you for the ideas and the bios tips!! :)

---

