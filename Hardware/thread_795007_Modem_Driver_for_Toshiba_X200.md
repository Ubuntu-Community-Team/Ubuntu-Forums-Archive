---
title: "Modem Driver for Toshiba X200"
date: 2008-05-15
forum: Hardware
---

### Post by Eskild69 on 2008-05-15
Hi,
I have installed ubuntu 8.04 on my Toshiba X200.
But it does not recognize my softmodem, which I believe is made by Agere.
Where can i found a driver for my modem.
Thanks.

---

### Post by Eskild69 on 2008-05-15
Gentlemen,
below you see what Scanmodem listed. 
Anyone who can help mke getting my modem working ?


	 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-16-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Your contry's local Linux experts
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html). 
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
 scanModem update of:  2008_05_02

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 04f2:b008 Chicony Electronics Co., Ltd 
 ID 1532:0007  
 ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader

USB modems not recognized
For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:284b	1179:ff00	Audio device: Intel Corporation 82801H 

 Modem interrupt assignment and sharing: 
 22:        408        395   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   33.910819] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   33.910841] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.
 PCI slot 00:1b.0 has a High Definition Audio Card

The ALSA verion is 1.0.15
The modem cards detected by "aplay -l"  are:


The /proc/asound/pcm file reports:
-----------------------
00-02: ALC268 Analog : ALC268 Analog : capture 1
00-01: ALC268 Digital : ALC268 Digital : playback 1
00-00: ALC268 Analog : ALC268 Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf7600000 irq 22
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 00:1b.0:
	Modem chipset  detected on
CLASS="Class 0403: 8086:284b"
NAME="Audio device: Intel Corporation 82801H "
SUBSYS=1179:ff00
PCIDEV=8086:284b
IRQ=22
HDA=8086:284b
SOFT=8086:284b.HDA
CodecArchived=11c11040
ArchivedChip=0x11c11040
IDENT=11c11040_Not_supported.

 For candidate modem in:  00:1b.0
   Class 0403: 8086:284b Audio device: Intel Corporation 82801H 
      Primary device ID:  8086:284b
    Subsystem PCI_id  1179:ff00 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 0x11c11040, residing on 1179:ff00 lacks support from LSI/Agere.
                        
      

Support type needed or chipset:	11c11040_Not_supported.

Read InfoGeneral.txt about alternative hardware

---

### Post by Eskild69 on 2008-05-18
Anyone, pls help....

---

### Post by Perkins on 2008-07-24
If yours is like mine, it's a Toshiba Softmodem made by Agere Systems.  On mine it shows up as serial82801.  You *might* be able to make it work with sl-modem-daemon.  No promises though, it's full of bugs and I haven't gotten it to function yet.

---

### Post by Psychoscorpic on 2008-08-19
> **Eskild69 said:**
> Anyone, pls help....

I have the same stupid modem in the Sahara Cel1 I just bought. Managed to get the driver loaded (agrsm-ubuntu8.04.1-2.6.24-19-generic) following the text tutorial that came with it.
Problem is, as soon as I rebooted, it no longer saw the thing, and I haven't been able to get it visible again.

Next try is to reinstall the driver from scratch - seems something overwrote something on shutdown (a lot of connectivity scripting seems to run - I have an idea it's left over from when I connected via our work broadband connection to update Ubuntu to 8.04.1)

Anyone with more help?

EDIT: 
OK - just reinstalled the driver, and set things up.
WVDIAL got stuck, but I went back to my trusty PPP (sudo pppconfig) and it dialed out (no dialing sound, but, after leaving it for a few seconds, I was able to connect to my gmail account!)

The acid test will be if all this still works after a reboot.

EDIT:
Nope. Loses it after rebooting. Will post solution here when I find it (or if someone else finds it)

---

### Post by _sandman_ on 2008-08-31
Psychoscorpic, we have the same problem. Agere modem driver seems to be un-installed after rebooting. I still have no clue how to resolve it, at first i was a bit satisfied after the first attempt upon installation, everything seems fine but the problem goes after the reboot. when ever I'd like to connect via modem, i just need to re-install it. man, that was a waste of time. Please don't hesitate to post if you find a better solution, and I'll do the same.

---

### Post by Psychoscorpic on 2008-09-02
Hi _sandman_

Resorted to writing a little script to automate this process a little.
Doesn't eliminate the need to reboot each time, but at least saves having to type it all out each time.

```
#!/bin/sh
sudo modprobe agrmodem
sudo modprobe agrserial
sudo ln -s /dev/ttyAGS3 /dev/ttySAGR
sudo ln -s /dev/ttyAGS3 /dev/modem
sudo wvdialconf /etc/wvdial.conf
```

I just double click and choose Run in Terminal after booting.
If it displays (very quickly) that it finds the modem, then a normal "wvdial" in Terminal works.
If it fails, then I reboot and run it again - works that time.

Not very elegant, but the best I've managed so far.:neutral:

---

