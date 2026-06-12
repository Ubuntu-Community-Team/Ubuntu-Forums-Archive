---
title: "USB C hub dropping USB peripherals"
date: 2020-05-13
forum: Hardware
---

### Post by ridagstran on 2020-05-13
Hey everyone, I'm having a worsening issue whereby my USB C dock will randomly cause my keyboard and mouse to go unresponsive.
I'm new to Linux, so please forgive any stupid noob stuff. I'll do my best to explain the issue concisely.

System:
[LIST]
[*]Dell XPS 13 9350
[*]Ubuntu 20.04 LTS
[*]Auker CB-C71 (USB C hub)
[*]Das Prime 13 (keyboard)
[*]Logitech M510 (wireless mouse)
[/LIST]

Symptoms:
[LIST]
[*]KB+M are usually unresponsive at system startup
[*]At startup, DAC (Scarlett Solo) mounts and unmounts multiple times. It remains powered but is not recognized until unplug and replug at the dock (dock remains connected).
[*]At random times, my KB lights will flicker, then suddenly both KB+M are unresponsive until dock unplug and replug. LED backlight remains lit.
[*]Unplugging and replugging failed KB+M *at* the hub doesn't fix the issue. The dock itself must be unplugged and replugged.
[*]The issue is getting worse-- now the peripherals only work for about a minute before going unresponsive.
[*]Problem occurred with a different dock (Dell WD 15).
[*]HDMI/DP output, as well as DAC after initial replug, remain fully functional during KB+M failure.
[*]Edit: This is not an issue when using Windows 10.
[*]Edit: My DAC becomes unresponsive after several minutes as well
[*]Edit: Even with just HDMI out in use, I am hearing disconnect followed by reconnect system sounds at random times.
[/LIST]

Auto suspend is disabled via editing a system config file and is reflected in GNOME config window.
My current workaround is to plug my KB+M into the built-in USB 3.0 ports on the side of my laptop. This provides functionality right at startup and a stable connection, but defeats the point of the dock.
Does anyone have suggestions? Any help is appreciated!

---

### Post by Autodave on 2020-05-13
Sounds more like a hardware problem than an OS prob.  That hub is unpowered, so my guess is that you are asking too much of you machine.  That is on the 5 volt line. So, try unplugging everything other than the mouse and keyboard.  If it takes longer for everything to stop working, you are going in the right direction.

I only use powered hubs.  You could also have a power supply going bad.  But, I usually see way too many things plugged into unpowered hubs.

---

### Post by Autodave on 2020-05-13
Sorry: I just saw where that is a laptop.  Get / try a powered dock.

---

### Post by ridagstran on 2020-05-13
Hi Autodave! My previous dock (Dell WD 15) was a powered unit, and the issue seems to be the same with the new dock. This frequency/time-to-failure remains unchanged despite the KB+M being the only connections on the hub, aside from HDMI out.
Edit: Now my DAC is becoming unresponsive after a few minutes as well.

---

### Post by Autodave on 2020-05-14
The HDMI also uses that 5V from the laptop.  Try disconnecting that.

What I would do: disconnect EVERYTHING.  See how it works using the internal KB + M without the HDMI connected.  If that is OK, try connecting only one thing at a time until you find the one that causes the issue.  If none of the singularly is causing it, then you have another issue: either the dock or the laptop itself.  There is a possibility of the OS causing this, but that is very remote.

---

### Post by Autodave on 2020-05-14
I did a quick search for the "Dell WD 15 problems".  It seems that there are quite a few issues.  You may want to take a look at some of them because a few are exactly the issue that you are having.

---

### Post by ridagstran on 2020-05-14
Rather confusingly, the dock has been working fine all morning. I started with ONLY the mouse connected, then worked my way up (waiting for failure with each addition) by adding KB, then HDMI, then a USB external hard drive.
HOWEVER, I am still hearing random disconnect/reconnect system sounds, despite the peripherals still working flawlessly. Right after I heard that happen, I punched in ```
dmesg --ctime
``` and here is the result. Does this help narrow anything down?

```
[Thu May 14 11:30:22 2020] r8152 4-1.3:1.0 enx4ce1734a629e: Stop submitting intr, status -71[Thu May 14 11:30:22 2020] usb 4-1: USB disconnect, device number 5
[Thu May 14 11:30:22 2020] usb 4-1.1: USB disconnect, device number 6
[Thu May 14 11:30:22 2020] usb 4-1.3: USB disconnect, device number 7
[Thu May 14 11:30:23 2020] usb 4-1: new SuperSpeed Gen 1 USB device number 8 using xhci_hcd
[Thu May 14 11:30:23 2020] usb 4-1: New USB device found, idVendor=2109, idProduct=0815, bcdDevice= 7.14
[Thu May 14 11:30:23 2020] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[Thu May 14 11:30:23 2020] usb 4-1: Product: USB3.0 Hub             
[Thu May 14 11:30:23 2020] usb 4-1: Manufacturer: VIA Labs, Inc.         
[Thu May 14 11:30:23 2020] usb 4-1: SerialNumber: 000000001
[Thu May 14 11:30:23 2020] hub 4-1:1.0: USB hub found
[Thu May 14 11:30:23 2020] hub 4-1:1.0: 4 ports detected
[Thu May 14 11:30:23 2020] usb 4-1.1: new SuperSpeed Gen 1 USB device number 9 using xhci_hcd
[Thu May 14 11:30:23 2020] usb 4-1.1: New USB device found, idVendor=05e3, idProduct=0754, bcdDevice=16.21
[Thu May 14 11:30:23 2020] usb 4-1.1: New USB device strings: Mfr=3, Product=4, SerialNumber=2
[Thu May 14 11:30:23 2020] usb 4-1.1: Product: USB Storage
[Thu May 14 11:30:23 2020] usb 4-1.1: Manufacturer: Generic
[Thu May 14 11:30:23 2020] usb 4-1.1: SerialNumber: 000000001621
[Thu May 14 11:30:23 2020] usb-storage 4-1.1:1.0: USB Mass Storage device detected
[Thu May 14 11:30:23 2020] scsi host8: usb-storage 4-1.1:1.0
[Thu May 14 11:30:24 2020] usb 4-1.3: new SuperSpeed Gen 1 USB device number 10 using xhci_hcd
[Thu May 14 11:30:24 2020] usb 4-1.3: New USB device found, idVendor=0bda, idProduct=8153, bcdDevice=31.00
[Thu May 14 11:30:24 2020] usb 4-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=6
[Thu May 14 11:30:24 2020] usb 4-1.3: Product: USB 10/100/1000 LAN
[Thu May 14 11:30:24 2020] usb 4-1.3: Manufacturer: Realtek
[Thu May 14 11:30:24 2020] usb 4-1.3: SerialNumber: 001000001
[Thu May 14 11:30:24 2020] usb 4-1.3: reset SuperSpeed Gen 1 USB device number 10 using xhci_hcd
[Thu May 14 11:30:24 2020] r8152 4-1.3:1.0 eth0: v1.10.11
[Thu May 14 11:30:25 2020] scsi 8:0:0:0: Direct-Access     Generic  MassStorageClass 1621 PQ: 0 ANSI: 6
[Thu May 14 11:30:25 2020] scsi 8:0:0:1: Direct-Access     Generic  MassStorageClass 1621 PQ: 0 ANSI: 6
[Thu May 14 11:30:25 2020] sd 8:0:0:0: Attached scsi generic sg0 type 0
[Thu May 14 11:30:25 2020] sd 8:0:0:1: Attached scsi generic sg1 type 0
[Thu May 14 11:30:25 2020] sd 8:0:0:0: [sda] Attached SCSI removable disk
[Thu May 14 11:30:25 2020] sd 8:0:0:1: [sdb] Attached SCSI removable disk
[Thu May 14 11:30:26 2020] r8152 4-1.3:1.0 enx4ce1734a629e: renamed from eth0
```

It seems that with every disconnect/reconnect cycle, those devices mount at higher and higher numbers, which is why they are high like you see here.
Next time my peripherals go down, I will attempt to grab a dmesg report on that. I no longer use or have the WD 15... due to an unfortunate accident involving holding it by the cable and whipping it into the ground. Thing was a piece of junk.

---

### Post by Autodave on 2020-05-14
That sure looks like you are losing enough voltage for the PC to no longer see the devices hooked to it.  You have too many USB devices: especially that external HD.  Bite the bullet and get a GOOD powered hub before you end up doing irreparable harm to your laptop.

Until you get one, keep that external drive off of the system.

I am hoping that the ext drive is an SSD: that is bad enough.  However, if it is a spinner drive, they use a large amount of power.

---

### Post by ridagstran on 2020-05-14
But why was I having the *same issue* issue even when I was using a powered hub that had a beefy power supply? Could it really have been that it was so poorly-designed as to not to make use of all that available power?

If you really think the hub is the issue, I will return it and go for a new powered one. It does look that a few reviewers on Amazon have similar-sounding issues regarding not enough power. If you have a recommendation for a good powered hub, please let me know.

Unfortunately, it's hard to test the issue again on Windows because the hub is being relatively well-behaved today. Also, I will keep the HDD off the system for now.

---

### Post by Autodave on 2020-05-14
I believe that if you keep that HD off of the system, you will be OK.  Especially if it is a spinner and not an SSD.

As far as a recommendation, I really don't.  The one that I am using right now periodically goes out (the data portion, not the power end) about every other week and I have to reset it.  Look up a few on Amazon or where ever and take a look at their ratings (mine was a 4.5 star).  Start with the better ones and then do a web search for problems with that unit.

---

### Post by ridagstran on 2020-05-14
Thank you, Autodave, for your help. I'll look around for a new one. Mine has a 4.5 star rating on Amazon and was picked out of several other highly-rated ones because it seemed that it wouldn't have issues. Unfortunately, it seems that the *vast *majority of hubs out there are made by cheap, no-name chinese brands and have many issues.

WHY IN THE WORLD Dell thought it would be a good idea to make many needed and useful ports only accessible through a USB C hub, especially when the overwhelming majority of them (including their own) are crap, absolutely boggles my mind  ](*,)

---

### Post by Autodave on 2020-05-14
I almost bought a Dell actually, but I don't remember the model.  There were a few negative reviews that caught my eye and I opted for a different one.  Now, I see that many people have the same issue, but at least it is readily "fixed" by resetting it.  Not a major inconvenience, but still an inconvenience.  Especially when only 2 months old.  Sigh.

---

