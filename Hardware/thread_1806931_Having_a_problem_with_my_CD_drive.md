---
title: "Having a problem with my CD drive"
date: 2011-07-18
forum: Hardware
---

### Post by JPurdy on 2011-07-18
I'm not sure how far back this problem goes back - I don't burn media that often and I had previously assumed the problem was with the media, but after several attempts, I'm thinking it's something with my CD drive. I reduced my use case to something simple - I'm trying to burn one 400 MB file using a CD-R disc and Brasero (maximum speed, creates image before burning, just one copy, etc).

It goes through the burning process and then says "Success", but it has problems mounting the newly-minted CD afterwards. My syslog contains these error messages:

```
Jul 18 11:18:44 jason-desktop kernel: [501959.813076] sr 2:0:0:0: [sr0] Unhandled sense code
Jul 18 11:18:44 jason-desktop kernel: [501959.813084] sr 2:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 18 11:18:44 jason-desktop kernel: [501959.813093] sr 2:0:0:0: [sr0]  Sense Key : Medium Error [current] 
Jul 18 11:18:44 jason-desktop kernel: [501959.813102] sr 2:0:0:0: [sr0]  Add. Sense: L-EC uncorrectable error
Jul 18 11:18:44 jason-desktop kernel: [501959.813112] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
Jul 18 11:18:44 jason-desktop kernel: [501959.813128] end_request: I/O error, dev sr0, sector 0
Jul 18 11:18:44 jason-desktop kernel: [501959.813138] Buffer I/O error on device sr0, logical block 0
```

Then it sticks on *Creating image checksum* until I hit **Cancel**. After I hit cancel, I get a pop-up that says:

> **Please eject the disc from "LITE-ON DVDRW SOHW-1633S" manually.**
The disc could not be ejected though it needs to be removed for the current operation to continue.

So I eject it manually and re-insert it and nothing. The alert message pop-up is still there and the new CD doesn't mount. I took it to another computer (Mac) and it just spits it back out.

Here is the information from running: [FONT="Courier New"]$ sudo lshw -C disk[/FONT]

```
  *-cdrom                 
       description: DVD writer
       product: DVDRW SOHW-1633S
       vendor: LITE-ON
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: BS0H
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
```

My system used to be able to burn CD's & DVD's with no problem. My guess is that one of my system upgrades knocked something out of whack.

I'm currently running 11.04 and please let me know what other information I can provide.

Thanks!

---

