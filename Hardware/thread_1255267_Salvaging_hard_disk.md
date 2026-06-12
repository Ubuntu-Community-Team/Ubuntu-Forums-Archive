---
title: "Salvaging hard disk"
date: 2009-09-01
forum: Hardware
---

### Post by Arndt on 2009-09-01
I had a Dell stationary computer, on which I ran Ubuntu (Breezy Badger). Something is broken in the computer, so that at first it would sporadically stop, and the screen tell me "no video signal". I could get the computer working again by repeatedly rebooting, each time getting further, so it took half a dozen restarts to get it functional. Things got worse, and now it won't get beyond "mounting root partition" (or something to that effect).

I have taken out the hard disk and connected it to another computer using USB. Doing so makes an icon labelled "USB Drive" appear in the Places->Computer tool, but I can't mount it, or even fsck it. What things could I try in order to retrieve what's on the disk?

---

### Post by RumboPumbo on 2009-09-01
This might not be much use as i havent got Ubuntu but this happened to me a couple of weeks ago just different problem and so as you have done got it connected using USB, with me we just opened it like a USB memory stick and then it comes up with all the folders, this is where you can salvage all the files by searching through these files, hope this is useful or not.

---

### Post by Arndt on 2009-09-01
> **RumboPumbo said:**
> This might not be much use as i havent got Ubuntu but this happened to me a couple of weeks ago just different problem and so as you have done got it connected using USB, with me we just opened it like a USB memory stick and then it comes up with all the folders, this is where you can salvage all the files by searching through these files, hope this is useful or not.

When I double click on that icon "USB Drive", it says "Can't mount file". I have no experience with USB memory sticks, so maybe I misunderstand something.

---

### Post by RumboPumbo on 2009-09-01
hmm, that shouldnt happen, I am guessing you are using a HDD Caddy, if so then are you sure that you have the right drivers?

---

### Post by Arndt on 2009-09-01
> **RumboPumbo said:**
> hmm, that shouldnt happen, I am guessing you are using a HDD Caddy, if so then are you sure that you have the right drivers?

I don't know. What drivers would I need?

This is what dmesg says when I attach it:

[17118.728590] usb 2-1: new high speed USB device using ehci_hcd and address 7
[17118.862776] usb 2-1: configuration #1 chosen from 1 choice
[17118.865050] scsi6 : SCSI emulation for USB Mass Storage devices
[17118.865446] usb-storage: device found at 7
[17118.865451] usb-storage: waiting for device to settle before scanning
[17123.864990] usb-storage: device scan complete
[17123.865875] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[17123.870466] sd 6:0:0:0: [sdb] Attached SCSI disk
[17123.870614] sd 6:0:0:0: Attached scsi generic sg2 type 0

---

### Post by RumboPumbo on 2009-09-01
Ah now the drivers i wouldnt be able to know as i don't have ubuntu yet, you may be able to find out by going onto the company that made the caddy to see if they even support linux. Sorry i can't be much help.

---

### Post by tomBorgia on 2009-09-01
> **Arndt said:**
> I don't know. What drivers would I need?

This is what dmesg says when I attach it:

[17118.728590] usb 2-1: new high speed USB device using ehci_hcd and address 7
[17118.862776] usb 2-1: configuration #1 chosen from 1 choice
[17118.865050] scsi6 : SCSI emulation for USB Mass Storage devices
[17118.865446] usb-storage: device found at 7
[17118.865451] usb-storage: waiting for device to settle before scanning
[17123.864990] usb-storage: device scan complete
[17123.865875] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[17123.870466] sd 6:0:0:0: [sdb] Attached SCSI disk
[17123.870614] sd 6:0:0:0: Attached scsi generic sg2 type 0

I'm assuming your using a (S)ATA to USB adapter -the last bit there shows the device is working properly... assigning it /dev/sdb - If it could automount the partitions it would right there and you'd be able to access the drive - It'd put an icon on your desktop linking to the disk. 

If this doesn't then I'd suggest you try testdisk (you'll need to install it with synaptic) to try and recover the partition table...

---

### Post by Arndt on 2009-09-01
> **RumboPumbo said:**
> Ah now the drivers i wouldnt be able to know as i don't have ubuntu yet, you may be able to find out by going onto the company that made the caddy to see if they even support linux. Sorry i can't be much help.

Thanks for the help so far, but obviously it supports linux since I took it out from a once working computer which ran Ubuntu.

---

### Post by PaulReaver on 2009-09-01
Stupidly obvious question, but have you tried to mount it as sudo/root
or tried to access it via nautilus run as root.

---

### Post by Arndt on 2009-09-01
> **PaulReaver said:**
> Stupidly obvious question, but have you tried to mount it as sudo/root
or tried to access it via nautilus run as root.

According to a colleague, it's supposed to appear on the desktop when it's plugged in, even if unformatted. But mounting, yes, I tried that. And fsck too, which is needed before mounting if it's become (slightly) corrupted, but fsck doesn't like it either:

```
# fsck /dev/sdb
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Invalid argument while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```
And following that advice didn't work better.

The only place where it appears is in Places->Computer, as "USB Drive", and there exists the option "Mount Volume", but then I get the message "Can't mount file".

---

### Post by trundlenut on 2009-09-01
you could try putting it back into the original machine and booting from a live cd such as Ultimate Boot CD or system rescue CD and test the disk for errors.  I have managed to rescue disks with bad sectors which were causing all sorts of problems on a windows machine.

---

### Post by Arndt on 2009-09-11
> **trundlenut said:**
> you could try putting it back into the original machine and booting from a live cd such as Ultimate Boot CD or system rescue CD and test the disk for errors.  I have managed to rescue disks with bad sectors which were causing all sorts of problems on a windows machine.

Thanks for all the advice. I managed in the end to boot the computer again, with the hard disk put back in it, and copying the data from it to another computer over the wlan. There was no actual error on the disk once I got that far. I still don't know if there was an intermittent error on the disk, or some other hardware error on the computer.

---

