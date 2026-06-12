---
title: "SATA Drive Issue"
date: 2008-06-17
forum: Hardware
---

### Post by Posty on 2008-06-17
After installing Ubuntu 8.04, I was able to access my IDE and USB hard drives just fine... However, my SATA disk (which is my main Windows drive, and has a majority of my files on it) isn't read by Ubuntu. I have a feeling that the drive isn't being initialized properly, due to the boot time being extremely long at the point where it mounts hard drives, and also on doing a reboot the SATA drive has trouble being detected in the BIOS even. However, the drive works perfectly under XP and Vista... I'm not sure if it helps, but my motherboard is an XFX nForce 680i LT SLi.

Any ideas?

---

### Post by ajgreeny on 2008-06-17
Can you see it in the output of ```
sudo fdisk -l
``` in terminal or is it completely unseen in ubuntu?

Try mounting it manually, first making sure you have the folder /media/windows with the command ```
sudo mkdir /media/windows
``` then with the command ```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```You will need to change the disk ident (/dev/hda1 in my example) to your own situation, which hopefully you will have got from the fdisk command earlier.  If that still doesn't do anything come back again and we'll see what else can be suggested.

---

### Post by Posty on 2008-06-18
> **ajgreeny said:**
> Can you see it in the output of ```
sudo fdisk -l
``` in terminal or is it completely unseen in ubuntu?

Try mounting it manually, first making sure you have the folder /media/windows with the command ```
sudo mkdir /media/windows
``` then with the command ```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```You will need to change the disk ident (/dev/hda1 in my example) to your own situation, which hopefully you will have got from the fdisk command earlier.  If that still doesn't do anything come back again and we'll see what else can be suggested.

fdisk doesn't list the drive at all... I have a feeling that it might be something to do with the SATA controller, but I don't exactly know how to go about fixing that. Either way, there's something wrong with it...

---

### Post by Imaginary on 2008-06-18
I've been having similiar problems.  While mine aren't solved yet, it'd be nice to see whether we're stuck up the same tree.

1) Are there any items in your /var/log/messages regarding your SATA?  Bonus points if you've got messages like:

```
ata1.00 failed to IDENTIFY (I/O error err_mask=0x4)
```

2) Is your SATA controller being properly recognized in the output from lspci?  Or are you getting unknown devices, particularly unknown bridge devices?

---

### Post by Posty on 2008-06-18
> **Imaginary said:**
> I've been having similiar problems.  While mine aren't solved yet, it'd be nice to see whether we're stuck up the same tree.

1) Are there any items in your /var/log/messages regarding your SATA?  Bonus points if you've got messages like:

```
ata1.00 failed to IDENTIFY (I/O error err_mask=0x4)
```

2) Is your SATA controller being properly recognized in the output from lspci?  Or are you getting unknown devices, particularly unknown bridge devices?

This might have something to do with it...

```
Jun 19 05:53:47 posty-desktop kernel: [   56.403948] ata3: soft resetting link
Jun 19 05:53:47 posty-desktop kernel: [   56.559644] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 05:53:47 posty-desktop kernel: [   86.507460] ata3.00: qc timeout (cmd 0x27)
Jun 19 05:53:47 posty-desktop kernel: [   86.507462] ata3.00: failed to read native max address (err_mask=0x4)
Jun 19 05:53:47 posty-desktop kernel: [   86.507465] ata3: failed to recover some devices, retrying in 5 secs
Jun 19 05:53:47 posty-desktop kernel: [   91.501419] ata3: hard resetting link
Jun 19 05:53:47 posty-desktop kernel: [   91.977467] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 05:53:47 posty-desktop kernel: [  121.916301] ata3.00: qc timeout (cmd 0xec)
Jun 19 05:53:47 posty-desktop kernel: [  121.916304] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jun 19 05:53:47 posty-desktop kernel: [  121.916306] ata3: failed to recover some devices, retrying in 5 secs
Jun 19 05:53:47 posty-desktop kernel: [  126.910263] ata3: hard resetting link
Jun 19 05:53:47 posty-desktop kernel: [  127.385314] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 05:53:47 posty-desktop kernel: [  157.326142] ata3.00: qc timeout (cmd 0xec)
Jun 19 05:53:47 posty-desktop kernel: [  157.326145] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jun 19 05:53:47 posty-desktop kernel: [  157.326147] ata3.00: disabled
Jun 19 05:53:47 posty-desktop kernel: [  163.169396] ata3: port is slow to respond, please be patient (Status 0xd0)
Jun 19 05:53:47 posty-desktop kernel: [  167.863962] ata3: device not ready (errno=-16), forcing hardreset
Jun 19 05:53:47 posty-desktop kernel: [  167.863963] ata3: hard resetting link
Jun 19 05:53:47 posty-desktop kernel: [  168.339015] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 05:53:47 posty-desktop kernel: [  168.339037] ata3: EH complete
Jun 19 05:53:47 posty-desktop kernel: [  168.339047] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339050] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339071] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339073] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339087] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339089] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339100] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339102] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339112] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339114] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339126] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339128] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339137] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339139] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339148] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339150] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339159] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339161] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339166] Dev sdb: unable to read RDB block 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339172] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339174] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339183] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339184] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339195] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339197] end_request: I/O error, dev sdb, sector 24
Jun 19 05:53:47 posty-desktop kernel: [  168.339203] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339205] end_request: I/O error, dev sdb, sector 24
Jun 19 05:53:47 posty-desktop kernel: [  168.339214] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339215] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339223] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:53:47 posty-desktop kernel: [  168.339225] end_request: I/O error, dev sdb, sector 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339228]  unable to read partition table
Jun 19 05:53:47 posty-desktop kernel: [  168.339264] sd 2:0:0:0: [sdb] Attached SCSI disk
Jun 19 05:53:47 posty-desktop kernel: [  168.339293] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jun 19 05:53:47 posty-desktop kernel: [  168.339319] ACPI: PCI Interrupt 0000:00:0e.1[B] -> Link [ASA1] -> GSI 22 (level, low) -> IRQ 17
```

But when I look further into the log... I see that the SATA drive seemed to be detected at first and was actually "working"...

```
Jun 19 05:53:47 posty-desktop kernel: [   25.561937] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 05:53:47 posty-desktop kernel: [   25.650792] ata3.00: ATA-7: Maxtor 6B160P0, BAH41G10, max UDMA/133
Jun 19 05:53:47 posty-desktop kernel: [   25.650794] ata3.00: 320173056 sectors, multi 16: LBA48 
Jun 19 05:53:47 posty-desktop kernel: [   25.650795] ata3.00: applying bridge limits
Jun 19 05:53:47 posty-desktop kernel: [   25.834419] ata3.00: configured for UDMA/100
Jun 19 05:53:47 posty-desktop kernel: [   26.144788] ata4: SATA link down (SStatus 0 SControl 300)
Jun 19 05:53:47 posty-desktop kernel: [   26.155176] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6B160P0   BAH4 PQ: 0 ANSI: 5
Jun 19 05:53:47 posty-desktop kernel: [   26.155224] sd 2:0:0:0: [sdb] 320173056 512-byte hardware sectors (163929 MB)
Jun 19 05:53:47 posty-desktop kernel: [   26.155232] sd 2:0:0:0: [sdb] Write Protect is off
Jun 19 05:53:47 posty-desktop kernel: [   26.155246] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 19 05:53:47 posty-desktop kernel: [   26.155274] sd 2:0:0:0: [sdb] 320173056 512-byte hardware sectors (163929 MB)
Jun 19 05:53:47 posty-desktop kernel: [   26.155281] sd 2:0:0:0: [sdb] Write Protect is off
Jun 19 05:53:47 posty-desktop kernel: [   26.155295] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

To be honest, I don't know nearly enough about Linux to make heads or tails about all of this... Hence the reason why I'm posting on here =P

---

### Post by Posty on 2008-06-18
*bump*

Any ideas? =\ This is really the only thing that's keeping me from using my Ubuntu installation.

---

### Post by markbuntu on 2008-06-19
Could you check your bios and see if somewhere in there is an option for SATA?
If so, make sure it is turned on.

---

### Post by Posty on 2008-06-19
> **markbuntu said:**
> Could you check your bios and see if somewhere in there is an option for SATA?
If so, make sure it is turned on.

I don't think you realized... I said in my first post that both XP and Vista recognize it, because well... They're installed on it. So it's not an issue with the BIOS.

---

### Post by Odrodzona-Sarmacja on 2008-06-21
Try "sudo blkid" and if your Ubuntu recognizes the hardware it should be listed there also with correct device (alike /dev/XXX) used by Ubuntu for it. Mount it then with that device. Fix your fstab to automount it too.

Good luck!

---

### Post by Posty on 2008-06-23
> **Odrodzona-Sarmacja said:**
> Try "sudo blkid" and if your Ubuntu recognizes the hardware it should be listed there also with correct device (alike /dev/XXX) used by Ubuntu for it. Mount it then with that device. Fix your fstab to automount it too.

Good luck!

Sadly, as I had said before with the fdisk -l, the device doesn't list... It's only detected prior to Ubuntu's full boot.. and afterwards, it simply stops working. As I had said, if I simply do a reboot, the BIOS has issues reading the drive after any distro of Linux tries using it... I simply don't understand it.

---

### Post by Odrodzona-Sarmacja on 2008-06-23
Indeed it sounds like bios issue. If plug&play automations does fail, then did you try setting your bios for non-plug and play os and then to reconfigure itself its hardware setup?

---

