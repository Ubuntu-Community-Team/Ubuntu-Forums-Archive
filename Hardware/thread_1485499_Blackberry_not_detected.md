---
title: "Blackberry not detected"
date: 2010-05-16
forum: Hardware
---

### Post by ezm on 2010-05-16
I am trying to connect my blackberry to my Ubuntu computer via USB.  It seems the computer is aware that I have plugged in the device.  When I run dmesg I saw the following messages: 

> 
[10732.484149] usb 2-1: new high speed USB device using ehci_hcd and address 5
[10732.618290] usb 2-1: configuration #1 chosen from 1 choice
[10732.625770] scsi5 : SCSI emulation for USB Mass Storage devices
[10732.626045] usb-storage: device found at 5
[10732.626050] usb-storage: waiting for device to settle before scanning
[10732.836712] usb 2-1: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1
[10733.948158] usb 2-1: reset high speed USB device using ehci_hcd and address 5


But even though there are no obvious errors here, a link to the device is nowhere to be found.  Any hints?

---

### Post by Aura21 on 2010-05-30
Hey, i have the same problem...

I can back up my Blackberry using ***"barrybackup"*** no problem, my laptop will detect it...

The only problem is, it wont detect my BB as a storage device.

Because of this, i cant transfer any pictures or MP3`s...

Well, i hope someone have a solution for this issue...
:guitar:

---

### Post by tarverator on 2010-05-31
My Blackberry 8220 is doing the same thing, and I think it started when I upgraded my distribution to lucid.  I plug in the USB cable, but no "drive" appears on the desktop where I expect it to appear as an icon.

---

### Post by Hieronymus Josch on 2010-07-21
I'm in the same boat with my 9530.  I can back mine up with Barry as well but I'm unable to access it as a storage device.  I used to all the time in 9.10.  This is absolutely a problem that has come up with the new distro.  If I don't see a solution soon, I'll have to go back to 9.1.  I'm getting pretty frustrated.

---

### Post by Hieronymus Josch on 2010-07-22
Nearly 250 views and not one suggestion.  This isn't looking good.  I'm going to file a bug report and see what comes of it.

---

### Post by Intel91 on 2010-07-22
You should hear what happens to my Blackberry Storm when I plug it up to my computer.... It completely reboots the phone.... continuously...... without end. 

I haven't taken any care to fix it because I really have no use for plugging my bb into linux, can't do a reliable firmware update like that, and my syncing is all wireless.

---

### Post by imho74 on 2011-06-20
I think *bcharge* from barry is the problem here

```
[10732.836712] usb 2-1: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1
[10733.948158] usb 2-1: reset high speed USB device using ehci_hcd and address 5
```

Do you use 0.15 from Lucid repos? I had the same problem with this version.

I removed it

```
sudo apt-get remove barrybackup-gui opensync-plugin-barry barry-util libbarry0 libbarry-dev 
```

and installed [_Barry 0.17.1 for Ubuntu 10.04_]("http://sourceforge.net/projects/barry/files/barry/barry-0.17.1/ubuntu1004/") with libbarry0, barry-util, barrybackup-gui, libbarry-dev and [_opensync-plugin-barry_0.17-1_]("http://sourceforge.net/projects/barry/files/barry/barry-0.17.1/01-rebuild/ubuntu1004/"). 

It works like a charme. ;)

---

### Post by nomko on 2011-06-20
> **imho74 said:**
> 

```
sudo apt-get remove barrybackup-gui opensync-plugin-barry barry-util libbarry0 libbarry-dev 
```and installed [_Barry 0.17.1 for Ubuntu 10.04_]("http://sourceforge.net/projects/barry/files/barry/barry-0.17.1/ubuntu1004/") with libbarry0, barry-util, barrybackup-gui, libbarry-dev and [_opensync-plugin-barry_0.17-1_]("http://sourceforge.net/projects/barry/files/barry/barry-0.17.1/01-rebuild/ubuntu1004/"). 

It works like a charme. ;)

I think the barry-util tool is a command line tool??? What about the barrybackup-gui? Is that a command line tool as well??

---

### Post by imho74 on 2011-06-30
The command ```
barrybackup
``` launches a GUI (that doesn’t appear anywhere in my Applications menu) that lets you back up your device databases. See also [http://thelinuxexperiment.com/tag/barrybackup/]("http://thelinuxexperiment.com/tag/barrybackup/")

---

