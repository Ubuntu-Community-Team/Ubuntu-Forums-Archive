---
title: "OCZ Vertex 2 SSD unrecognized by Ubuntu - faulty drive?"
date: 2011-02-13
forum: Hardware
---

### Post by macho on 2011-02-13
I just bought a 60GB OCZ Vertex 2 SSD, which shows up fine in my BIOS. I tried installing Ubuntu to it earlier, but it failed/I aborted part way through. Now it still shows in the BIOS, but the 64-bit Maverick LiveCD I'm using doesn't recognize it. 

I'm suspecting it might be faulty hardware, but I don't feel confident enough to make this diagnosis myself. Here's a whole bunch of diagnostic info that may be helpful.

```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

Unable to read /dev/sda
```

```
ubuntu@ubuntu:~$ dmesg | grep sda
[    3.220567] sd 2:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    3.220594] sd 2:0:0:0: [sda] Write Protect is off
[    3.220596] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.220607] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.220691]  sda: sda1 sda2 < sda5 >
[    3.221664] sd 2:0:0:0: [sda] Attached SCSI disk
[   10.037351] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  208.641027] end_request: I/O error, dev sda, sector 116547528
[  208.641283] sd 2:0:0:0: [sda] READ CAPACITY(16) failed
[  208.641296] Adding 2438140k swap on /dev/sda5.  Priority:-1 extents:1 across:2438140k SS
[  208.641304] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  208.641314] sd 2:0:0:0: [sda] Sense not available.
[  208.641367] sd 2:0:0:0: [sda] READ CAPACITY failed
[  208.641371] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  208.641378] sd 2:0:0:0: [sda] Sense not available.
[  208.641449] sd 2:0:0:0: [sda] Asking for cache data failed
[  208.641456] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  208.641468] sda: detected capacity change from 60022480896 to 0
```

```
ubuntu@ubuntu:~$ sudo sg_format /dev/sda
inquiry: transport: Host_status=0x04 [DID_BAD_TARGET]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

/dev/sda doesn't respond to a SCSI INQUIRY
ubuntu@ubuntu:~$ 
```

I enabled SMART for the device in the BIOS and tried to use smartctl.

```
ubuntu@ubuntu:~$ sudo smartctl -t short /dev/sda
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

Short Background Self Test has begun
Use smartctl -X to abort test
ubuntu@ubuntu:~$ sudo smartctl --all /dev/sda -T permissive
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

Device: /2:0:0:0  Version: 
scsiModePageOffset: response length too short, resp_len=47 offset=50 bd_len=46
>> Terminate command early due to bad response to IEC mode page
Log Sense failed, IE page [scsi response fails sanity test]

Error Counter logging not supported
scsiModePageOffset: response length too short, resp_len=47 offset=50 bd_len=46
Device does not support Self Test logging
```

Any suggestions? Is there a way I can wipe the drive clean or otherwise make it functional? Should I take it back?

---

### Post by fjgaude on 2011-02-13
If it is easy to take back I would do it. Ubuntu 10.10 should have no issues with an OCZ SSD, though I know some few have had.

You should be able to install to the drive and it should be seen by the LiveCD.

---

### Post by J@n on 2011-02-14
Hi,

I encountered the same problem as you. Recognized in BIOS, found in gparted and that's it. In my case it appears to be an incompatible BIOS (simply too old) and I am trying the get a newer one from the community.

What BIOS / MoBo do you have and how old is it? It may shed some light on the subject.

HTH

Greetz,
J@n

---

### Post by dabl on 2011-02-14
You might try starting over by "dd'ing" the boot record and partition table

```
sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1
```

where "X" is the correct ID of your device.

Then set the BIOS SATA mode to "IDE" or "compatible" or "legacy" or whatever is not AHCI mode.

Then with GParted do "Device > New Partition Table", chooe "MS-DOS" type, and proceed with partitioning.  Then try installing Ubuntu again.

If it works, then you should be able to go into BIOS and change the SATA mode back to AHCI and get the faster performance.  Although, note this:

[http://ubuntuforums.org/showthread.php?t=1687311](http://ubuntuforums.org/showthread.php?t=1687311)

---

### Post by macho on 2011-02-14
Thanks for the replies!

J@n: I bought the board new at the same time as the OCZ drive a few days ago. It's an [Asus ASRock N68C-S UCC]("http://www.asrock.com/mb/overview.asp?model=n68c-s%20ucc"). Is it worth checking the BIOS?

dabl: Ubuntu doesn't seem to see the partition at all, so I can't write to it.

```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
dd: writing `/dev/sda': No space left on device
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000944044 s, 0.0 kB/s
```

I'll try making a bootable USB stick for 11.04 to see if that kernel has better luck, but the issue in the other thread seems unrelated to mine. (When I reboot I can check my specific BIOS version too...)

Any other thoughts?

---

### Post by J@n on 2011-02-15
Hi macho,

You might want to take a look at [www.ocztechnologyforum.com](www.ocztechnologyforum.com) and search the section Sandforce if there are any known issues with your board.

It is a good idea to check if your board has the latest BIOS. And if you can't get the SSD to work then a BIOS update (if available) is justified.

And if you are a real Dare Devil you might want to browse around [www.bios-mods.com](www.bios-mods.com) to see if somebody has already "modified" your BIOS (use at own risk and only as a last resort! Note that you will void your warranty)

Greetz,

J@n

---

### Post by chasem1991 on 2011-02-15
I have an OCZ Vertex 2 60GB and it works great with Ubuntu.  I would contact where you bought it and tell them it was DOA. If they tell you tough luck contact OCZ from what I understand they are good with just exchanging them.

-Check your bios settings and look for ACPI. Try enabling it if you can find it. Some motherboards automatically set this, others don't.

---

### Post by macho on 2011-02-21
Thanks everyone, for all the continuing advice. Unfortunately, I don't feel much closer.

The device is still only intermittently showing up. I was able to run mkfs.ext4 on it, but then as soon as I finished I was getting "No such device" for sdd. I physically moved the SSD over from sda, where it was earlier, in case you're wondering why it's sdd now.

I updated my BIOS to v1.40, which seems to be the newest version on the ASRock site. On the BIOS screen it identifies as AMI v02.67C, same as before (see attached photos). I took the drive back to the store, and they messed around and said they couldn't find a problem with it.

I tried setting ACPI: no effect either, unless maybe I'm setting it wrong. From the attached screenshot: I changed 'ACPI HPET Table' to 'Enabled', is there anything else I need to do?

I have a hunch it's the AHCI stuff, but I can't find anywhere to set that in the BIOS. Any idea how I might do it? From the attached screenshot you can see the options I have for each SATA device is between 'IDE' and 'RAID', and I've so far just kept it at IDE.

Any other ideas?

---

### Post by J@n on 2011-02-22
Hi Macho,

Your BIOS is setup correctly to work with the SSD (IDE mode for SATA controller). It seems AHCI is not working well with the Vertex 2.

I'll tell you how I faired with my SSD:

My mother board was indeed too old (nVidia chipset MCP61). So I bought myself a new one. This time I got an ASUS M4A78-EM with AMD chipsets. Connected the SSD on the first SATA port and the other disks on SATA 2 and 3. Tried to install but no luck (boy that makes you feel unlucky;))

Disconnected all drives and created a fresh Live CD. No luck. It crashed during install. Created a bootable disk with the Alternate version. Same result.

I created a bootable USB disk (pen drive) with UnetBootIn and tried again. This time I got a complete and succesfull install. Reconnected the other drives and now all is working perfectly.

You might want to try this approach (skip to the last step though:D)

HTH

Greetz,

J@n

---

### Post by johnross@johnross.com on 2011-03-02
I'm having similar problems with a 120 GB OCZ Vertex 2 SSD. I'm using Asus M2N68AM-Plus MB with latest BIOS. OCZ shows up in BIOS but Maverick 64 bit alternate install doesn't see it at all. Lucid 64 bit alternate sees it but crashes after partitioning during file copy.

I moved the OCZ to an external USB adapter. In this case Maverick install finds it and actually completes. Unfortunately it crashes on boot whether the drive is hooked to the external USB adapter or the internal SATA. 

If just try to use the drive as a secondary disk under Maverick it works fine. I put it in a WinXP box and formatted it NTFS and ran ATTO tests and it also works there as well. 

OCZ tech support hasn't given me any clues yet. If you guys have an ideas let me know. Thanks!

---

### Post by J@n on 2011-03-02
Hi Johnross,

Tried my approach? No drives but the OCZ and install using pen drive?

Let me know.

Greetz,

J@n

---

### Post by johnross@johnross.com on 2011-03-02
J@n,

Yes, I've tried installing from CD and I've also tried installing from usb flash drive with other drives connected and with all other drives disconnected. Results are always the same.

OCZ tech support suggested doing a secure erase to reset the drive but their firmware tool doesn't work on Windows XP and I don't have Vista/7 so I'm stuck on that approach.

This morning I tried doing a usb pen drive install of the latest natty build. It appears natty has the same issues as the others and it couldn't find the OCZ ssd.

I've done a lot of googling and I think the problem lies in a murky nexus of buggy bios firmware, ssd firmware and linux drivers. I'm guessing that no one really knows what the problem really is and even if they do I kind of doubt that it will get fixed any time soon.

At this point, I've wasted far more time trying to get this to work than the faster drive would have ever saved me on my applications so I've decided to give up on it and just go back to using my HHD for now. I may try a different make of SSD at a later date. Frustrating to say the least!

Thanks again for responding!

---

### Post by J@n on 2011-03-03
Hi Johnross,

I had the same frustrating experience with my first board (Asus M2N series). I too concluded the combination was causing the problems. So I bought the new board expecting install was going to be a breeze. Unfortunately it was quite difficult to get it working as you have read.

I found on the OCZ forum a tool/method to secure erase the disk. Haven't used it myself but you could investigate. Have a look here: [http://www.ocztechnologyforum.com/forum/showthread.php?81321-Secure-Erase-With-bootable-CD-USB-Linux..-Point-and-Click-Method](http://www.ocztechnologyforum.com/forum/showthread.php?81321-Secure-Erase-With-bootable-CD-USB-Linux..-Point-and-Click-Method)

Greetz,

J@n

---

### Post by johnross@johnross.com on 2011-03-03
Thanks for the link! I'll give it a try and let you know if I have any success.

---

### Post by johnross@johnross.com on 2011-03-03
Looks like partedmagic secure erase internal mode couldn't detect the ocz drive. It found my maxtor hdd just fine though. Oh well...

---

### Post by macho on 2011-03-03
> **J@n said:**
> I created a bootable USB disk (pen drive) with UnetBootIn and tried again. This time I got a complete and succesfull install. Reconnected the other drives and now all is working perfectly.

Thanks again, J@n. I finally got around to giving this a shot, but unfortunately I still get the same result. Any other thoughts, anyone?

---

### Post by macho on 2011-03-06
bump.

---

### Post by johnross@johnross.com on 2011-03-07
Over the weekend I put the ocz in an external usb adapter. I booted parted magic on a usb stick and was able to detect and wipe the ocz with secure erase. I was then able to install Maverick 64 bit from usb stick without any problems. The ocz booted and ran fine in the usb adapter. Unfortunately when I connected the drive to the SATA adapter on the Asus motherboard it froze with drive errors on boot. That was enough for me and I returned the drive to the seller for a refund. 

I'm done with ocz for now but would appreciate it if someone would e-mail me if you ever figure out the root cause of this issue. Thanks!

John

---

### Post by edwinclout on 2011-10-25
Same problem for me with a 120GB Corsair Force 3 Series SSD.

I tried a new Linux install from CD onto the drive, trying both Ubuntu 11.10 and Debian Testing.. but both failed at the same point..

Syslog reveals:

```
Oct 25 17:42:20 kernel: [    1.447477] libata version 3.00 loaded.
Oct 25 17:42:20 kernel: [    1.455693] pata_sis 0000:00:02.5: version 0.5.2

Oct 25 17:42:20 kernel: [    1.480712] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 25 17:42:20 kernel: [    1.493927] scsi0 : pata_sis
Oct 25 17:42:20 kernel: [    1.505575] scsi1 : pata_sis
Oct 25 17:42:20 kernel: [    1.516947] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
Oct 25 17:42:20 kernel: [    1.528328] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15

Oct 25 17:42:20 kernel: [    1.744260] ata1.00: ATAPI: TSSTcorp CDDVDW TS-L632H, TMC0, max UDMA/33
Oct 25 17:42:20 kernel: [    1.788233] ata1.00: configured for UDMA/33
Oct 25 17:42:20 kernel: [    1.800281] Refined TSC clocksource calibration: 1999.975 MHz.
Oct 25 17:42:20 kernel: [    1.812522] Switching to clocksource tsc
Oct 25 17:42:20 kernel: [    1.825711] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  TMC0 PQ: 0 ANSI: 5
Oct 25 17:42:20 kernel: [    1.838030] ata2: port disabled. ignoring.

Oct 25 17:42:20 kernel: [    1.880495] sata_sis 0000:00:05.0: version 1.0
Oct 25 17:42:20 kernel: [    1.880534] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 25 17:42:20 kernel: [    1.880540] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
Oct 25 17:42:20 kernel: [    1.947251] scsi2 : sata_sis
Oct 25 17:42:20 kernel: [    1.947388] scsi3 : sata_sis
Oct 25 17:42:20 kernel: [    1.947932] ata3: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 17
Oct 25 17:42:20 kernel: [    1.947935] ata4: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 17

Oct 25 17:42:20 kernel: [    7.480035] ata3.00: qc timeout (cmd 0x27)
Oct 25 17:42:20 kernel: [    7.493502] ata3.00: failed to read native max address (err_mask=0x4)
Oct 25 17:42:20 kernel: [    7.507191] ata3.00: HPA support seems broken, skipping HPA handling
Oct 25 17:42:20 kernel: [    7.708215] ata3.00: ATA-8: Corsair Force 3 SSD, 1.3, max UDMA/133
Oct 25 17:42:20 kernel: [    7.721907] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
Oct 25 17:42:20 kernel: [    7.756209] ata3.00: configured for UDMA/133
Oct 25 17:42:20 kernel: [    7.770092] scsi 2:0:0:0: Direct-Access     ATA      Corsair Force 3  1.3  PQ: 0 ANSI: 5
Oct 25 17:42:20 kernel: [    7.955617] sr 0:0:0:0: Attached scsi generic sg0 type 5
Oct 25 17:42:20 kernel: [    7.976509] scsi 2:0:0:0: Attached scsi generic sg1 type 0
Oct 25 17:42:20 kernel: [    7.991283] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Oct 25 17:42:20 kernel: [    8.007956] sd 2:0:0:0: [sda] Write Protect is off
Oct 25 17:42:20 kernel: [    8.021802] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 25 17:42:20 kernel: [    8.022424] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 25 17:42:20 kernel: [    8.051637]  sda: sda1 sda2 < sda5 >
Oct 25 17:42:20 kernel: [    8.066370] sd 2:0:0:0: [sda] Attached SCSI disk

Oct 25 17:42:20 kernel: [   38.848028] ata3: lost interrupt (Status 0x58)
Oct 25 17:42:20 kernel: [   38.863129] ata3: drained 512 bytes to clear DRQ.
Oct 25 17:42:20 kernel: [   38.863138] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct 25 17:42:20 kernel: [   38.877849] ata3.00: failed command: IDENTIFY DEVICE
Oct 25 17:42:20 kernel: [   38.892153] ata3.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
Oct 25 17:42:20 kernel: [   38.892155]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 25 17:42:20 kernel: [   38.920958] ata3.00: status: { DRDY }
Oct 25 17:42:20 kernel: [   38.920986] ata3: soft resetting link
Oct 25 17:42:20 kernel: [   39.212209] ata3.00: configured for UDMA/133
Oct 25 17:42:20 kernel: [   39.226301] ata3: EH complete

Oct 25 17:43:26 kernel: [  104.928061] ata3: lost interrupt (Status 0x58)
Oct 25 17:43:26 kernel: [  104.928430] ata3: drained 512 bytes to clear DRQ.
Oct 25 17:43:26 kernel: [  104.928438] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct 25 17:43:26 kernel: [  104.928442] ata3.00: failed command: IDENTIFY DEVICE
Oct 25 17:43:26 kernel: [  104.928448] ata3.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
Oct 25 17:43:26 kernel: [  104.928449]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 25 17:43:26 kernel: [  104.928452] ata3.00: status: { DRDY }
Oct 25 17:43:26 kernel: [  104.928477] ata3: soft resetting link
Oct 25 17:43:26 kernel: [  105.124210] ata3.00: configured for UDMA/133
Oct 25 17:43:26 kernel: [  105.124229] ata3: EH complete

Oct 25 17:45:07 kernel: [  205.920025] ata3: lost interrupt (Status 0x58)
Oct 25 17:45:07 kernel: [  205.920394] ata3: drained 512 bytes to clear DRQ.
Oct 25 17:45:07 kernel: [  205.920402] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct 25 17:45:07 kernel: [  205.920406] ata3.00: failed command: IDENTIFY DEVICE
Oct 25 17:45:07 kernel: [  205.920412] ata3.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
Oct 25 17:45:07 kernel: [  205.920414]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 25 17:45:07 kernel: [  205.920417] ata3.00: status: { DRDY }
Oct 25 17:45:07 kernel: [  205.920442] ata3: soft resetting link
Oct 25 17:45:07 kernel: [  206.180210] ata3.00: configured for UDMA/133
Oct 25 17:45:07 kernel: [  206.180230] ata3: EH complete

Oct 25 17:47:16 kernel: [  334.880026] ata3: lost interrupt (Status 0x58)
Oct 25 17:47:16 kernel: [  334.880395] ata3: drained 512 bytes to clear DRQ.
Oct 25 17:47:16 kernel: [  334.880405] ata3.00: limiting speed to UDMA/100:PIO4
Oct 25 17:47:16 kernel: [  334.880409] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct 25 17:47:16 kernel: [  334.880413] ata3.00: failed command: IDENTIFY DEVICE
Oct 25 17:47:16 kernel: [  334.880419] ata3.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
Oct 25 17:47:16 kernel: [  334.880420]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 25 17:47:16 kernel: [  334.880423] ata3.00: status: { DRDY }
Oct 25 17:47:16 kernel: [  334.880449] ata3: soft resetting link
Oct 25 17:47:16 kernel: [  335.116210] ata3.00: configured for UDMA/100
Oct 25 17:47:16 kernel: [  335.116229] ata3: EH complete

Oct 25 17:48:18 kernel: [  396.896022] ata3: lost interrupt (Status 0x50)
Oct 25 17:48:18 kernel: [  396.896040] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct 25 17:48:18 kernel: [  396.896044] ata3.00: failed command: FLUSH CACHE
Oct 25 17:48:18 kernel: [  396.896049] ata3.00: cmd e7/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Oct 25 17:48:18 kernel: [  396.896051]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 25 17:48:18 kernel: [  396.896054] ata3.00: status: { DRDY }
Oct 25 17:48:18 kernel: [  396.896079] ata3: soft resetting link
Oct 25 17:48:18 kernel: [  397.164210] ata3.00: configured for UDMA/100
Oct 25 17:48:18 kernel: [  397.164214] ata3.00: retrying FLUSH 0xe7 Emask 0x4
Oct 25 17:48:33 kernel: [  412.164027] ata3.00: qc timeout (cmd 0xe7)
Oct 25 17:48:33 kernel: [  412.164032] ata3.00: FLUSH failed Emask 0x4
Oct 25 17:48:33 kernel: [  412.164054] ata3: soft resetting link
Oct 25 17:48:33 kernel: [  412.400209] ata3.00: configured for UDMA/100
Oct 25 17:48:33 kernel: [  412.400213] ata3.00: retrying FLUSH 0xe7 Emask 0x4
Oct 25 17:48:48 kernel: [  427.400031] ata3.00: qc timeout (cmd 0xe7)
Oct 25 17:48:48 kernel: [  427.400037] ata3.00: FLUSH failed Emask 0x4
Oct 25 17:48:48 kernel: [  427.400042] ata3.00: limiting speed to UDMA/100:PIO3
Oct 25 17:48:48 kernel: [  427.400068] ata3: soft resetting link
Oct 25 17:48:49 kernel: [  427.596210] ata3.00: configured for UDMA/100
Oct 25 17:48:49 kernel: [  427.596213] ata3.00: retrying FLUSH 0xe7 Emask 0x4
Oct 25 17:49:19 kernel: [  457.596031] ata3.00: qc timeout (cmd 0xe7)
Oct 25 17:49:19 kernel: [  457.596037] ata3.00: FLUSH failed Emask 0x4
Oct 25 17:49:19 kernel: [  457.596040] ata3.00: disabled
Oct 25 17:49:19 kernel: [  457.596056] ata3.00: device reported invalid CHS sector 0
Oct 25 17:49:19 kernel: [  457.596082] ata3: soft resetting link
Oct 25 17:49:19 ata_id[4852]: HDIO_GET_IDENTITY failed for '/dev/sda': No message of desired type
Oct 25 17:49:19 kernel: [  457.752059] ata3: EH complete
Oct 25 17:49:19 kernel: [  457.752300] sd 2:0:0:0: [sda] READ CAPACITY(16) failed
Oct 25 17:49:19 kernel: [  457.752303] sd 2:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 25 17:49:19 kernel: [  457.752308] sd 2:0:0:0: [sda] Sense not available.
Oct 25 17:49:19 kernel: [  457.752342] sd 2:0:0:0: [sda] READ CAPACITY failed
Oct 25 17:49:19 kernel: [  457.752344] sd 2:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 25 17:49:19 kernel: [  457.752348] sd 2:0:0:0: [sda] Sense not available.
Oct 25 17:49:19 kernel: [  457.752407] sd 2:0:0:0: [sda] Asking for cache data failed
Oct 25 17:49:19 kernel: [  457.752409] sd 2:0:0:0: [sda] Assuming drive cache: write through
Oct 25 17:49:19 kernel: [  457.752417] sda: detected capacity change from 120034123776 to 0

```

---

### Post by Sandro kensan on 2012-09-15
I have not Ubuntu, but I have OCZ Vertex 2 Sata II and the same problem. I have an old PC with intel d865perl but the same results.

Same dmesg, HDD maxtor (the same of someone in this 3ad), same smartctl --all /dev/sdb results. I have try all my live cd (madriva, pardus, mageia) and gparted without luck.

Windows XP install fine and works fine. Pardus 2011.2 dama dama find ocz ssd and i can write on it but not to partition it. With an old mandriva live i can to partition it, i'll try some suggestion in this 3ad but I'm not optimistic.

---

### Post by Sandro kensan on 2012-09-16
Ok, I finally return the OCZ vertex2 to my frend. This is what i learn.

My Intel perl moterboard is ok. I turn the bios sata mode to legacy how suggested by dub (TY very much). My linux box Pardus dama dama is able to make partition table, to partition the ssd, to format the ssd very well without the dd procedure and witout Gparted but only with the tools in the distro. The ssd is mountable and writable (root mode). So i can write an OS inside the partitions.

Every live cd that i have try failed to install. The ssd is not formatable, sometimes is not recognized, sometimes is instable, only with pardus dama dama works fine but the install dvd don't recognize the partition table.

In my linux box with perl the ssd is frozen and de-frozen procedure failed because the system froze. My pc don't shout down and reamain in sleep cause the ssd, i don't know why.

It is that i have learnel. So if you get the SSD Vertex2 OCZ sata II, leave it.

---

