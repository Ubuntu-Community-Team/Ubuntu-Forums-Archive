---
title: "Retain USB power on suspend"
date: 2010-04-04
forum: Hardware
---

### Post by duncanka2 on 2010-04-04
I'm trying to figure out if it's possible for me to charge my iPhone from my Ubuntu laptop while it's sleeping.  So far, despite trying the suggestions at [http://ubuntuforums.org/showthread.php?t=853179](http://ubuntuforums.org/showthread.php?t=853179), the USB ports continue lose power when I suspend.  In fact, I can't even write to the settings they discuss there - even if I sudo I get a "permission denied" error.  Any suggestions?

For what it's worth, the output from lsusb (with the iPhone connected) is:
```

Bus 002 Device 032: ID 05ac:1292 Apple, Inc. iPhone 3G
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```and the output of ```
ls /sys/bus/usb/devices/
``` is
```

1-0:1.0/   2-1/       3-0:1.0/   3-2:1.0/   3-2:1.2/   5-0:1.0/   7-0:1.0/   7-1:1.0/   7-1.2:1.0/ usb2/      usb4/      usb6/      
2-0:1.0/   2-1:1.0/   3-2/       3-2:1.1/   4-0:1.0/   6-0:1.0/   7-1/       7-1.2/     usb1/      usb3/      usb5/      usb7/

```

---

### Post by Slim Odds on 2010-04-04
Most PC's don't power their USB ports when the system is off.

Some very modern systems allow one to remain powered.

Is yours one of these?

---

### Post by duncanka2 on 2010-04-06
I don't think it's one of those, but I'm not turning the power off completely - I'm putting Ubuntu into "sleep"  (AKA "suspend") mode, in which the power light continues to blink and (as I understand) even the RAM continues to be powered.  Shouldn't that allow the USB ports to remain powered?

---

### Post by Slim Odds on 2010-04-06
> **duncanka2 said:**
> I don't think it's one of those, but I'm not turning the power off completely - I'm putting Ubuntu into "sleep"  (AKA "suspend") mode, in which the power light continues to blink and (as I understand) even the RAM continues to be powered.  Shouldn't that allow the USB ports to remain powered?

Not necessarily, a USB device could use a lot more power than RAM. Sleep mode tends to be pretty energy conscious because it's typically used for laptops. Though it can, and is, used for desktops these days.

How old is the system? Like I mentioned, older systems did not ever support that concept. Some new ones do.

---

### Post by tgalati4 on 2010-04-06
sudo apt-get install acpitool

man acpitool

post the output of:

acpitool -w

On an ibm thinkpad t43p I get:

tgalati4@tpad-Gloria7 ~ $ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID	  S3	*enabled   
  2. SLPB	  S3	*enabled   
  3. UART	  S3	 disabled  pnp:00:09
  4. EXP0	  S4	 disabled  pci:0000:00:1c.0
  5. EXP1	  S4	 disabled  
  6. EXP2	  S4	 disabled  pci:0000:00:1c.2
  7. EXP3	  S4	 disabled  
  8. PCI1	  S4	 disabled  pci:0000:00:1e.0
  9. USB0	  S3	 disabled  pci:0000:00:1d.0
  10. USB1	  S3	 disabled  pci:0000:00:1d.1
  11. USB3	  S3	 disabled  pci:0000:00:1d.3
  12. USB7	  S3	 disabled  pci:0000:00:1d.7
  13. AC9M	  S4	 disabled  

You need to enable one of the usb buses, and possible one of the pci buses to allow the port to stay powered during sleep.  This may not work with all hardware as it dependent on your laptop's acpi programming.

This tool is normally used to keep a network card awake during sleep so that it can listen for wake-on-lan signal.  So it might be possible to keep the usb port awake and that might provide power as well.  I have a desktop machine (2006 vintage) that has one port that provides power during sleep.  The rest of the ports go to sleep when the machine is put into suspend mode.

My guess is that anything before 2006 might not work because charging via USB was a novel concept back then.

---

### Post by duncanka2 on 2010-04-07
Here's the output:
```

   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. PCI0      S5     disabled   no-bus:pci0000:00
  2. PCI       S4     disabled   pci:0000:00:1e.0
  3. USB1      S0     disabled   pci:0000:00:1d.0
  4. USB2      S0     disabled   pci:0000:00:1d.1
  5. USB3      S0     disabled   pci:0000:00:1d.2
  6. USB4      S0     disabled   pci:0000:00:1a.0
  7. USB5      S0     disabled   pci:0000:00:1a.1
  8. EHC2      S0     disabled   pci:0000:00:1a.7
  9. EHCI      S0     disabled   pci:0000:00:1d.7
  10. AZAL     S3     disabled   pci:0000:00:1b.0
  11. RP01     S3     disabled   pci:0000:00:1c.0
  12. RP02     S4     disabled   pci:0000:00:1c.1
  13. RP03     S3     disabled  
  14. RP04     S3     disabled  
  15. RP05     S3     disabled  
  16. RP06     S5     disabled   pci:0000:00:1c.5
  17. LID      S3     *enabled   
  18. PBTN     S4     *enabled   

```By running sudo acpitool -W <#> I can change the status of all the USB and PCI entries to 'enabled', but still none of the USB ports provides power to the phone in sleep mode.  The laptop is a Dell Latitude D630 from the summer of 2007.  Is there any way to check whether I'm wasting my time - whether the hardware even supports this capability? And if I'm not wasting my time, would I be better off trying any alternate suspend program such as s2ram?

---

### Post by tgalati4 on 2010-04-07
Try sending an email to Dell's support line.  Put in your service tag so that they can tell you it's out-of-warranty.    

My best guess was to use acpitool, but if that doesn't work then look in BIOS for a switch that says "Let USB, keyboard, or mouse wake from suspend".  This would normally be in the power management section.

If that doesn't work, then my guess is that the hardware just doesn't support it.

You could also ask on the Apple and or Dell forums.

---

### Post by duncanka2 on 2010-04-14
OK...I had a little chat with a Dell agent, and despite the fact that the BIOS has a "Wake from USB" setting I can enable, the agent said that my laptop's hardware just doesn't provide enough USB power during sleep to charge an iPhone.  I guess that answers that. :(

---

### Post by Slim Odds on 2010-04-14
> **duncanka2 said:**
> OK...I had a little chat with a Dell agent, and despite the fact that the BIOS has a "Wake from USB" setting I can enable, the agent said that my laptop's hardware just doesn't provide enough USB power during sleep to charge an iPhone.  I guess that answers that. :(

I figured that this was probably the case. There is a big difference between the power needed to wake from sleep (almost nothing) to charging an external device (quite a bit).

---

