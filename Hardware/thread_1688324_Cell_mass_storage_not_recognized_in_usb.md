---
title: "Cell mass storage not recognized in usb"
date: 2011-02-15
forum: Hardware
---

### Post by asphixmx on 2011-02-15
I have a Blackberry. I used to connect it via usb to transfer my pics & mp3s. Suddenly, it is not recognized anymore. When I do a "lsusb", it appears my RIM phone on the list, but it is not mounted; it doesn't appear in /media either. No problem in ms windows, I can use it. But I hate to switch to windows just to transfer my pics & music.
Any idea?
Thanks!

---

### Post by jerrrys on 2011-02-17
don't know how to fix that, but just a though; maybe its time to move on to 10o4

---

### Post by asphixmx on 2011-02-17
Thanks for your response Jerry. I have Lucid, 10.04. I will see why it says I have 8.04 :P

---

### Post by CharlesA on 2011-02-17
> **asphixmx said:**
> Thanks for your response Jerry. I have Lucid, 10.04. I will see why it says I have 8.04 :P
It's set in yer profile, [here]("http://ubuntuforums.org/profile.php?do=editprofile").

Is the device shown when you run this:

```
sudo fdisk -l
```

---

### Post by asphixmx on 2011-02-17
Profile updated, thanks.
Ok, lsusb shows:

Bus 008 Device 002: ID 045e:009d Microsoft Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0e5e:6622  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0fca:8004 Research In Motion, Ltd. 
Bus 002 Device 002: ID 054c:01bd Sony Corp. MRW62E Multi-Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

(Reserch In Motion, Ltd. is the cel phone)

sudo fdisk -l shows only sda, sdb & sdc. Those are my 3 hard disks. Nothing more.
Any idea?

---

### Post by CharlesA on 2011-02-17
Well it's shown in lsusb, so the OS sees it, but it doesn't see it as a drive. Is there a setting you need to pick on the phone it self to make it a mass storage device?

---

### Post by jerrrys on 2011-02-17
nevermind

---

### Post by asphixmx on 2011-02-17
Charles, yes, the phone asks to set it up like mass storage, I answer yes to that on the phone when I plug it in the usb (even now). Few weeks ago it worked ok and the Lucid saw the "Blackberry" SD card... suddenly it doesn't anymore. Maybe after an update, don't know.
Jerry: I tried that too, boot the Ubuntu with the phone already plugged in. Same result. On the other side, I can't back one kernel version because I always delete de old ones.

I thought it could be de SD card..but in windows works ok; besides I connected my girlfriend's phone (same model as mine) and same results with her phone.

---

### Post by CharlesA on 2011-02-17
Sounds like maybe an update messed communication with the phone. Does it work if you boot off a livecd?

---

### Post by jerrrys on 2011-02-17
will **dmesg | tail** throw any light on it ?

---

### Post by asphixmx on 2011-02-17
Charles, using LiveCD = everything works OK

Jerry, the output to dmesg | tail is:

[  449.149055] usb-storage: waiting for device to settle before scanning
[  449.683368] usb 2-4: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1
[  450.533933] usb 2-4: USB disconnect, address 7
[  463.440521] usb 2-4: new high speed USB device using ehci_hcd and address 8
[  463.573046] usb 2-4: configuration #1 chosen from 1 choice
[  463.590882] scsi13 : SCSI emulation for USB Mass Storage devices
[  463.591007] usb-storage: device found at 8
[  463.591009] usb-storage: waiting for device to settle before scanning
[  463.789791] usb 2-4: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1
[  469.896022] usb 2-4: reset high speed USB device using ehci_hcd and address 8

---

