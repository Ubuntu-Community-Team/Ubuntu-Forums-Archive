---
title: "CD Burning not working"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by xubu_caapn on 2007-07-11
Hey everyone, the title says it all! :) I can't burn CDs or DVDs, all the burning programs I've tried (K3b, Graveman, xfburn) tell me that my drive doesn't even have the capability (it does, of course). I burnt restore discs of Windows when this laptop shipped so that's not the issue. I'd post some terminal outputs but I don't know where to start.

---

### Post by dabl on 2007-07-11
Try "Administration">"Preferences">"Hardware Info" (or something like that) -- it shows all your devices.  Does it show your CD/DVD drive correctly?

---

### Post by xubu_caapn on 2007-07-11
I'm sorry, I forgot to mention I'm on Xubuntu. Does anyone know the equivalent of this?
I also failed to mention that this has happened on Debian and Zenwalk as well!

---

### Post by xubu_caapn on 2007-07-11
well, this is the relevant output of lshw:

```
           *-cdrom
                description: DVD reader
                product: DVD-ROM GDR8087N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                capabilities: removable audio dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom

```

i don't what other info i could provide.

---

### Post by xubu_caapn on 2007-07-11
I found the following on an installation guide of the thinkpad t60, which is the system i'm working on. can anyone provide some clarification with what he says, and if this sounds like a good procedure to get this working?

UPDATE: Kernel 2.6.19 and higher (gentoo sources) The dvd burner has an ide interface which is directly connected to the SATA controller.

You have to remove completely ide support
```

Device Drivers --->
ATA/ATAPI/MFM/RLL support --->
< > ATA/ATAPI/MFM/RLL support

```
and add SATA support (SATA, AHCI and the Intel sata driver).

Then add the following options to grub to your kernel(sata in the kernel and not as modules):

```
noprobe=/dev/hdc libata.atapi_enabled=1 
```

so that it looks like that:
```

title Gentoo Linux 2.6.19-gentoo-r5
root (hd0,0)
kernel /boot/kernel-2.6.19-gentoo-r5 root=/dev/sda2 vga=0x31B noprobe=/dev/hda noprobe=/dev/hdc libata.atapi_enabled=1 udev
```

---

### Post by ramjet_1953 on 2007-07-12
Copy and paste this command into a terminal:

wodim --devices

It will list your CD/DVD devices and tell you what read/write permissions that youi have.

Post the output back to this forum.

Regards,
Roger :cool:

---

### Post by xubu_caapn on 2007-07-12
```
0    dev='/dev/sr0'   rwrw-- :  'HL-DT-ST'  'DVD-ROM GDR8087N'

```

---

### Post by xubu_caapn on 2007-07-15
does anyone know what to do from here?

---

### Post by BoGs on 2007-07-15
Sounds like you have the same issue I am having with my burner -- I also have an open topic in this forum.... :S

---

### Post by ramjet_1953 on 2007-07-16
Go into k3b and navigate to [COLOR="Blue"]Settings>Configure K3b[/COLOR]

Click on the [COLOR="Blue"]Devices[/COLOR] icon in the left panel.

Is your burner listed?

If not, click on the [COLOR="Blue"]Refresh[/COLOR] button.

Does it show up now?

If not click on the [COLOR="Blue"]Add Device[/COLOR] button and add your burner manually /dev/sr0

Regards,
Roger :cool:

---

### Post by xubu_caapn on 2007-07-16
I don't want to use K3b, but I added the device in Graveman. It identified it only as a DVD reader, not writer.

---

### Post by xubu_caapn on 2007-07-17
i'm desperate! does anyone know what to do?

thank you

---

### Post by xubu_caapn on 2007-07-18
anyone? There are so many distros I want to try, and the DVD burner is preventing this! :(

---

### Post by xubu_caapn on 2007-07-20
bump.

---

### Post by xubu_caapn on 2007-07-20
```
brandon@brandon-laptop:/$ cdrecord dev=/dev/sr0 /brandon/wolvix.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-ROM GDR8087N'
Revision       : '1.01'
Device seems to be: Generic mmc2 DVD-ROM.
```

---

### Post by xubu_caapn on 2007-07-22
i've looked for help in irc as well, to no avail. this doesn't seem like a complex problem. can anyone help me?

---

### Post by xubu_caapn on 2007-07-24
can anyone help me?

---

### Post by kkinder on 2008-05-18
I have this problem too. Does anyone have a solution? It's quiet lame because it worked up until 7.10 for me.

---

