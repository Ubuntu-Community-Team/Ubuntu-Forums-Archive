---
title: "Laserjet 6L connection via USB not detected"
date: 2010-03-05
forum: Hardware
---

### Post by Colin@oxford on 2010-03-05
I have read various threads around here and am having no luck reaching my LaserJet 6L printer connected via a newly-acquired USB->printer port cable.  hp-setup does not detect it.  If I use Ubuntu's printer setup to force it to be at parallel:/dev/usb/lp0 and attempt to print, I get a "not connected" status.

Is there any way that I can test the cable?  Or are there any other suggestions for getting the computer to talk to the printer?

---

### Post by colourfullegume on 2010-03-24
After banging my head against my screen until it bled, getting advice from many forum users, and searching and searching until my eyes grew red, I have some tips which I can share:

1. First check whether your cable is detected by running the following in a terminal both with and without the cable plugged in, and see if anything changes.  If there is no change, the cable is probably not being detected.  Note that the printer MUST be switched on when you do this:

[B]sudo lsusb
[/B]
Some people get a line that gives the printer correctly named, others get the name of the chip in the cable, others (like me) just get **Unknown**, e.g., 

Bus 001 Device 012: ID 1a86:7584 Unknown 

2. If step 1 works, continue to this step; if it doesn't I can't help further.  Check that you have a file called /dev/usb/lp0 and a link to it called /dev/usblp0.  You can check this in a terminal with these commands:

[B]ls -l /dev/usb/lp0
ls -l /dev/usblp0[/B]

They should return something like this:
crw-rw---- 1 root lp 180, 0 2010-03-24 10:39 /dev/usb/lp0
and
lrwxrwxrwx 1 root root 7 2010-03-24 10:39 /dev/usblp0 -> usb/lp0
respectively

3. If that is all OK, add the printer.  For example, in GNOME, choose System > Administration > Printing > New.  When asked to select a device, choose **Other** and type as the URI, **parallel:/dev/usblp0**  then continue with the rest of the printer installation as normal.

---

### Post by jpl888 on 2010-03-24
I bought one of these cables the other day.

In Lucid all I did was plug the cable in and my HP Laserjet 6P was detected and started working straight away.

Clearly a YMMV moment.

---

### Post by Colin@oxford on 2010-03-24
Thanks for your ideas.  Unfortunately they fail at every stage with me :(

sudo lsusb gives:
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 09ef:3604 Xitel 
Bus 003 Device 003: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
with or without the printer plugged in.

And neither of the dev directories exists.

Maybe I should just use this smiley:  ](*,) and then find another route.

---

### Post by jpl888 on 2010-03-24
This is my syslog output after plugging the cable in:-```
Mar 24 12:49:50 tux kernel: [89585.480027] usb 7-1: new full speed USB device using uhci_hcd and address 5
Mar 24 12:49:50 tux kernel: [89585.675400] usb 7-1: configuration #1 chosen from 1 choice
Mar 24 12:49:50 tux udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0
Mar 24 12:49:50 tux udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7/7-1
Mar 24 12:49:50 tux udev-configure-printer: Device vendor/product is 067B:2305
Mar 24 12:49:50 tux kernel: [89585.688396] usblp0: USB Bidirectional printer dev 5 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
Mar 24 12:49:50 tux udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/usb/lp0
Mar 24 12:49:50 tux udev-configure-printer: failed to claim interface
Mar 24 12:49:50 tux udev-configure-printer: failed to claim interface
Mar 24 12:49:50 tux udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 24 12:49:50 tux udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7/7-1
Mar 24 12:49:50 tux udev-configure-printer: MFG:Hewlett-Packard MDL:HP LaserJet 6P SERN:- serial:
Mar 24 12:49:51 tux kernel: [89586.891696] usb 7-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Mar 24 12:49:53 tux udev-configure-printer: URI matches without serial number: usb://HP/LaserJet%206P
Mar 24 12:49:53 tux udev-configure-printer: No serial number URI matches so using those without
Mar 24 12:49:53 tux udev-configure-printer: Queue ipp://localhost:631/printers/HP-LaserJet-6P-2 has matching device URI
Mar 24 12:49:53 tux udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/HP-LaserJet-6P-2
```

This is my lsusb:-```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 005: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 1410:1450 Novatel Wireless 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05ca:180c Ricoh Co., Ltd 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

It's important to note that if I plugged the cable in before the printer was switched on the detection didn't work.

It also appears we have different cables, do you know whether yours is the Xitel of the Pixart Imaging in your lsusb output?

---

### Post by jpl888 on 2010-03-24
This is what I get in Karmic:-

```
Mar 24 12:59:30 bernadette-laptop kernel: [   78.217545] usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
Mar 24 12:59:30 bernadette-laptop kernel: [   78.217625] usbcore: registered new interface driver usblp
Mar 24 12:59:30 bernadette-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/usb/lp0
Mar 24 12:59:30 bernadette-laptop udev-configure-printer: failed to claim interface
Mar 24 12:59:30 bernadette-laptop udev-configure-printer: failed to claim interface
Mar 24 12:59:30 bernadette-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 24 12:59:30 bernadette-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1
Mar 24 12:59:30 bernadette-laptop udev-configure-printer: MFG:Hewlett-Packard MDL:HP LaserJet 6P SERN:- serial:
Mar 24 12:59:31 bernadette-laptop kernel: [   79.612700] usb 2-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Mar 24 12:59:33 bernadette-laptop udev-configure-printer: URI matches without serial number: usb://HP/LaserJet%206P
Mar 24 12:59:33 bernadette-laptop udev-configure-printer: No serial number URI matches so using those without
Mar 24 12:59:33 bernadette-laptop udev-configure-printer: About to add queue for usb://HP/LaserJet%206P
Mar 24 12:59:34 bernadette-laptop udev-add-printer: add_queue: URIs=['usb://HP/LaserJet%206P']
Mar 24 12:59:53 bernadette-laptop udev-add-printer: PPD: drv:///hpijs.drv/hp-laserjet_6p-hpijs.ppd; Status: 0
Mar 24 12:59:53 bernadette-laptop udev-add-printer: HP LaserJet 6P: Checking whether plugin is needed
```

---

### Post by jpl888 on 2010-03-24
BTW the CUPS+Gutenprint driver prints much faster than HPIJS for me.

---

### Post by Kevinator on 2010-03-24
> **Colin@oxford said:**
> And neither of the dev directories exists.


That suggests usblp is not loaded (check by running lsmod). I think it should get loaded automatically unless it is blacklisted, so try this:

grep -r usblp /etc/modules /etc/modprobe.d/

If that locates a blacklist entry, you'll need to remove it. Loading usblp (either with mobprobe or by unplugging/replugging the printer) should at least get you as far as having the /dev/usblp0 and /dev/usb/lp0 entries. After that, run this to see if CUPS detects the printer:

lpinfo -v

---

### Post by Colin@oxford on 2010-03-25
jpl888:
> 
It also appears we have different cables, do you know whether yours is the Xitel of the Pixart Imaging in your lsusb output?


I have no idea, but since these appear even when the cable is not connected, I assume it is neither.

lsmod | grep usb

gives:
```

snd_usb_audio          84224  2 
snd_usb_lib            16284  1 snd_usb_audio
snd_hwdep               7200  2 snd_usb_audio,snd_hda_codec
snd_rawmidi            22176  2 snd_usb_lib,snd_seq_midi
snd_pcm                75296  5 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    59204  22 snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
usb_storage            52768  0 
usbhid                 38208  0 

```

grep -r usblp /etc/modules /etc/modprobe.d/

gives nothing.

Duff cable?

---

### Post by Kevinator on 2010-03-25
It's entirely possible that I'm wrong about usblp being loaded automatically in this case, so don't take it as a sign that the cable is broken. You can load usblp manually with:

sudo modprobe usblp

And you can cause it to be loaded on boot by adding "usblp" to /etc/modules.

Once you get the module loaded, check for detected printers with:

lpinfo -v

If it's not detected then I'm not sure what that means, but you might still be able to use the parallel:/dev/usb/lp0 trick.

---

### Post by Colin@oxford on 2010-04-04
Running
```

sudo modprobe usblp

```
Now shows
```

usblp                  12636  0 

```
at the top when I use lsmod | grep usb

So now usblp is loaded, but I still have no /dev/usblp0 or /dev/usb/lp0 entries

```

$ ls /dev/usb*
/dev/usbmon0  /dev/usbmon2  /dev/usbmon4  /dev/usbmon6
/dev/usbmon1  /dev/usbmon3  /dev/usbmon5  /dev/usbmon7

```

---

### Post by sola on 2010-04-04
@JP888

What kind of cable do you have? 

Is there some manufacturer name or type code on it?

---

### Post by Colin@oxford on 2010-04-05
Unfortunately not.  It just says "USB Parallel Printer cable".  But until I can see the /dev entries, I cannot be certain that the cable is even being examined.

---

