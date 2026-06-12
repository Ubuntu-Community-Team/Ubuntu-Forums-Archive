---
title: "[SOLVED] CD/DVD Drive not responding"
date: 2008-11-25
forum: General Help
---

### Post by ZootHornRollo on 2008-11-25
Hi,

My CD/DVD RW is not longer working.

It is physically working in terms of there is power etc.  and i can insert discs.  But i cannot do anything with them - play, read, write....   nothing.

When i insert a disc the drive spins up and the drive light illuminates.  The drive can be heard spinning up and slowing down.

This happens with all discs be they CDs, DVD, Data, music, film etc.

I ran  ```
sudo lshw -C disk
``` with an audio cd in the drive.

here is the output :

```
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD A  DH20A4P
       vendor: ATAPI
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 9P59
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk
       description: ATA Disk
       product: WDC WD5000AACS-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WMASU0894599
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000be48b

```

Any hglp appreciated.

---

### Post by ZootHornRollo on 2008-11-25
i have now run ```
dmesg | grep CD
```

```
[   38.196674] scsi 0:0:0:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
[   38.720068] Uniform CD-ROM driver Revision: 3.20
[   38.720484] sr 0:0:0:0: Attached scsi CD-ROM sr0
```

---

### Post by ZootHornRollo on 2008-11-25
if i right click on the drive and select open i get 

```
no media in the drive
```

despite there being an audio cd in there

---

### Post by theozzlives on 2008-11-25
I have a WD Dual Layer CD/DVD +/- RW that won't read CDs anymore also, I had to make my CD-ROM the master in order to install 8.1. It won't write CD/DVDs either, I just figured it died with age.

---

### Post by cariboo on 2008-11-25
If the drive doesn't see a disk when it is inserted, it is more than likely a problem with the drive. Try another CDRom drive to see if the problem persists.

Jim

---

### Post by ZootHornRollo on 2008-11-25
ok,

thanks.  the drive is only around 6 months old but i'll see if i can find another one lying around and try that.

Cheers.

---

### Post by CatKiller on 2008-11-25
Have you tried cleaning it? You can get discs with small brushes on that will clean the lens, although if they've got to the point that they won't read discs at all, you can't use them. Compressed air is quite effective, but expensive. (Ten quid a can! Outrageous...) Condensation on the lens can cause temporary problems if the drive is very cold but the air is warmer and slighly damp. I used to work in a recording studio that got rather cold in the winter, and this used to happen to one of the cd burners. It goes away once the unit has warmed up.

Have you been inside the case at all recently, or jogged it? It is possible that a cable that is loose can cause drives to not function correctly, although it normally exhibits as a drive that randomly disappears.

Optical drives, like all hardware, can fail over time. For example, if the lens assembly has become misaligned or jammed in some way, then the drive would spin up OK, but since the optical data wasn't coming back, the drive would report that there's no disc. If that's the case, then it's probably repairable, but it might not be worth bothering since drives are really quite cheap.

---

### Post by theozzlives on 2008-11-25
> **ZootHornRollo said:**
> ok,

thanks.  the drive is only around 6 months old but i'll see if i can find another one lying around and try that.

Cheers.

If it's only 6 mos. old it's still under warranty from WD

---

### Post by ZootHornRollo on 2008-11-25
guys,

i tried it with the dell dvdrom that was originally in this machine and it works perfectly.  

so i guess i have a broken drive on my hands.

It will be under warrnty but i can't actually remember where i got it - somewhere online....  - but it wasn't expensive.  i'll hunt around the sites i buy kit from and see if they still have the order online.

thanks for your help folks....  appreciated.

---

### Post by theozzlives on 2008-11-25
go directly through Western Digital on there web site or call them, if you have a credit card they'll send an advance replacement and a box to send the defective one in.

---

### Post by denny577 on 2008-11-25
My drives don't work either.

If I put a disc in it, it buzzes, but nothing happens,

if I try to open it:

```
Cannot invoke CheckForMedia on HAL: org.freedesktop.DBus.Error.NoReply:
Did not receive a reply. Possible causes include:
the remote application did not send a reply, 
the message bus security policy blocked the reply, 
the reply timeout expired, 
or the network connection was broken.
```

If I put the disc in the drive before I have logged in, it sees that there is a disc in the drive, it sees that there is software on it, and it shows an icon, but if I try to open it, it just keeps loading...

And I can't eject them after trying to open it.

:P

Regards

---

### Post by ZootHornRollo on 2008-11-25
> **theozzlives said:**
> If it's only 6 mos. old it's still under warranty from WD

its not actually Western Digital - thats my HD - its a Lite On.

I got it from scan.co.uk and i've only heard good things about their service so far so i reckon it won't be a problem getting it replaced.

---

