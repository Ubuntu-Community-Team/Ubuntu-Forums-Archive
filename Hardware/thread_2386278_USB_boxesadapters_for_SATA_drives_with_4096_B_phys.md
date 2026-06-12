---
title: "USB boxes/adapters for SATA drives with 4096 B physical sectors"
date: 2018-03-03
forum: Hardware
---

### Post by sudodus on 2018-03-03
Recently I bought a **new 120 GB SSD drive**, and I encountered a new problem, that I have not encountered before with older SSD drives of the same size.

I tried to install Lubuntu 16.04.4 LTS during the iso-testing into the SSD drive, when it was connected via an **adapter with the brand name Deltaco**. I tried again with Lubuntu Bionic (to be released as 18.04 LTS) hoping that the problem should be solved with the newer kernel and its drivers. The partitioner of the installer **ubiquity** of both versions failed. See the attached screenshot. (Following the advice did not work, I arrived at the same error message.)

It was possible to use **gparted** in the same live systems and pre-partition the drive and then install Lubuntu via 'Something else' at the partitioning window.

[B]I noticed that the new SSD drive has 4096 B physical sectors, while the old ones have 512 B physical sectors.
[/B]
```

Created by gparted in Bionic
---
The partitioner in ubiquity failed in this (new) drive in
16.04.4 and 17.10 and 18.04 (Bionic).
---
tester@tester-SATELLITE-PRO-C850-19W:~$ sudo parted -ls
[sudo] lösenord för tester: 
Modell: KINGSTON  SUV400S37120G (scsi)
Disk /dev/sda: 120GB
Sektorstorlek (logisk/fysisk): [COLOR="#cc0000"]512B/4096B[/COLOR]
Partitionstabell: gpt
Disk Flags: 

Nummer  Början  ****    Storlek  Filsystem       Namn  Flaggor
 1      1049kB  2097kB  1049kB                         bios_grub
 2      2097kB  21,5GB  21,5GB   ext4
 3      115GB   120GB   5369MB   linux-swap(v1)

---

Created by the partitioner in the ubiquity installer.
---
tester@tester-SATELLITE-PRO-C850-19W:~$ sudo parted -ls
[sudo] password for tester: 
Model: KINGSTON  SKC300S37A120G (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): [COLOR="#cc0000"]512B/512B[/COLOR]
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      33,6MB  116GB  116GB   primary   ext4            boot
 2      116GB   120GB  4127MB  extended
 5      116GB   120GB  4127MB  logical   linux-swap(v1)

```

The new drive works correctly with the partitioner of the installer, when connected via internal SATA.

I tested the new drive in an **external box with the brand name Akasa**. Via this box the new SSD drive was seen with 512 B physical sectors, and the partitioner of the installer could manage the situation and install a working Lubuntu system.

This system works correctly when connected internally, even though the new SSD drive was seen with 4096 B physical sectors. It worked also via the Deltaco adapter, but with some quirks.

I checked for the hardware in the adapter and the external box. lsusb showed exactly the same identification for them (except the bus number)

```

$ diff -s temp1.txt temp2.txt
1c1
< Bus 004 Device 002: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
---
> Bus 002 Device 002: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge

```

The Deltaco adapter is newer than the Akasa box, I think one or two years newer. I guess the hardware and internal programming can be different, even though they have the same signature that is found by **lsusb**.

[hr][/hr]
I guess (but have not tested) that the same problem would appear with big HDDs with 4096 B physical sectors.

**Question:** *Have you found a new (currently sold) USB3 to SATA adapter or external box, where you can install Ubuntu and Ubuntu community flavours without problems (where the partitioner of ubiquity works correctly) with drives that have 4096 B physical sectors?*

In that case, please share your knowledge (tell us the brand name and model) :-P

---

### Post by TheFu on 2018-03-03
I had a strange issue installing 16.04.4 today. Post-install, the system wouldn't boot. I'd just put in a new SSD, with 4k sectors. The old SSD is dead - thousands of bad sectors.  The EFI part of the installation still isn't correct, but I've been able to boot it going through the EFI BIOS and picking a boot file manually.

Got other warnings before unlocking the encrypted partition ... the system wouldn't boot at all until I updated to newer BIOS.  I'm using a version of CoreBoot. I figured the problem was related to the intel CPU stuff being pushed out for the CPU this week.

Really happy I have backup religion. ;)

Considered putting 18.04-alpha on the machine, but decided against it at this point.  Have it running in a VM. Seems to be fine.

---

### Post by sudodus on 2018-03-04
@TheFu,

Thanks for showing that there can be other problems with new drives with 4k sectors. Not only USB boxes/adapters, but also the BIOS can create a problem.

---

### Post by TheFu on 2018-03-04
> **sudodus said:**
> @TheFu,

Thanks for showing that there can be other problems with new drives with 4k sectors. Not only USB boxes/adapters, but also the BIOS can create a problem.

Actually it wasn't a new SSD.  It was a different SSD that previously had been used in the machine 2 yrs ago. Worked fine then. My thinking is that the issue is related to the new intel firmware and kernel updates.  Only put it back because the prior SSD (128G) failed a few days ago after just under 4 yrs of use (3 yr warranty).

Plus the machine is a Toshiba CB35-C Chromebook (2015), so it isn't a normal computer in many respects.  The ChromeOS code name for it is "gandolf" for people who care.  It hasn't seen ChromeOS in a few years, however. ;)

The SSD warnings were about having 4k physical sectors, but Linux reporting 412b sectors.  I can't find the errors in the boot logs ... it is full of bluetooth, WPA supplicant, postfix and pulse errors (which will be solved as I carefully restore /etc/).  Restoring a fully encrypted install is non-trivial.

---

### Post by sudodus on 2018-03-04
@TheFu,

- I can imagine that restoring a fully encrypted install is non-trivial.

- Have you got any external box or adapter, where you can try to install Ubuntu into an SSD with 4K physical sectors?

---

### Post by TheFu on 2018-03-04
> **sudodus said:**
> @TheFu,

- I can imagine that restoring a fully encrypted install is non-trivial.

- Have you got any external box or adapter, where you can try to install Ubuntu into an SSD with 4K physical sectors?

TL;DR - no.

Since it is a chromebook running a non-commercial BIOS, boot options are limited.  There is no way to save most BIOS settings, for example.  I don't believe it can boot through EFI anything external, though I've never tried.  I did try to load Ubuntu-mate onto a 64G USB3 flash memory device yesterday.  Took 2+ hrs - maybe longer. I stopped watching it and did some yard work. ;)  Think the flash drive is nearing EoL. It was very fast for the 1st year of use, not so fast anymore. Post-install, it wouldn't boot.  I think that is when I decided to dig out the 64G SSD from another use, updated the chromebook BIOS firmware and try harder to get the machine to boot internally again. Chromebooks can be funny. Each model is a little different. Some will never boot anything but chromeos. Others can be made to boot anything and behave like a normal computer.  My Toshiba is somewhere in the middle.

---

### Post by sudodus on 2018-03-04
I have almost no experience of chromebooks.

As long as the 64G USB3 flash memory device is alive, you can try wiping the whole device (overwrite with zeros). This way I have recovered almost the original write speed, and I think also pushed gridlock and other fatal diseases further into the future. See this link, if you want more details,

[Pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

### Post by oldfred on 2018-03-04
I was in Illinois for a week for grand daughter's 3rd birthday.

So decided to pull out old 64GB SSD that was from 2011 and Microcenter (computer store) OEM.
Its seen as 
ata-SSD_G2_series_64GB.
And I connected it with this new USB to SATA adapter.
 KINGWIN USB3 TOSATA HDD ADAPTER 
Drive always was 512/512,  not newer 4K drive.


I had used SSD in my old BIOS system but gpt partitioned. So I Already had an ESP.
So did full install of 18.04 over old install of 12.04.

Now I have installed many full versions to flash drives without issue BIOS or UEFI, but this install, would not boot directly from UEFI.
And after several boot attempts my UEFI locked up. And my normal suggestions on cold boot did not work.
And even removing battery or jumpering reset pins did not work.
Finally got system working again by disconnecting main sda SSD. 

So I never had a full chance to debug issue as now back in Florida, but first time with major issues and external drive.

---

### Post by sudodus on 2018-03-05
@oldfred,

Thanks for sharing your experience of first time with major issues and external drive.

@everybody,

I have been thinking about 'my problem' and the Deltaco adapter: What makes gparted work, but not the partitioner in ubiquity, when the SSD has 4096 B physical sectors?

Can it be considered a bug in the partitioner in ubiquity, or is the Deltaco adapter sending some confusing information?

---

