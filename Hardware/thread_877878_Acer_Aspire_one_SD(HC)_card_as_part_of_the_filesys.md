---
title: "Acer Aspire one: SD(HC) card as part of the filesystem"
date: 2008-08-02
forum: Hardware
---

### Post by zzats on 2008-08-02
Hi all,

I'm using an acer aspire one computer, and tried to use a SDHC card as a part of the filesystem, but I'm experiencing strange problems I cannot solve myself.

I tried toying around with a fast SDHC card, and the original idea was to mount it as my home directory. The idea seemed a brilliant one, as it practically removed all the waitings involved with heavy firefox-caching or downloading large files, so the basic idea of "halving" the SSD-workload proved to work nicely, the overall responsiveness and speed of the system rose significantly. (if anyone has a good idea of how to benchmark these, let me know and I'm willing to try)

...but it was too good to be true. The problems arose when I first suspend my laptop, the ext2 system on the SD-card is getting corrupted due to unclean unmounts and the card reader device resetting itself (hint: partition table corrupts)

I tried some solutions, that I thought were potential ones. Had the reader been an USB-device, this is exactly what USB_PERSIST would have solved, but that doesn't help with PCIE-devices, obviously.

I tried also adding the sdhci, mmc_block and mmc_core modules to acpi whitelist, no luck -> the home partition cannot be unmounted for reasons unknown to me, and the laptop doesn't suspend at all.

Has anyone else tried to mount vital parts of the system, such as the root partition to an SD card and has managed to get the machine actually working this way? If so, could we try writing a small howto on the subject?

lspci output of the relevant parts
```

04:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
04:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
04:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
04:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384

```
lsmod output of the relevant parts
```

sdhci                  19076  0 
mmc_core               51460  2 mmc_block,sdhci

```

---

### Post by raptor386 on 2008-08-03
My install of Xubuntu won't even recognize the card readers in my machine. They won't even show up in lshw or lspci. Did you do anything special to get them to show up, or are you trying to do this on the default OS?

---

### Post by zzats on 2008-08-03
I'm doing this in Vanilla 8.04 ubuntu, try inserting the SD-card to the reader _before_ booting up ubuntu. I've heard similar problems, and that seems to be the solution.

I can't get my card-reader working either, but the "storage" expansion works nicely this way.

I've looked through the Linpus configuration files, and it seems more and more that it's using some patch for the kernel.

---

### Post by happyzax on 2008-08-06
I use a 16GB SDHC Card partitioned for /var /tmp and /home and it works great for me... I just don't use suspend.:wink:

Seriously, though, I recall that the fix for this was to compile the kernel with a patch (like you mentioned).  I think that is the proper solution.  I just don't know how to do this right now!

First, I have to get that internal mic working...](*,)

---

### Post by mistseeker on 2008-09-26
> **happyzax said:**
> I use a 16GB SDHC Card partitioned for /var /tmp and /home and it works great for me... I just don't use suspend.:wink:

Seriously, though, I recall that the fix for this was to compile the kernel with a patch (like you mentioned).  I think that is the proper solution.  I just don't know how to do this right now!

First, I have to get that internal mic working...](*,)

Is there somewhere a guide (how-to) that shows how to partition such a card for /var, /tmp and /home and how to make it automount at startup?

I'm a beginner in ubuntu and don't know how to do such fundamentals...

---

### Post by frostbyte1982 on 2008-09-26
I would be interested in a how to as well.  One of the reasons I got the Aspire one was that I had a 8 gb SDHC card for the storage expander slot.  And under linspire this happened automatically, my SSD looked like a 16 gb instead of a 8 gb.  Any ideas on how exactly to do it for a Ubuntu beginner??  Thanks!

---

### Post by malmjako on 2008-10-07
I would also be very interested in the solution for this. I'm thinking of installing most of a ubuntu system onto a 16 GB card, with only the necessary files for booting on the SSD, so that I can keep linpus on the machine as well.

---

### Post by undecidable on 2009-06-16
zzcats

As another datapoint which may be helpful:
I am using an eee 1000 running kubuntu 9.04.

It has two ssd cards mounted as /dev/sda and /dev/sdb and I have added a 16gb sdhc card as /dev/sdc.  I mount the sdhc card at boot time in the fstab as a separate partition /1docs, and use it for data.  

While it has some issues mounting at boot time (which I suspect are timing issues, see my post 17/6/09 for this) once mounted it has no problems.  It suspends/ unsuspends without issues - no corruption.  

Hope this is useful.

---

### Post by ianmillington on 2009-06-17
My position:

My wife has an Aspire 1 A110 running 2x8Gb cards as follows:

Card 1 7GB ext2  and 1 GB swap. This is how it arrived. I have allocated the 7GB to the main system

Card 2 (left hand slot) - On arrival was FAT 32(!) I reformatted it to Ext2 and use it as home.

I have found it to be unwise to either suspend or hibernate this machine as the following occurs:

Hibernate - seems to be treated as a forced shutdown as on subsequent startup it forces a file system check.

Suspend - Totally trashes the filesystem in card 2. The system cannot find the /home directory. Attempting to read it in the sd card reader of my laptop fails as it cannot recognise a file system. Using testdisk to check the card reports there to be an ext2 filesystem there but that it's irrecoverable. 

Result - suspending results in a need to reinstall. As a result I have configured things so as shut the computer down when the lid is closed. I do hope they fix this soon.

One question (as I've not tried it on the netbook as it's not my computer and I've messed up once already:redface:). In kde I can tell the system to save the session on shutdown - Can I do so with gnome as well?

---

### Post by undecidable on 2009-06-17
Are you referring to SSD cards or SDHC cards??

My 1st two cards are SSD, which I repartitioned and reformatted as ext2.  Suspends with no problem ever.  Have never tried to hibernate as I think the concept is useless.  

I have no HDDs.  

I have had issues trying to use SDHC cards as part of the filesystem, cf:  [http://ubuntuforums.org/showthread.php?t=1189625](http://ubuntuforums.org/showthread.php?t=1189625)
which I solved by having it mounted with the <pass> parameter set to 0 so it is not checked at boot, but is mounted.  

I suspect the problem is that these cards are not ready quickly enough, so that they give fstab spurious errors.  However as long as you don't try to correct the errors, there shoud be no problems.

---

### Post by ianmillington on 2009-06-17
Dn't know about the one in the machine, but the one in the left hand slot is definitely SDHC.

I can only say that when I tried to suspend the sdhc card in the left hand slot became unreadable by any means. As it had not, at that stage been backed up, given my understanding that suspend simply "worked" all data was lost. Thankfully it only had 4 documents on it, of which 3 had copies held elsewher so it was an irritation.

---

