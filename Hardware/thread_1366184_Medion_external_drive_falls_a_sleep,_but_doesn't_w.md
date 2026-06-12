---
title: "Medion external drive falls a sleep, but doesn't wak up"
date: 2009-12-28
forum: Hardware
---

### Post by Bartje on 2009-12-28
Hi all,

I've got a  problem here with an external drive from Medion, it's the HDDrive 2 go ultra speed, of 1,5 TB.

It can be connected using e-sata or usb. I use the usb. At first I formatted the drive in ext4, and I tried it out.

It works, but... after a while it falls asleep when not in use. ubuntu karmic does not show it as 'unmounted' or 'disconnected', it stays visible in nautilus. I even can browse through the directories, but when something that is not read before is double clicked, I get the message that it can't read from source. The only way to revive the drive, is plugging out the power, and starting it up again. 

Then I reformatted the drive to ext3.
Problem persists.

Then I discovered that when starting up the computer with the external drive connected and powered up, it won't start up. Booting hangs before entering grub.

It is very annoying because I've put my music collection on the drive. Rythmbox just hangs when the drive falls a sleep. I guess it falls a sleep because it isn't active, even when rhythmbox is playing, because it reads some songs into memory to not to re-read from the drive continuously.

Probably it has something to do with power management, that automatically puts the drive to sleep, and is not capable of waking it up. I can't test it on e-sata because I don't have the right connector for it.

any suggestions? Tell me if more info is needed.

greets,
Bart

---

### Post by Bartje on 2010-01-10
Nobody? perhaps this post is to much down the list...

---

### Post by tazthecat on 2010-01-30
Same here, You're using ubuntu 9.10 are you?

Switch back to Ubuntu 9.04 this worked for me!

I don't know why they don't fix this, I submitted numerous bug reports, but not even 1 answer.

---

### Post by Ivo Moelans on 2010-01-31
Mine does wake up, but too slow.
My player (gmusicbrowser) gives an error message which disappears when the hard disk finally revives. It's usable but somewhat annoying.
I wonder if this behavior can be changed somehow.

---

### Post by Bartje on 2010-01-31
I've tried fstab options, but nothing helped so far. I still think it has something to do with the usb chip, because it causes boot problems. Even checking memory hangs when starting up having the drive connected.

---

### Post by Bartje on 2010-04-13
After quite some time now, I've decided to try out something, I removed the drive from the casing (was useless anyway) and placed it in another box, also usb connected.

At first it seemed to work properly, and now I can boot the PC with the external drive powered on. That means, in my opinion, that there was a problem with the usb chip on the original casing.

But now there is a different problem, which probably also existed with the original box, but handled differently by Ubuntu because of the different usb-chip.

The drive works, as long as I don't read while writing to it, or the other way round. Playing my music from this drive works, but even when saving an edit of the mp3-tag in Rhythmbox, the drive disappears. 

I've searched the messages, and this is what I get :

```
Apr 13 13:37:03 UbuntuStudio kernel: [23080.900148] usb 1-3: new high speed USB device using ehci_hcd and address 19
Apr 13 13:37:03 UbuntuStudio kernel: [23081.019074] usb 1-3: configuration #1 chosen from 1 choice
Apr 13 13:37:03 UbuntuStudio kernel: [23081.020462] scsi12 : SCSI emulation for USB Mass Storage devices
Apr 13 13:37:08 UbuntuStudio kernel: [23086.021996] scsi 12:0:0:0: Direct-Access     ST315003 41AS                  PQ: 0 ANSI: 2 CCS
Apr 13 13:37:08 UbuntuStudio kernel: [23086.022811] sd 12:0:0:0: Attached scsi generic sg8 type 0
Apr 13 13:37:08 UbuntuStudio kernel: [23086.028640] sd 12:0:0:0: [sdg] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
Apr 13 13:37:08 UbuntuStudio kernel: [23086.029355] sd 12:0:0:0: [sdg] Write Protect is off
Apr 13 13:37:08 UbuntuStudio kernel: [23086.030984]  sdg: sdg1
Apr 13 13:37:08 UbuntuStudio kernel: [23086.060488] sd 12:0:0:0: [sdg] Attached SCSI disk
Apr 13 13:37:09 UbuntuStudio kernel: [23087.222659] EXT4-fs (sdg1): barriers enabled
Apr 13 13:37:09 UbuntuStudio kernel: [23087.278076] kjournald2 starting: pid 13129, dev sdg1:8, commit interval 5 seconds
Apr 13 13:37:09 UbuntuStudio kernel: [23087.278893] EXT4-fs (sdg1): internal journal on sdg1:8
Apr 13 13:37:09 UbuntuStudio kernel: [23087.278898] EXT4-fs (sdg1): delayed allocation enabled
Apr 13 13:37:09 UbuntuStudio kernel: [23087.278902] EXT4-fs: file extents enabled
Apr 13 13:37:09 UbuntuStudio kernel: [23087.407649] EXT4-fs: mballoc enabled
Apr 13 13:37:09 UbuntuStudio kernel: [23087.407674] EXT4-fs (sdg1): recovery complete
Apr 13 13:37:09 UbuntuStudio kernel: [23087.408793] EXT4-fs (sdg1): mounted filesystem with ordered data mode
Apr 13 13:38:08 UbuntuStudio kernel: [23146.821020] usb 1-3: reset high speed USB device using ehci_hcd and address 19
Apr 13 13:38:19 UbuntuStudio kernel: [23157.058019] usb 1-3: reset high speed USB device using ehci_hcd and address 19
Apr 13 13:38:55 UbuntuStudio kernel: [23193.825225] usb 1-3: reset high speed USB device using ehci_hcd and address 19
Apr 13 13:38:56 UbuntuStudio kernel: [23194.359142] usb 1-3: reset high speed USB device using ehci_hcd and address 19
Apr 13 13:38:56 UbuntuStudio kernel: [23194.891146] usb 1-3: reset high speed USB device using ehci_hcd and address 19
Apr 13 13:38:57 UbuntuStudio kernel: [23195.402144] usb 1-3: reset high speed USB device using ehci_hcd and address 19
Apr 13 13:38:57 UbuntuStudio kernel: [23195.812054] sd 12:0:0:0: Device offlined - not ready after error recovery
Apr 13 13:38:57 UbuntuStudio kernel: [23195.812063] sd 12:0:0:0: [sdg] Unhandled error code
Apr 13 13:38:57 UbuntuStudio kernel: [23195.812066] sd 12:0:0:0: [sdg] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Apr 13 13:38:57 UbuntuStudio kernel: [23195.812113] sd 12:0:0:0: [sdg] Unhandled error code
Apr 13 13:38:57 UbuntuStudio kernel: [23195.812115] sd 12:0:0:0: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 13 13:38:57 UbuntuStudio kernel: [23195.812139] usb 1-3: USB disconnect, address 19
Apr 13 13:38:57 UbuntuStudio kernel: [23195.817628] reading directory #9551876 offset 0
Apr 13 13:38:58 UbuntuStudio kernel: [23195.869193] previous I/O error to superblock detected
Apr 13 13:38:58 UbuntuStudio kernel: [23195.890832] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
Apr 13 13:38:58 UbuntuStudio kernel: [23195.890839] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
Apr 13 13:38:58 UbuntuStudio kernel: [23195.890844] EXT4-fs: mballoc: 0 generated and it took 0
Apr 13 13:38:58 UbuntuStudio kernel: [23195.890847] EXT4-fs: mballoc: 0 preallocated, 0 discarded
```

I hope someone knows what's going on, google didn't bring relevant results so far, and there was an issue in bugtracker which could be relevant, but that does not show solutions either :

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746")

If there's someone around here that can help... 

grtz,
Bart

---

