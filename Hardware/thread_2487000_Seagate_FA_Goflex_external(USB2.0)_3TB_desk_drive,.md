---
title: "Seagate FA Goflex external(USB2.0) 3TB desk drive, spinning but not recognized"
date: 2023-05-19
forum: Hardware
---

### Post by emonti on 2023-05-19
This is a SATA, 7200 drive. 

I have three machines, running variously: Ubuntu 16.04, 20.04 LTS, Win7/10.


_**Background:**_
    - drive was reformatted from NTFS to MBR, as a single, 3000Gb partition for ubuntu. I used it for several years. 
Occasionally it would go into an unpredictable sleep/wake state but I always managed to wake it up by shutting down or reconnecting the drive. ;
    - then one day, the drive stopped working I suspect it was after I performed a 'umount -a'. I have never managed to get it to work again(except for once, very briefly... see below). There is about 1Tb of data on the drive. ;
    - the drive was not responding but for a single flicker of a power light on the dock. Not spinning up. ;
    - the last time I reached out for some help on this forum is here: [https://ubuntuforums.org/showthread.php?t=2460082](https://ubuntuforums.org/showthread.php?t=2460082) . I have since acquired new computers with which to test/revive the device. ;
    - I had just about given up on it, until the other day. I thought I'd give it one last attempt to get it to come back as a working drive... so...
        - the other day(2 yrs later) I decided to try a different power-lead, at a phone shop, the drive was recognized instantly, using a newer laptop(running 20.04LTS), but the assistant performed a non-graceful dismount(he was quite eager to make a power-cable sale, bless him) and the drive has not been recognized by my laptop/s since then :(. It may have nothing to do with the non-graceful dismount/power-down but I suspect the drive is too sensitive for such rough handling. ;
    - I have swapped out a power lead, using one I scrounged from my scraps at home. (The old one says 'fully regulated' the new(spare) one doesn't., although both have the same spec 12v to 2amp. ***Question:*** What does 'fully regulated' mean in this context?).


_**Current state of the drive**_, now, is: spinning but not recognized:
    - lights come on for 10-15 seconds on wall-power-connect (occasionally I will notice the power light will come back on and flash constantly. On further observation, it appears to take approximately an hour before it starts to flash... and the drive makes a slight noise as it transitions into a slightly different state, although the spinning/humming continues unabated. ) ;
    - the drive spins, non-stop, from power-connect to power-disconnect, connecting/disconnecting the data cable to the laptop/drive has no apparent effect whatsoever. Edit: except when it is flashing and I disconnect the data cable from the usb port on the laptop, it stops flashing straight away. Connect it again and the light doesn't come back on. ;
    - OS (ubuntu 20.04 LTS) doesn't recognize the drive on connecting usb cable from dock to laptop, same for Debian and Windows7. ;
    - I did manage to take a copy of the syslog(generated while at the shop), before the logs could get recycled. So I can see that/how the drive was recognized when it worked in the shop. This would be very useful for subsequent problems i.e. once the drive is recognized, but I'm not sure how useful until then. Perhaps it is possible to somehow force/probe the drive using the same configuration (laptop:usb port). ***Question:*** Does someone know? (I have the syslogs for when the drive was recognized on ubuntu 20.04 about a week ago).


_**I have tried**_ the usual basic troubleshooting steps:
    - different usb port ;
    - different laptop ;
    - different OS (win7) on one of the laptops, debian on the other ;
    - different order of cable connectivity ; 
    - lsusb, fdisk -l, ls /dev/* | wc -l : show the drive is not recognized ;
    - different wall socket (in shop and at home) ;
    - 3rd (Windows10) laptop ;


_**Still to try:**_
    - another power lead, preferably 'fully regulated', and without intermediate national adaptors ;
    - removing seagate ext cover... and connecting as a regular pc drive :
        - if the Seagte FA goflex 3TB dock is emulating a 64-bit addressable partition-size, ***(Question:*** would this be an option? My understanding was that in order to create a single partition on the drive, a 64-bit address capacity was needed, which when the drive originally hit the market, there was no OS-level support for the LBA address capacity... hence the dock itself was enabled to take care of that.*** Question: ***If I remove the dock from the equation, will ubuntu be able to make sense of the 3TB partition? ;


Any feedback/ideas would be appreciated.

p.s. I know this is old HW, and that my hopes are a little high, but it did come to life, the other day after not touching it for about 2 years, albeit briefly. You'll have to forgive me for not giving up so easily.

---

### Post by oldfred on 2023-05-19
If it is USB2, it will be very slow.
It will plug into a USB3 port and be a bit faster. I used USB3 flash drives in USB2 ports and they were a bit faster.

You cannot use MBR with drives over 2TB. Some early versions may have used some proprietary partitioning scheme as a work around for the MBR 2TB limit. Generally large drives use gpt. 
If a proprietary partition scheme you may need software on drive or your system for it to work?

---

### Post by emonti on 2023-05-19
> [COLOR=#000000]If it is USB2, it will be very slow.[/COLOR]
[COLOR=#000000]It will plug into a USB3 port and be a bit faster. I used USB3 flash drives in USB2 ports and they were a bit faster.[/COLOR]

Yes, I don't really mind about the speed. I'd be very happy just to get it recognized at this point. 

Having said that, the new laptop will have the latest usb ports so I'm guessing 3.0.

> [COLOR=#000000]You cannot use MBR with drives over 2TB. Some early versions may have used some proprietary partitioning scheme as a work around for the MBR 2TB limit. Generally large drives use gpt.[/COLOR]
[COLOR=#000000]If a proprietary partition scheme you may need software on drive or your system for it to work?[/COLOR]

Agree with everything you say, although for the Seagate utilities to work, afaik, you first need for the drive to be recognized.

The only reason I asked about that is if I get around to removing the enclosure of the drive and attempt to get it to work in a pc.

---

### Post by oldfred on 2023-05-19
If you have Seagate software for the drive, that only will work in Windows. I do not think they have a driver for Linux.

---

### Post by aljames2 on 2023-05-19
If you have your data backed up on other devices, then may I ask what is there to gain reviving this old spinner?  HDDs are rather inexpensive these days. I would not trust it for anything but a paperweight at this point.  If your data lives on it & no other backup then carefully press on.  Does GParted see the drive?

When you buy your next HDD(s), maybe consider avoiding the 3TBs. I’ve read the failure rates are somewhat higher on the 3TBs vs 2, 4, or 8TB.  May be worth reading up on this.  I am waiting for a good sale to get a couple WD Black 8TBs.

---

### Post by emonti on 2023-05-20
They do have a version of the utilities for ubuntu 20.04, but all the commands seem to need an input which is the device which shows up in /dev.

---

### Post by emonti on 2023-05-20
In hindsight, I should have bought two 1TB drives, instead.

3TB turned out to be a bit of a waste because if you're going to keep that much data, it makes sense to scale in parallel if you know what I mean. To back up 3TB you need another 3TB drive.

I have just under 1TB of data on the drive, but I'd still like access to the files, so no I'm not quite ready to convert it into a door stop.

---

### Post by emonti on 2023-05-20
Interesting development...

I have an old partition on one of my laptops that is - I think - ubuntu 12. Now booting it up with the spinner connected, I see a generic usb drive showing up.... on /dev/sdb.

I'll see if I can't use it to perform a mount, using the syslogs I mentioned in the opening post.

I also saw something in the logs which said waiting for device to settle... words to that effect. It's on a different partition, so that's why this is a little bit vague. Perhaps part of the problem has to do with timing i.e. probing the usb port before the drive has completely spun up.

 I'll have a look and report back.

---

### Post by emonti on 2023-05-20
So, it seems I cannot mount /dev/sdb on the old partition.... it says 'no media'.

There may yet be something to the timing of usb-port probing. So far no joy.

---

### Post by oldfred on 2023-05-20
Is this what you have?
[https://www.seagate.com/support/downloads/beyond-2tb/](https://www.seagate.com/support/downloads/beyond-2tb/)

---

### Post by emonti on 2023-05-21
Yes, OldFred, they are talking about the 32-bit address limit on an MBR partition. 

Here is a contemporary review of the actual drive....

[https://www.anandtech.com/show/3858/the-worlds-first-3tb-hdd-seagate-goflex-desk-3tb-review/2](https://www.anandtech.com/show/3858/the-worlds-first-3tb-hdd-seagate-goflex-desk-3tb-review/2)

This article (part2 specifically) describes the work around - in the form of dock-level sector-size emulation(so that it(an effective-4kb sector partition) resembles a 512byte sector partition to the OS/firmware/device controller) - to lack of GPT support from OS and firmware, back in 2010. That 's my understanding, anyway. (see here for more: [https://www.anandtech.com/show/2888](https://www.anandtech.com/show/2888))

What I perhaps should have done is simply used multiple smaller partitions, e.g. 3x 1TB partitions, under MBR.

I'd still like to know if removing the enclosure and inserting it as an internal drive to a pc, would pose a threat/risk to the written data on the drive. It might try to write to an incorrectly addressed sector. That might depend on how the pc will interpret the data signal from the drive, given there is no dock to emulate a 4kb sector as a 512b sector. Has the partition been written to any differently? Is the difference all in the emulation performed by the dock? (Maybe making sure to mount it as read-only would at least enable me to get the data off). 

p.s. If it is the case that modern hardware/firmware/software can easily read the 64-bit address partition, without the dock, then it is a potential solution i.e. to remove it from its enclosure and stick it in a pc.

---

### Post by oldfred on 2023-05-21
The use of 512 for 4K sectors is standard.
From my fdisk:
[FONT=monospace][COLOR=#000000]Sector size (logical/physical): 512 bytes / 4096 bytes

But MBR has the hard limit of 2TB no matter how many partitions you add.
The proprietary driver for your Seagate does a work around.

Link also says you cannot use gpt with BIOS, but I did back in 2010 with my BIOS only system. You still boot to gpt's protective MBR and have to have a bios_grub partition for grub code normally just after MBR. Space after MBR does not exist with gpt. Gpt has protective MBR, just to have one entry in MBR table that says drive is gpt, so old MBR formatting tools do not see drive as empty and then damage partitions trying to format in MBR. 
[/COLOR]
[/FONT]

---

### Post by emonti on 2023-05-22
> **oldfred said:**
> The use of 512 for 4K sectors is standard.
From my fdisk:
[FONT=monospace][COLOR=#000000]Sector size (logical/physical): 512 bytes / 4096 bytes

But MBR has the hard limit of 2TB no matter how many partitions you add.
[/COLOR]
[/FONT]

Okay. If you say so. I didn't know that. When I read the statement from the Anand review: '[COLOR=#444444][FONT=Arimo]Now LBAs under MBR partitions are addressed using 32-bit values', 

[/FONT][/COLOR]I just assumed the 32bit value was per partition, but okay. 

> **oldfred said:**
> 
[FONT=monospace][COLOR=#000000]
The proprietary driver for your Seagate does a work around.

Link also says you cannot use gpt with BIOS, but I did back in 2010 with my BIOS only system. You still boot to gpt's protective MBR and have to have a bios_grub partition for grub code normally just after MBR. Space after MBR does not exist with gpt. Gpt has protective MBR, just to have one entry in MBR table that says drive is gpt, so old MBR formatting tools do not see drive as empty and then damage partitions trying to format in MBR.
[/COLOR]
[/FONT]

Okay, well I guess that's useful info' but for me right now, the drive was formatted using MBR, in 2010, and was written to .... if I recall, to the tune of just under 1TB. 

So, what do you think would happen if I removed the enclosure and tried to use it as an internal drive from an ubuntu usbboot flash drive? Is there is risk it would write to the drive before I explicitly do so, myself?

In other words I would be removing the emulation layer that exists in the form of the dock.

---

### Post by oldfred on 2023-05-22
First issue will be whether BIOS sees drive or sees it correctly. BIOS cannot run the Seagate software.

I would not expect drive to be written into, unless you force issue.
Clicking on it in a file browser will try to mount it, if it is seen. But often will not mount as default is read/write and if not fully seen then just does not mount. Sometimes then a manual mount read only works.

Or lower level tools like testdisk or photorec, if BIOS has seen drive. But you should be able to run those when connected by USB if seen.

---

