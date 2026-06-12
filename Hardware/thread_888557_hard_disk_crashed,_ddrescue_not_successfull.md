---
title: "hard disk crashed, ddrescue not successfull"
date: 2008-08-13
forum: Hardware
---

### Post by tikey on 2008-08-13
Hello,

I have an 2.5" harddisk (fat32) from a laptop from which I'm trying to recover the data. The laptop was not working anymore, so I got out the harddisk and plugged it into my kubuntu-laptop via usb.

Trying dosfsck gave me the following:
```
sudo dosfsck /dev/sdd
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Got 0 bytes instead of 512 at 0

```

So I tried dd, to copy the data to a file, which wasn't successfull, either. Searching the forum here I found ddrescue, which I tried without success. Using the simple ddrescue command gave me the following after less than a second.
```
sudo ddrescue -r1 -v /dev/sdd /home/tikey/ablage/ImageDisk.dd /home/tikey/ablage/ImageDisk.log


About to copy an undefined number of Bytes from /dev/sdd to /home/tikey/ablage/ImageDisk.dd
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 hard blocks
Hard block size: 512 bytes
Max_retries: 1    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:         0 B,  errsize:       0 B,  current rate:        0 B/s
   ipos:         0 B,   errors:       0,    average rate:        0 B/s
   opos:         0 B

```

So I tried to skip the beginning of the harddrive, which after running for a whole night gave me the following
```
sudo ddrescue -r1 -v --input-position=512 /dev/sdd /home/tikey/ablage/ImageDisk1.dd /home/tikey/ablage/ImageDis1.log


About to copy an undefined number of Bytes from /dev/sdd to /home/tikey/ablage/ImageDisk1.dd
    Starting positions: infile = 512 B,  outfile = 512 B
    Copy block size: 128 hard blocks
Hard block size: 512 bytes
Max_retries: 1    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:    920 TB,  errors:       1
Current status
rescued:         0 B,  errsize:    921 TB,  current rate:        0 B/s
   ipos:   921278 GB,   errors: 17780860,    average rate:        0 B/s
   opos:   921278 GB
Interrupted by user

```

Does anyone have an idea what I could do? Am I just doing something completly wrong or does it look like there's just no chance to get the data back?
It's the first time that I'm trying to recover data from a harddisk, so I'd really appreciate any suggestions. I also searched the forum but I didn't find anything. Maybe I was just looking in the wrong places. So any suggestions where I could start another round of searching would also be greatly appreciated.

Thanks
  Thomas

---

### Post by evets25 on 2008-08-13
This might be a silly suggestion, but perhaps you're making this more complicated than it needs to be. Have you tried simply mounting the fat32 partition and reading it the normal way? Also, what does gparted or any other partitioning program tell you about the drive?

---

### Post by tikey on 2008-08-13
Indeed, I had not tried to mount it. But when I did so now, it showed me
```
 sudo mount -t vfat /dev/sdd /media/test/
mount: /dev/sdd: can't read superblock

```

When I start gparted, the device is not even listed. I have the following in /dev/disk/by-id:
```
ls /dev/disk//by-id/ -la
total 0
drwxr-xr-x 2 root root 180 2008-08-13 16:02 .
drwxr-xr-x 5 root root 100 2008-08-12 23:05 ..
lrwxrwxrwx 1 root root   9 2008-08-12 10:29 ata-WDC_WD1200VE-00KWT0_WD-WXE207E94420 -> ../../sda
lrwxrwxrwx 1 root root  10 2008-08-12 10:29 ata-WDC_WD1200VE-00KWT0_WD-WXE207E94420-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-08-12 10:29 ata-WDC_WD1200VE-00KWT0_WD-WXE207E94420-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2008-08-12 10:29 scsi-1ATA_WDC_WD1200VE-00KWT0_WD-WXE207E94420 -> ../../sda
lrwxrwxrwx 1 root root  10 2008-08-12 10:29 scsi-1ATA_WDC_WD1200VE-00KWT0_WD-WXE207E94420-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-08-12 10:29 scsi-1ATA_WDC_WD1200VE-00KWT0_WD-WXE207E94420-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2008-08-13 15:57 usb-Initio_INIC-1511_00000000000000000-0:0 -> ../../sdd

```
and sudo fdisk -l /dev/sdd just returns with no output!

---

### Post by evets25 on 2008-08-13
I just re-read your first post, and I noticed that you mentioned you have it plugged in to your laptop via USB. I presume this involves some sort of IDE-to-USB adaptor? Perhaps this is where the problem lies. 

I mean, it sounds to me as if it is breaking down somewhere between the steps where it detects that a device is attached, and that it's a hard drive, but when it goes to read information from it it fails. Perhaps the adaptor itself is the problem, not the hard drive. 

SO... try plugging it into a regular old desktop, if you have one available, via IDE (directly), and then boot from the Ubuntu live CD and see if you can mount the drive. If you can, then you know the adaptor is the problem, if not, then you're back to other troubleshooting steps. 

Also, it might be helpful to post the output of this command while the drive is plugged in to your laptop via usb: 
```
lsusb
```

---

### Post by tikey on 2008-08-13
Thanks for your help, unfortunately it doesn't solve the problem. After you suggested that it might be the adapter I tried the following:

I got a new adapter and another 2,5"HDD (one which I know is working).
This HDD is working on my kubuntu-machine with both adapters without problems.
The problematic harddrive is NOT working with both adapters. With the first adapter it is still the same problem as I described. With the second adapter it is even worse. dmesg doesn't show anything and lsusb doesn't show anything either.

Any other ideas?

---

### Post by tikey on 2008-08-13
I tried one more adapter. This time I used a 3,5" external drive. I replaced the harddrive and plugged in the 2,5" using a IDE adapter. Now dmesg gives me the following:

```
[ 4945.933539] usb 4-1: new high speed USB device using ehci_hcd and address 12
[ 6594.712478] usb 4-1: configuration #1 chosen from 1 choice
[ 6594.735766] scsi9 : SCSI emulation for USB Mass Storage devices
[ 6594.742310] usb-storage: device found at 12
[ 6594.742320] usb-storage: waiting for device to settle before scanning
[ 6595.985389] usb-storage: device scan complete
[ 6601.589074] usb 4-1: USB disconnect, address 12
[ 6601.589325] scsi 9:0:0:0: Device offlined - not ready after error recovery

```

Unfortunately I have no idea what it means but I'll try to do some research. If anyone has an idea how to solve this, please let me know!

Thanks

Edit: I tried to remove ehci_hcd
```
sudo modprobe -r ehci_hcd
``` but still without success. Now dmesg gives me:
```
[ 7263.725600] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 7279.559570] usb 1-1: device descriptor read/64, error -110
[ 2735.801741] usb 1-1: device descriptor read/64, error -110
[ 2736.017560] usb 1-1: new full speed USB device using uhci_hcd and address 6
[ 7314.238213] usb 1-1: device descriptor read/64, error -110
[ 7334.140182] usb 1-1: device descriptor read/64, error -110
[ 2750.423311] usb 1-1: new full speed USB device using uhci_hcd and address 7
[ 7348.456412] usb 1-1: device not accepting address 7, error -110
[ 7348.568395] usb 1-1: new full speed USB device using uhci_hcd and address 8
[ 7362.926878] usb 1-1: device not accepting address 8, error -110

```

---

### Post by ioliver on 2008-09-02
Your disk looks very bad, but they can get themselves into these states and then recover IMO.

Let the drive cool down. Maybe even chill it a little but avoid dew/frost situations!

Plug it in and check that the dmesg output is sane.

Use ddrescue the first time with the -n switch. This will immediately move on if it hits any errors. You can also use -s to set the maximum size and -i to skip parts of the disk. The -s is only really needed if ddrescue can't find the size of the drive, which is bad in itself!

If the drive gets into a bad state, stop ddrescue, disconnect the drive and let it cool down, and then try again.

After the run with -n you will still have loads of errors. You can then try again without -n. Then have another run with retries set to 2-3.

Good luck!

Ian

---

### Post by ioliver on 2008-09-02
Oh, and you can also use hdparm to turn off disk read ahead. And newer versions of ddrescue support direct access. It's easy to build this from source - instructions on request.
Ian

---

### Post by marioitalo on 2008-10-01
I found a solution to that problem (apparently this is about the time needed to the device wake-up):
At /etc/modprobe.d/options I added the line:
options scsi_mod inq_timeout=20
Then I tried to unload and load the module(scsi_mod), but didn't work, because this option was in initrd file. So I reinstalled the package linux-image-* what forced the system to make a new initrd file and use the new configuration (of course there is a better way to do that but I didn't want to search how to), then, after a reboot, voilá, the pen drive was back to life.:popcorn:
I hope this help someone.

---

### Post by bektom on 2008-11-20
Hey,

I do not know if you still have that problem, but I had just the same and for me it came out that the hardrive got half disattached from the integrated part which has the usb connection.
I found this when I gave up all other trials and get rid of the cover by screwing out all the screws. I simply pushed it back and now it works perfectly.

Good luck!

---

