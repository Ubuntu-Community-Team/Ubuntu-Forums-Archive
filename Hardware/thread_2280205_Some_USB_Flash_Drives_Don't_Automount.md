---
title: "Some USB Flash Drives Don't Automount"
date: 2015-05-28
forum: Hardware
---

### Post by mbratch on 2015-05-28
I am running Ubuntu Studio 14.04.

I have an old USB flash drive which, when I plug in, causes an icon to automatically appear on the desktop that looks like a thumb drive and says "67MB Volume". I can open it and it is the contents of the flash drive. When I got to a command prompt, I can see that Ubuntu has created a device /dev/sdf1 for this drive. It has been automatically mounted, but does not appear under /mnt or /media. [**EDIT:** Prompted by Keith Helms' question, I found that I was mistaken here: the thumb drive *does *appear under /media. I also tried an external USB hard drive, and it also automounted under /media.]

I have a newer USB flash drive from PNY which is 32GB capacity. When I plug it in, I do not get an icon on my desktop. It does not automatically mount anywhere. However, a /dev/sdf1 device does appear when I insert the thumb drive, and I can manually mount the drive to, for example, /mnt. I can read and write files from/to the volume and manually unmount it. However, I still do not get an icon on my desktop when I manually mount it.

I'm very puzzled why one will automount and the other won't I would prefer the automount behavior. Any ideas on what might be wrong? I've searched and read a lot about automount issues from users, but it's usually that they want to turn off automount, or that no drives will automount for them.

The ports are USB 2.0.

---

### Post by Keith_Helms on 2015-05-29
Where is the older thumb drive mounted if not under /mnt or /media?  Open a command line and run the command **df **to see if it is listed somewhere.  Is the drive listed in /etc/fstab?

---

### Post by mbratch on 2015-05-29
> **Keith_Helms said:**
> Where is the older thumb drive mounted if not under /mnt or /media?  Open a command line and run the command **df **to see if it is listed somewhere.  Is the drive listed in /etc/fstab?

OK that was my mistake. The "67 MB Volume" thumb drive does mount to /media/... I also tried a USB hard drive and it mounted under /media/...

However, my 32GB flash drive does not automount, which is the issue that I don't understand.

---

### Post by VMC on 2015-05-29
Does 'dmesg" reveal into special about that 32gb flash drive? I have one that reports "[FONT=monospace][COLOR=#000000][B]partition table partially beyond EOD, truncated".

[/B][/COLOR]
[/FONT]

---

### Post by mbratch on 2015-05-29
> **VMC said:**
> Does 'dmesg" reveal into special about that 32gb flash drive? I have one that reports "[FONT=monospace][COLOR=#000000]**partition table partially beyond EOD, truncated".**[/COLOR]
[/FONT]
Good question! Here's what comes from dmesg all after inserting the 32GB thumb drive:

```
[199923.234628] usb 3-6: new high-speed USB device number 30 using xhci_hcd
[199923.401173] usb 3-6: New USB device found, idVendor=154b, idProduct=005b
[199923.401182] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[199923.401186] usb 3-6: Product: USB 2.0 FD
[199923.401190] usb 3-6: Manufacturer: PNY Technologies
[199923.401193] usb 3-6: SerialNumber: ACBB12D0500000768
[199923.401491] usb 3-6: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
[199923.401502] usb 3-6: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes
[199923.402053] usb-storage 3-6:1.0: USB Mass Storage device detected
[199923.402350] scsi22 : usb-storage 3-6:1.0
[199924.838891] scsi 22:0:0:0: Direct-Access     PNY      USB 2.0 FD       1100 PQ: 0 ANSI: 4
[199924.839376] sd 22:0:0:0: Attached scsi generic sg6 type 0
[199924.839597] sd 22:0:0:0: [sdf] 63901440 512-byte logical blocks: (32.7 GB/30.4 GiB)
[199924.840151] sd 22:0:0:0: [sdf] Write Protect is off
[199924.840157] sd 22:0:0:0: [sdf] Mode Sense: 43 00 00 00
[199924.840698] sd 22:0:0:0: [sdf] No Caching mode page found
[199924.840708] sd 22:0:0:0: [sdf] Assuming drive cache: write through
[199924.846936]  sdf: sdf1
[199924.849814] sd 22:0:0:0: [sdf] Attached SCSI removable disk
```

When I plug in the "67 MB Volume", I get:

```
[200173.931558] usb 3-5: new full-speed USB device number 31 using xhci_hcd
[200174.096844] usb 3-5: New USB device found, idVendor=0204, idProduct=6025
[200174.096851] usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[200174.096855] usb 3-5: Product: Flash Disk
[200174.096857] usb 3-5: Manufacturer: CBM
[200174.096860] usb 3-5: SerialNumber: 0818030131609305
[200174.097610] usb-storage 3-5:1.0: USB Mass Storage device detected
[200174.097833] scsi23 : usb-storage 3-5:1.0
[200175.098084] scsi 23:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
[200175.098327] sd 23:0:0:0: Attached scsi generic sg6 type 0
[200175.098631] sd 23:0:0:0: [sdf] 130272 512-byte logical blocks: (66.6 MB/63.6 MiB)
[200175.098782] sd 23:0:0:0: [sdf] Write Protect is off
[200175.098785] sd 23:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[200175.098977] sd 23:0:0:0: [sdf] No Caching mode page found
[200175.098982] sd 23:0:0:0: [sdf] Assuming drive cache: write through
[200175.106770]  sdf: sdf1
[200175.107747] sd 23:0:0:0: [sdf] Attached SCSI removable disk
```

The most interesting variance is the addition of the following two lines in the 32GB case:

```
[199923.401491] usb 3-6: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
[199923.401502] usb 3-6: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes

```

But both say they've attached a SCSI removable disk. Although the first case doesn't get automounted.

---

### Post by VMC on 2015-05-29
> **mbratch said:**
> ...

The most interesting variance is the addition of the following two lines in the 32GB case:

```
[199923.401491] usb 3-6: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
[199923.401502] usb 3-6: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes

```

But both say they've attached a SCSI removable disk. Although the first case doesn't get automounted.

I've never seen that message. There are several bug reported for that error. Most effect scanners:
[http://superuser.com/questions/800057/has-my-flash-drive-failed-no-media](http://superuser.com/questions/800057/has-my-flash-drive-failed-no-media)
and
[http://lists.opensuse.org/opensuse/2015-01/msg00522.html](http://lists.opensuse.org/opensuse/2015-01/msg00522.html)

---

### Post by mbratch on 2015-05-29
In my case there's no problem mounting the drive manually. So the system obviously thinks it's OK. There's no error when I mount it manually. It just won't mount it automatically. I'll play around with reformatting the thumb drive different ways and see what happens.

[some minutes later...]

OK, I feel rather sheepish about it. I did a fresh reformat of the flash drive and now it will automount. I had not suspected an issue with the formatting since Windows liked it just fine (it automounted under Windows) and I could manually mount it and use it on Ubuntu. But that first link you posted made me think to reformat. There must have been something slightly amiss in the formatting of the thumb drive.

---

