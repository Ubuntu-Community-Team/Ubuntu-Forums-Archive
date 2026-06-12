---
title: "RocketRAID 622 rr62x:hpt_reset"
date: 2010-10-10
forum: Hardware
---

### Post by concordfta on 2010-10-10
Well this is getting frustrating!  I've had Linux software raid (mdadm) working for over 3 years.  I needed to expand, and slowly replace the old hard drives as they will be dieing soon.

I bought the Sans Digital TR5M-BP kit:

[http://www.sansdigital.com/towerraid-plus/tr5mbp.html](http://www.sansdigital.com/towerraid-plus/tr5mbp.html)

It's a VERY slick piece of hardware.  The only negative is that it comes with the Highpoint RocketRAID 622 PCI-e card.

I'm running Ubuntu 10.04.1 LTS Desktop on a Asus P5Q-E and have successfully migrated the drives out of my case and into this TR5M case, plus another TR5M case with all new drives.  I went and compiled the driver, since Highpoint is STILL on 9.10 for precompiled drivers.  I created the rr62x.ko driver and I am able to load it and see all of my drives and access them.  So I'm using the RocketRAID as a pass-through or JBOD setting, NOT fake-raid.

```

[   63.201986] rr62x:RocketRAID 62x SATA controller driver v1.1 (Oct  7 2010 19:38:39)
[   63.202012] pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   63.202017] pci 0000:02:00.0: setting latency timer to 64
[   63.202034] rr62x:adapter at PCI 2:0:0, IRQ 16
[   63.205002] rr62x:[0 0  ] start port.
[   63.205002] rr62x:[0 0  ] start port hard reset (probe 1).
[   63.205002] rr62x:[0 1  ] start port.
[   63.205002] rr62x:[0 1  ] start port hard reset (probe 1).
[   66.380095] rr62x:[0 0  ] start port soft reset (probe 1).
[   66.384091] rr62x:[0 1  ] start port soft reset (probe 1).
[   67.675183] rr62x:[0 0  ] pmp attached: vendor 1095 device 3726.
[   67.678166] rr62x:[0 1  ] pmp attached: vendor 1095 device 3726.
[   72.961072] rr62x:[0 0 0] start device soft reset.
[   73.645074] rr62x:[0 1 0] start device soft reset.
[   74.296111] rr62x:[0 0 1] start device soft reset.
[   74.950130] rr62x:[0 1 1] start device soft reset.
[   74.950130] rr62x:[0 0 2] start device soft reset.
[   76.263120] rr62x:[0 1 2] start device soft reset.
[   76.263120] rr62x:[0 0 3] start device soft reset.
[   77.575113] rr62x:[0 1 3] start device soft reset.
[   77.575113] rr62x:[0 0 4] start device soft reset.
[   78.887102] rr62x:[0 1 4] start device soft reset.
[   78.887102] rr62x:[0 0  ] port started successfully.
[   78.887102] rr62x:[0 0 0] device probed successfully.
[   78.887102] rr62x:[0 0 1] device probed successfully.
[   78.887102] rr62x:[0 0 2] device probed successfully.
[   78.887102] rr62x:[0 0 3] device probed successfully.
[   78.887102] rr62x:[0 0 4] device probed successfully.
[   79.870613] rr62x:[0 1  ] port started successfully.
[   79.870613] rr62x:[0 1 0] device probed successfully.
[   79.870613] rr62x:[0 1 1] device probed successfully.
[   79.870613] rr62x:[0 1 2] device probed successfully.
[   79.870613] rr62x:[0 1 3] device probed successfully.
[   79.870613] rr62x:[0 1 4] device probed successfully.
[   80.269774] scsi8 : rr62x
[   80.270012] scsi 8:0:0:0: Direct-Access     ATA      WDC WD10EACS-00D 01.0 PQ: 0 ANSI: 5
[   80.270078] scsi 8:0:1:0: Direct-Access     ATA      WDC WD10EACS-00D 01.0 PQ: 0 ANSI: 5
[   80.270144] scsi 8:0:2:0: Direct-Access     ATA      WDC WD10EACS-00D 01.0 PQ: 0 ANSI: 5
[   80.270207] scsi 8:0:3:0: Direct-Access     ATA      WDC WD10EACS-00Z 01.0 PQ: 0 ANSI: 5
[   80.270270] scsi 8:0:4:0: Direct-Access     ATA      WDC WD10EACS-00D 01.0 PQ: 0 ANSI: 5
[   80.270331] scsi 8:0:5:0: Direct-Access     ATA      WDC WD20EARS-00J 80.0 PQ: 0 ANSI: 5
[   80.270392] scsi 8:0:6:0: Direct-Access     ATA      WDC WD20EARS-00J 80.0 PQ: 0 ANSI: 5
[   80.270454] scsi 8:0:7:0: Direct-Access     ATA      WDC WD20EARS-00J 80.0 PQ: 0 ANSI: 5
[   80.270515] scsi 8:0:8:0: Direct-Access     ATA      WDC WD20EARS-00J 80.0 PQ: 0 ANSI: 5
[   80.270576] scsi 8:0:9:0: Direct-Access     ATA      WDC WD20EARS-00J 80.0 PQ: 0 ANSI: 5

```

See everything works great so far!! Happy, Happy!

Now for the kick in the head.... :confused:

On long writes (Lets say that I'm copying directories over from one raid to another, or large 4GB+ files) The damn driver resets on me!

```

[  517.988113] rr62x:hpt_reset(8/0/5)
[  517.992099] rr62x:[0 1  ] failed to disable comm status change bits
[  517.992099] rr62x:[0 1  ] start port.
[  517.992099] rr62x:[0 1  ] start port hard reset (probe 1).
[  521.167458] rr62x:hpt_reset(8/0/6)
[  521.167463] rr62x:hpt_reset(8/0/7)
[  521.167466] rr62x:hpt_reset(8/0/8)
[  521.167469] rr62x:hpt_reset(8/0/9)
[  524.169022] rr62x:[0 1  ] start port soft reset (probe 1).
[  529.061091] rr62x:[0 1 0] start device soft reset.
[  529.712159] rr62x:[0 1  ] port started successfully.
[  529.712159] rr62x:[0 1 0] device done to reset (reset 1)
[  594.988549] rr62x:hpt_reset(8/0/5)
[  594.992535] rr62x:[0 1  ] failed to disable comm status change bits
[  594.992535] rr62x:[0 1  ] start port.
[  594.992535] rr62x:[0 1  ] start port hard reset (probe 1).
[  601.104084] rr62x:[0 1  ] start port soft reset (probe 1).
[  606.001084] rr62x:[0 1 0] start device soft reset.
[  606.652602] rr62x:[0 1 2] start device soft reset.
[  607.309411] rr62x:[0 1  ] port started successfully.
[  607.309411] rr62x:[0 1 0] device done to reset (reset 1)
[  607.309411] rr62x:[0 1 2] device done to reset (reset 1)
[  607.789615] rr62x:hpt_reset(8/0/6)
[  607.789619] rr62x:hpt_reset(8/0/7)
[  607.789623] rr62x:hpt_reset(8/0/8)
[  607.789626] rr62x:hpt_reset(8/0/9)

```

This happens constantly and randomly!!  So in the middle of a file copy the port that is on the writing set of raid drives, decides to reset!!  This causes a file-system freeze for over a minute everytime!

In the above example you can see that port 2 (0 1 0) decides to reset, causing ALL 5 drives to be restarted.  Port 1 is still ok, since I was reading from that array.

Has anyone else seen this problem???  This is rendering my setup useless..

Thanks.

---

### Post by quelx on 2010-10-14
Try disabling the read ahead and write caches on each drive.  I had the same problem but after disabling the caches I have not had any more disconnects or kernel panics.

---

### Post by smeuse on 2010-11-18
Out of curiosity, are you using RE drives, or standard desktop drives? 

I'm thinking about purchasing a TR5M-BP and am curious if with Software raid it would make a difference or not. 

Also, has any looked at fake raid performance vs. Linux software raid on this device? Just curious mostly....would probably stick with software raid anyhow.

-Steve

---

### Post by quelx on 2010-11-21
> **smeuse said:**
> Out of curiosity, are you using RE drives, or standard desktop drives? 
-Steve

I am using Samsung HD204UI drives; regular desktop drives.

---

### Post by rod.batten on 2010-12-18
Is the sata_mv module loaded?  I'm having a similar problem with the rr64x module loaded.  rr and mv don't seem to play nice together.  

I've removed the sata_mv module and I'm going to see if it clears up that ugly hpt_reset issue on large file transfers.

My setup is:
SuperMicro T6016T SuperServer (Intel E5500 w/ 8GB installed)
Highpoint RocketRAID 644
15 bay port-multiplier enclosure
15x WD Caviar Black 2TB
OpenFiler

I realize that this machine is running rPath, not Ubuntu, but the problem seems to exist across distributions.

Anyone running *BSD with Highpoint RocketRAID cards?  (just for comparison)

---

### Post by quelx on 2010-12-18
I have moved to Gentoo for the system with the rr622 in it.  The relevant config bits from the kernel:
```
# CONFIG_SATA_MV is not set
# CONFIG_SATA_NV is not set

```

I am not using sata_mv.  What stopped the kernel panics for me was disabling the drive caches noted above.

---

### Post by rod.batten on 2010-12-27
I confirm that my problem was not with sata_mv.

I rethought my strategy (ease-of-management(==pure laziness)) and went from OpenFiler (kernel was older) back to a generic Ubuntu server (AMD64) installation.  The problem persisted, however.  

I duly filed a support request with Highpoint about a week ago, but  didn't receive any reply.  So, in frustration, I went out and purchased a low-end Silicon Image 3132 based card.   (I spent _my own money_ on this so that my boss would know that I was serious about it.)

I rebuilt my linux software RAID, scanned and  mounted the LVM volumes and didn't get a single error on the simple (but  large-ish) file transfer tests.  I haven't given it a full battery yet, but initial results indicate that it will work better (for my situation, at least). 

(Linux software RAID behind a decent UPS system is solid in my book).

I neglected to consider (or report earlier) that the port multipliers in our external enclosure are using the Silicon Image 3726 PM chip.  I had read about [COLOR=Blue][COLOR=Lime][BackBlaze's field research into using PMs and SATA controllers]("http://blog.backblaze.com/2009/09/01/petabytes-on-a-budget-how-to-build-cheap-cloud-storage/")[/COLOR] [/COLOR](see footnote), but wasn't really ready to give up on the (enclosure-vendor-supplied) rr644 card right away; Highpoint's current slogan states that it is "Port Multiplier ready".  So much for stubbornness (wish in one hand and shift in the other, see which fills up faster). :D 

I've also made sure that our enclosure vendor (Norco) is aware of the problem; their hardware is pretty cheap, but it does seem as though it's designed to do what it says on the tin.  Hopefully they'll be interested in making sure that they supply interface hardware that actually works with their enclosure systems. i.e. something other than the "RocketRAID" junk.

The only problem is that the low-end Silicon Image card only has two external ports and I need three ports to use all the disks in our enclosure.  The results so far, however, have given me enough encouragement to order a 4 port Silicon Image based controller.

The SMART data, etc are available to the OS when using the SI3132 card.  With the RocketRAID, the drives were only accessible as abstracted RocketRAID generic SCSI drives.  I'll dig into a bit more as time is available, but it seems like the SI card gives direct access to the drives.  

And there hasn't been a glut of bus resets either.  It's all gravy.

I'll report back when I get a >2 port SI-based card.  Hopefully it'll all be golden. 

If anyone ever hears anything useful from Highpoint tech support, I'd  like to hear it.  They haven't given me any help, and there's almost no  useful information to be gleaned by searching the web.

Footnote (*from BackBlaze' blog*):
[I]A note about SATA chipsets: Each of the port multiplier backplanes has a  Silicon Image SiI3726 chip so that five drives can be attached to one  SATA port. Each of the SYBA two-port PCIe SATA cards has a Silicon Image  SiI3132, and the four-port PCI Addonics card has a Silicon Image  SiI3124 chip. We use only three of the four available ports on the  Addonics card because we have only nine backplanes. We don&#8217;t use the  SATA ports on the motherboard because, despite Intel&#8217;s claims of port  multiplier support in their ICH10 south bridge, we noticed strange  results in our performance tests. Silicon Image pioneered port  multiplier technology, and their chips work best together.

[/I]_I.e. Check your PM chipset, fakeraid JBOD on RocketRAID doesn't seem to be a pass-through._

---

### Post by jjazz on 2011-01-03
I've had a rough time w/my RR 622 and the Sans Digital TR8MP. I was getting kernel panic as previously stated. Disabling the read ahead and write cached helped, but I'm only getting ~10MB writes in RAID10 using 8 WD1001FALS drives.

I contacted tech support detailing the issues and received the following email:
== Begin Response ==
Thank you for purchasing our product.
RR622 should be compatible with Ubuntu. Please try download and install the driver from HighPoint website.
[http://www.highpoint-tech.com/USA_new/series_rr600.htm](http://www.highpoint-tech.com/USA_new/series_rr600.htm)
Please click on "Download" and choose the correct version according to your OS under the "RocketRAID 622".
== End Response ==

Not really helpful.

Rod, Interested to hear your feedback on the 3132 card.

---

### Post by jjazz on 2011-01-12
Just wanted to follow up in case anyone else runs into this issue.

Purchased a SYBA PCIe card to replace the RR622. Was able to switch cards no problem. Card recognized without issue (Ubuntu 10.10 server), mdadm raid came back up after adjusting mdadm.conf to new device mappings. 

Attempted a large write and a drive immediately fell out. A few searches indicated that NCQ needed to be disabled on the drives so I added the following for each drive in rc.local:
```
echo 1 > /sys/block/sdX/device/queue_depth
```

was able to then read and write successfully, but still very slow and still generating errors:
```
Jan  8 14:29:54 i5server kernel: [    7.937687] ata4.15: Port Multiplier 1.1, 0x1095:0x3726 r23, 6 ports, feat 0x1/0x9
Jan  8 14:29:54 i5server kernel: [    7.938211] ata4.00: hard resetting link
Jan  8 14:29:54 i5server kernel: [    8.287772] ata4.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
Jan  8 14:29:54 i5server kernel: [    8.287847] ata4.01: hard resetting link
Jan  8 14:29:54 i5server kernel: [    8.637741] ata4.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  8 14:29:54 i5server kernel: [    8.637819] ata4.02: hard resetting link
Jan  8 14:29:54 i5server kernel: [    8.987704] ata4.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  8 14:29:54 i5server kernel: [    8.987782] ata4.03: hard resetting link
Jan  8 14:29:54 i5server kernel: [    9.337684] ata4.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  8 14:29:54 i5server kernel: [    9.337759] ata4.04: hard resetting link
Jan  8 14:29:54 i5server kernel: [    9.687631] ata4.04: SATA link down (SStatus 0 SControl 320)
Jan  8 14:29:54 i5server kernel: [    9.687777] ata4.05: hard resetting link
Jan  8 14:29:54 i5server kernel: [   10.037617] ata4.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
```

Doing some searching revealed that the esata cables may be suspect. I picked up 2 startech.com shielded esata cables and replaced them. Now everything is working great. 120MB/s writes and 1.5GB/s reads on raid10. The cables may have been the only problem initially, but it's hard to say given the behvior of the RR622 card.

Justin

---

### Post by Dr. Strange on 2011-01-12
Another FYI, in case someone comes along with the same problem. I started out with a vanilla install of Lucid (Kubuntu, but that's irrelevant) and had this exact issue. Finally got it sorted out last night / today after two weeks on-and-off banging my head on it. I have the TR8M running off the included RocketRAID card. The array has been syncing overnight and has generated zero hpt_reset errors. Long story short, I think the solution is this:

1. IF RUNNING A VERSION OF UBUNTU LOWER THAN 10.10, update to a 2.6.35 or higher kernel (note: 10.10 has a 2.6.35 kernel by default; you can skip this step by installing or upgrading to that version).
   #sudo apt-get update; sudo apt-cache search linux-image
   Find a suitable kernel version number (x) and build type (y - generic, server, whatever) on the resulting list.
   #sudo apt-get install linux-image-x.x.xx-xx-yyyy linux-headers-x.x.xx-xx-yyyy
   Reboot.

2. Read and do: [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

3. Insert the driver.
   #sudo modprobe rr62x
   Edit your /etc/modules and add rr62x on a new line at the end of the file.
   Reboot

4. Confirm the driver installs on boot.
   #lsmod | grep rr62x

5. Set up the drives in the card's BIOS (either reboot and hotkey into the card's BIOS directly during boot, or install and use the Highpoint web-GUI software from [http://www.highpoint-tech.com/USA_new/series_rr600.htm](http://www.highpoint-tech.com/USA_new/series_rr600.htm) with the system running). Note that setting up the actual RAID array directly on the card's BIOS limits arrays to five drives per - that's just a limitation of the card's BIOS. I prefer to set each drive up in the card's BIOS as its own JBOD array (a direct pass-through, basically), then use mdadm to set up the RAID array; that gets around the five-drive limit since the actual array control is in mdadm and not BIOS, and I personally prefer mdadm to on-chip fakeRAID anyway.

6. Wait. For scale, syncing a RAID-5 array of 8 2TB 5900RPM drives (Seagate Barracuda LPs) on an Atom D525 rig (it's just a home media server - needed small footprint and low heat production more than performance) takes about 24 hours. You can track the status via proc:
   #watch cat /proc/mdstat
   When the sync finishes, your array is done; set up the filesystem, fstab mounts, whatever, and rock on.

On previous attempts I'd have a huge list of hpt_reset errors by now, accompanied by the lights on the front of the enclosure flashing in sequence as the driver re-initializes and tries again, wash-rinse-repeat every few minutes. YMMV, but I've got an array as described in #6 at 85% sync after 16-some hours of syncing without a single error or a single observed enclosure reset.

---

### Post by jalder on 2011-01-12
I thought I'd add my recent experience with the TR8M with the RocketRAID card. I originally set it up with 8 1Tb disks using mdadm. I was getting frequent hpt_reset in the log. Under heavy load I would get a port reset, 30-60 second system hang and then the port would kick back in and the transfer would continue. However, at least two or three times the ports would not be reset properly and 4 out of my 8 disks would drop out (the top four lights on the chassis would be off). Losing 4 disks at once would pretty much destroy my RAID5. I also tried the onboard fakeraid with pretty much the same result. After reading here and on the Sans Digital forum I decided to dump the RocketRAID card for an Addonics ADSA3GPX1-2E. I haven't had any problems with the Addonics card so far, not a single error in the log. It also didn't need a driver to use pass-through which is a bonus. Its a bit slower than the RocketRAID since its SATA II rather than III, but I'm still getting 100 - 120 Mb/s writes using mdadm. 

My only problem now is the system doesn't want to boot properly without the RocketRAID card installed. I tried to blacklist rr62x in /etc/modprobe.d/blacklist.conf but it still looks like its trying to load the driver. I get a long mysterious dump at boot if the RocketRAID is not physically installed and it drops down to busybox (if I put the card in it boots). Luckily when it starts up I hit GRUB and can load an older kernel so I can boot without the RocketRAID card. I'm hoping if I have the RocketRAID card out when the next kernel update rolls around it will magically fix itself. If that fails, does anyone have any tips/instructions on how to uninstall the rr62x driver?

I noticed that Rosewill sells something pretty much identical to the TR8M but with a Sil 3132 card. If I ever need to buy another one I'd go that route.

---

### Post by ghost_zero on 2011-02-16
@jaider:
Are there any other good controller cards that work fine under Windows and Ubuntu (Linux in general) with RAID and are also available in Europe?

The one you mentioned I could only find in shops in the USA.
What is also important for me is that 3TB drives work fine in both Windows and Linux (partitions should be readable from both)


@Dr. Strange:
So you have no issues now? Is this still the case?
Because I haven't bought such a controller card yet but I am thinking about it. Especially, as it should also work fine wiht 3TB drives.
Are the partition tables (GPT) recognized in both Linux and Windows (with my current option which is only a SB750 fake-raid, I have an issue there).

EDIT:
Is there any news if a RocketRAID 622 driver will be included in future Linux kernels (without the need of installing an additional driver)?

---

### Post by Dr. Strange on 2011-04-04
@ghost_zero:
I had minor issues with it for quite some time; I'd say 98% reliable. Yesterday, it started acting up again rather badly. I upgraded to Maverick, just so I'd have a 2.6.35 kernel without having to manually bodge one into Lucid and re-built the driver. Didn't help. I finally realized that the 'bad behavior' correlated with times when I'd pull out the server from it's typical position next to my desk.

Reading upthread that cabling can be an issue, I took the 6' eSATA cables included in the kit that I'd velcro-tied to length (I need like a foot to get from the server to the RAID enclosure) and swapped them. Previously, Port 1 (drives 1 through 4) kept resetting. Once I switched the cables, Port 2 (drives 5 through 8 ) kept resetting. The problem followed the cable. I unwrapped the marginal cable and straightened it out. Since then, not a blip - instant 100% reliability. The cables I got were obviously from a grab-bin - they weren't even the same model (the connecters were slightly different shapes and stamped differently), and clearly one is marginal.

So I recommend my above procedure to get it working initially. If issues persist, replace the eSATA cables with something well-reviewed and generally considered reliable.

---

### Post by Dr. Strange on 2011-04-07
Update - I bought and installed this set of cables: [http://www.amazon.com/gp/product/B002G1YNRC](http://www.amazon.com/gp/product/B002G1YNRC)

The short length is ideal for my situation, as I have an Apex MI-008 server standing on top of the TR8M-B. I noticed a slight decrease in time between the driver loading on boot and Kubuntu seeing the array and continuing the boot process. The rig has been running for all of five minutes, but based on what I've been seeing to date, I'm five-nines sure my above post is the solution.


Update - Despite heavy bi-directional usage (simultaneously copying files to the array and streaming media from it), my server hasn't thrown a single reset error. I believe that the procedure I wrote up in post #10 plus a good set of eSATA cables is a solid solution, with the upside of not having to disable any caches.

---

### Post by JEDIDIAH on 2011-04-08
> **quelx said:**
> Try disabling the read ahead and write caches on each drive.  I had the same problem but after disabling the caches I have not had any more disconnects or kernel panics.

I tried this on mine and it seemed to do the trick. I disabled read ahead. Although I could not disable write caching.

```

echo "Turn off readahead for RAID drives..."

DRIVES=$( blkid | grep raid  | sed 's/:.*//g' )
for lun in $DRIVES; do
    hdparm -a0 $lun
done

```

---

### Post by Eikensson on 2011-06-09
Having the same problems with the RR622 but only when using the drives in a mdadm raid. Individually they work fine.

If disabling write cache it don't reset but the write speeds are terrible.

Just wanted to check if anyone have found a good solution?
Also wonder what kind of speeds i can expect if i decide to purchase a SIL3132 card instead that supposedly from what i have read should be much more stable but slower.

---

### Post by wangmaster on 2011-07-22
I had the same resets under load and during raid6 rebuild.  The idea of turning of caches to try to workaround the problem seems a kludge at best. Tried different esata cables and none made any difference.  

This was with a sans digital tr5m+ and 5 Samsung 2tb f4eg drives.

So I gave up on the rr622 card and bought a syba sy-pex40033 which is a straight up Marvell 9128 sata 6gb based controller and bingo. No problems. Transferred nearly 3tb of data to it so far and zero resets. 

From a performance stance the marvell 9128 solution should be a bit better than the sil3132 option and it just works with the drivers built into the kernel too.

I'be only been transferring files from USB2 drives so far so the performance is bottlenecked on the source end. Once I'm done with that I'll do raw read and write tests to see how it really performs.

---

### Post by geojams on 2011-10-11
After running an 8x2TB RAID6 array for some time with no problems, I decided to build another array and it has been nothing but trouble.  At first I didn't know any better and used WD20EARS drives.  After a few weeks of messing with those, I finally bought some Seagate ST2000DL003 drives since the ST32000542AS I have in the original array are not readily available.  After trying every trick, new cables, disable read ahead, etc, I finally have something I think works.  I am using the TR8M-B case with a RocketRaid 622 controller, and eight ST32000542AS drives, in a refurbed HP desktop PC I picked up for cheap.  Hopefully this helps someone get their setup working.

Here is what seems to have worked:


[LIST=1]
[*] Follow steps 1 through 4 in post 10 to get your rr62x driver installed. I used the v1.0 driver.

[*] Do not partition the drives.  When you create the array, use bare drives.  While I do not think this fixed the reset issue alone, I did see an immediate improvement in speed and reliability. The lights on the front of the case seemed to be more in sync than when using partitions to create the array.  

Create and format the array: 

#sudo mdadm -C --level 6 -n8 --chunk=512 /dev/md0 /dev/sd[bcdefghi] --assume-clean
 
#sudo mkfs.xfs /dev/md0


[*] Disable readahead and standby on each drive.  

 #sudo hdparm -a0 /dev/sdc
 #sudo hdparm -S0 /dev/sdc

You should add these to your hdparm.conf file so the settings are saved on reboot.

[/LIST]

I have transfered about 2TB of data over the past 12hours. I am getting about 60-70MB/s over a Gigabit link from the original server to the new.  hdparm -t /dev/md0 shows 195MB/s, so speed doesn't seem to be affected too much.

I did get one hpt_reset but it did not take out the array.  

It is yet to be seen if this is a long term fix for hpt_reset taking out arrays.  I just hope this saves someone some frustration and work.  Good luck and reply back if it helped.

---

### Post by pals0007 on 2012-04-19
I really need some help with this. I am brand new to Ubuntu 12 straight from windows my whole life. But so far I am loving Linux except for a few things. One of them being I can not get these rr622 v1.1 drivers to work I have tried all I could. I have over 200 DVDs on these drives so I desperately need help. 

Could some one please. Pretty please just compile this for me and email it I would be forever greatfull

---

### Post by pals0007 on 2012-04-20
Ok after days of trying I finally got it to work, but becuase of my many failed attempts whenever I install new software I get a failed installation error refering to rr62x files, so i tried the remove failed install command and nothing works, can someone please help me clean this up 


```
jesse@Office-PC:~$ sudo apt-get --fix-broken install
[sudo] password for jesse: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up rr62x-dkms (1.1) ...
Error! rr62x-1.O is already added!
Aborting.


Unable to load DKMS tarball /usr/share/rr62x-dkms/rr62x-1.1.dkms.tar.gz.
Common causes include: 
 - You must be using DKMS 2.1.0.0 or later to support binaries only
   distribution specific archives.
 - Corrupt distribution specific archive


dpkg: error processing rr62x-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 rr62x-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
jesse@Office-PC:~$ 

```

---

### Post by pals0007 on 2012-05-02
Bump

---

