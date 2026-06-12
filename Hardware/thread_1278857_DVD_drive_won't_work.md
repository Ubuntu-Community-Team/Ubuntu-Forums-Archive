---
title: "DVD drive won't work"
date: 2009-09-30
forum: Hardware
---

### Post by loosie on 2009-09-30
Hi, Just bought a new 'no name' brand external CD/DVD burner. It doesn't work at all on Linux - doesn't register, doesn't open. Can anyone tell me what I might need to get it going? TIA

---

### Post by Littleweseth on 2009-09-30
I assume it's a USB device?

Try finding out the USB ID with lsusb, and googling that in conjunction with the word 'linux'. For example :

```

lws@lws-desktop:/etc/apache2$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

You would try googling '1d6b:0002 Linux'. Of course you'd this with the USBID that belongs to the external drive, not my half-baked example ones.

Post back with the output of lsusb, and any information you find out.

- L.

(Edit : I had this same kind of issue with a no-name USB->IDE adapter. LSUSB actually gives you a surprising amount of information in some cases, including manufacturer names that aren't printed on the labeling; my device turned out to be a 'Myson Century '04cf:8818 Myson Century, Inc. USB2.0 to ATAPI Bridge', which helped me track down a website and drivers.)

---

### Post by loosie on 2009-10-01
Thanks! Done the lsusb thing already. Sorry I forgot to include that. The lsusb info appears to be; Bus 001 Device 005: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter  

When I googled 'O5e3:0701 Genesys Logic' Driveragent.com was one of the results. Went into that, but it says Genesys 0701 is an 'optical device'. Would this be right for a dvd drive? Clicking on that gave me a whole list of irrelevant looking products, such as hard drives, storage devices, etc. Does that sound right to you??

adding 'Linux' to the search criteria brings up my post on another forum as the first result! Also a lot of other similar type questions & info that didn't make much sense... altho I am over tired atm.

---

### Post by Littleweseth on 2009-10-01
A DVD drive is indeed an 'optical drive' (it reads a disc using a laser - that's the definition of an optical drive. :) )

It looks like what you have is a generic USB -> IDE adapter that has a generic IDE DVD drive on the end of it. That's not a very useful thing to know, though.

More information digging : try 'sudo tail -f /var/log/syslog' (or everything.log, or dmesg - I don't have an Ubuntu box to hand.) 'tail -f' will output any changes to the end of the log, as they happen; unplug and replug your DVD drive to see what log messages come out.

---

### Post by loosie on 2009-10-01
OK, here's what it gave me... In bold is when disconnecting & reconnecting the drive.

.....desktop:~$ sudo tail -f /var/log/syslog
[sudo] password for xxxx: 
Oct  2 12:41:54 anya-desktop kernel: [ 1390.634851] sd 5:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct  2 12:41:54 anya-desktop kernel: [ 1390.634857] sd 5:0:0:0: [sdb] Sense not available.
Oct  2 12:41:54 anya-desktop kernel: [ 1390.634903] sd 5:0:0:0: [sdb] Write Protect is off
Oct  2 12:41:54 anya-desktop kernel: [ 1390.634908] sd 5:0:0:0: [sdb] Mode Sense: 00 00 00 00
Oct  2 12:41:54 anya-desktop kernel: [ 1390.634912] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Oct  2 12:41:54 anya-desktop hald[2361]: forcibly attempting to lazy unmount /dev/sdb1 as enclosing drive was disconnected
Oct  2 12:41:54 anya-desktop kernel: [ 1390.868151] scsi 5:0:0:0: rejecting I/O to dead device
Oct  2 12:41:54 anya-desktop hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 0
Oct  2 12:41:56 anya-desktop chipcardd[2306]: devicemanager.c: 3373: Changes in hardware list
Oct  2 12:50:02 anya-desktop /USR/SBIN/CRON[4228]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct  2 13:00:01 anya-desktop /USR/SBIN/CRON[4449]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Oct  2 13:00:01 anya-desktop /USR/SBIN/CRON[4464]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct  2 13:01:56 anya-desktop kernel: [ 2593.016186] usb 1-5: USB disconnect, address 4
Oct  2 13:01:59 anya-desktop chipcardd[2306]: devicemanager.c: 3373: Changes in hardware list
Oct  2 13:02:11 anya-desktop kernel: [ 2608.460078] usb 1-5: new high speed USB device using ehci_hcd and address 8
Oct  2 13:02:12 anya-desktop kernel: [ 2608.639936] usb 1-5: configuration #1 chosen from 1 choice
Oct  2 13:02:12 anya-desktop kernel: [ 2608.698980] scsi6 : SCSI emulation for USB Mass Storage devices
Oct  2 13:02:12 anya-desktop kernel: [ 2608.699588] usb-storage: device found at 8
Oct  2 13:02:12 anya-desktop kernel: [ 2608.699594] usb-storage: waiting for device to settle before scanning
[B]Oct  2 13:02:14 anya-desktop chipcardd[2306]: devicemanager.c: 3373: Changes in hardware list
Oct  2 13:02:17 anya-desktop kernel: [ 2613.717883] usb-storage: device scan complete
Oct  2 13:02:17 anya-desktop kernel: [ 2613.721188] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4084N KQ09 PQ: 0 ANSI: 0
Oct  2 13:02:17 anya-desktop kernel: [ 2613.779897] sr1: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Oct  2 13:02:17 anya-desktop kernel: [ 2613.780715] sr 6:0:0:0: Attached scsi CD-ROM sr1
Oct  2 13:02:17 anya-desktop kernel: [ 2613.780877] sr 6:0:0:0: Attached scsi generic sg2 type 5
[/B]

---

### Post by Littleweseth on 2009-10-02
That dmesg output looks fairly normal. Can you try it with a disc in the drive, too?

---

### Post by loosie on 2009-10-03
It just makes farty noises when a disk's in, nothing else. Here's the same 'tail' output with a CD in...

desktop:~$ tail -f /var/log/syslog
Oct  4 09:59:00 anya-desktop kernel: [ 2896.236637] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4084N KQ09 PQ: 0 ANSI: 0
Oct  4 09:59:00 anya-desktop kernel: [ 2896.302451] sr1: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Oct  4 09:59:00 anya-desktop kernel: [ 2896.302657] sr 4:0:0:0: Attached scsi CD-ROM sr1
Oct  4 09:59:00 anya-desktop kernel: [ 2896.302815] sr 4:0:0:0: Attached scsi generic sg2 type 5
Oct  4 10:00:01 anya-desktop /USR/SBIN/CRON[5031]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Oct  4 10:00:01 anya-desktop /USR/SBIN/CRON[5042]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct  4 10:00:10 anya-desktop kernel: [ 2967.112126] sr 4:0:0:0: Device offlined - not ready after error recovery
Oct  4 10:00:10 anya-desktop kernel: [ 2967.112203] sr 4:0:0:0: rejecting I/O to offline device
Oct  4 10:00:10 anya-desktop kernel: [ 2967.112415] usb 1-5: USB disconnect, address 6
Oct  4 10:00:11 anya-desktop chipcardd[2281]: devicemanager.c: 3373: Changes in hardware list

When I first put a disk in it, was looking at 'computer' in a file browser & 'CD RW/DVD RW' came up... momentarily. Clicking on it only gave me 'unable to mount drive' and then not long after that it just disappeared from file browser.

BTW, in case you see another DVD drive above, I've actually put my old internal one in this machine for now. Not ideal tho - it's temperamental & I have to hit it occasionally to get it to open! So I still need to try to get this working.

---

