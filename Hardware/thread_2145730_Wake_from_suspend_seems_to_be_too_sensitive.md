---
title: "Wake from suspend seems to be too sensitive?"
date: 2013-05-16
forum: Hardware
---

### Post by abexman on 2013-05-16
It seems like something is wrong with my Ubuntu 12.04's suspend command. It seems like the suspend often fails (laptop comes back to active state), seemingly when the laptop is physically moved. I have a wireless mouse, but even when this mouse is off or not moved itself, the laptop still wakes. How can I make suspend only *wake* via the power button or maybe keyboard pressing?

/proc/acpi/wakeup
```

Device    S-state      Status   Sysfs node
PB2      S5    *disabled  
PB3      S4    *disabled  
PB5      S5    *disabled  pci:0000:00:05.0
PB6      S4    *disabled  pci:0000:00:06.0
USB0      S3    *enabled   pci:0000:00:12.0
USB1      S3    *enabled   pci:0000:00:13.0
USB4      S3    *enabled   pci:0000:00:12.2
USB5      S3    *enabled   pci:0000:00:13.2
USB6      S3    *enabled   pci:0000:00:16.2
PS2K      S3    *enabled   pnp:00:07
PS2M      S3    *disabled  pnp:00:08
P2P      S5    *disabled  pci:0000:00:14.4
```

---

### Post by tgalati4 on 2013-05-16
Install *acpitool*.  Open a terminal:

```
sudo apt-get install acpitool
man acpitool
acpitool -w
```

It should look something like:

tgalati4@Mint14-Extensa ~ $ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID0	  S3	*enabled   
  2. SLPB	  S3	*enabled   
  3. HDEF	  S3	*disabled  pci:0000:00:1b.0
  4. PXSX	  S5	*enabled   pci:0000:02:00.0
  5. USB1	  S3	*enabled   pci:0000:00:1d.0
  6. USB2	  S3	*enabled   pci:0000:00:1d.1
  7. USB3	  S3	*enabled   pci:0000:00:1d.2
  8. EHC1	  S3	*enabled   pci:0000:00:1d.7

Use the -W 8 switch to turn off (disable) device number 8 in the above list.  Turn off all other devices (especially the USB devices) because all it takes is a noisy bluetooth or camera that will wake your machine if all the USB devices are left on during sleep.  You will have to experiment and take notes as to what you tried.  Be prepared to set things back the way they were, because turning off power to parts of the bus during sleep will have unknown consequences.

A simpler method is to boot into BIOS and look for a switch "Allow USB devices to Wake" and turn that off.  There may be other sleep settings in BIOS that you can try.

---

