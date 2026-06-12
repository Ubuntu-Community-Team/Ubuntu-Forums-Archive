---
title: "Hardware issues USB - please help"
date: 2008-12-27
forum: Hardware
---

### Post by desaber on 2008-12-27
Hey All,

I am extremely new to ubuntu and linux in general. I just installed Ubuntu 8.10 on my Acer TravelMate 8200 laptop. During boot ubuntu hangs on the splash screen for 2 mins and once booted up and logged in the computer itself in generally sluggish ( compared to the install of XP SP3 ).

I booted up recovery mode so i could see where the issue was. it seems to have issues with a usb device(s) The below error cycles 127 times, causing the delay in boot and continues when the computer is running.

here is a copy of one of the offending entries from /var/log/messages:

Dec 27 08:32:05 Fortress kernel: [  717.760110] usb 5-8: new high speed USB device using ehci_hcd and address 71
Dec 27 08:32:05 Fortress kernel: [  746.942966] usb 5-8: configuration #1 chosen from 1 choice
Dec 27 08:32:05 Fortress kernel: [  778.568869] gspca: probing 046d:0892
Dec 27 08:32:05 Fortress kernel: [  809.492608] vc032x: check sensor header 44
Dec 27 08:32:05 Fortress kernel: [  847.638135] usb 5-8: USB disconnect, address 71
Dec 27 08:32:05 Fortress kernel: [  861.505922] vc032x: I2c Bus Busy Wait 0
Dec 27 08:32:05 Fortress kernel: [  861.505922] vc032x: I2c Bus Busy Wait 0
Dec 27 08:32:05 Fortress kernel: [  861.505922] vc032x: I2c Bus Busy Wait 0
Dec 27 08:32:05 Fortress kernel: [  861.505922] vc032x: I2c Bus Busy Wait 0
Dec 27 08:32:05 Fortress kernel: [  861.505922] vc032x: I2c Bus Busy Wait 0
Dec 27 08:32:05 Fortress kernel: [  861.505922] vc032x: I2c Bus Busy Wait 0
Dec 27 08:32:05 Fortress kernel: [  954.809333] vc032x: Unknown sensor...
Dec 27 08:32:05 Fortress kernel: [  968.061353] vc032x: probe of 5-8:1.0 failed with error -22

This starts at Address 1 and cycles through to address 127. Any help would be GREATLY APPRECIATED!! THANKS!

---

### Post by desaber on 2008-12-27
Ok.. so after a lot of research i am convinced that this is most likely the piece O' crap orbicam that is built into the laptop. I don't ever use it. nor do i want to. 

I have added this line: "blacklist gspca" to the bottom of: etc/modprobe.d/blacklist

But the error is still going nuts. I have been searching high and low to try and find out how to permanently disable this device and haven't found an answer yet. Is there some hardware manager i am missing. or can this at least be done from the command line?

Thanks!

---

### Post by desaber on 2008-12-29
Does anyone know of another message board where i might be able to get some help?

---

### Post by desaber on 2008-12-30
I was able to stop this error by modifying my blasklist entry.

I modified "blacklist gspca" to "blacklist gspca_vc032x" This stopped the error and also stopped udevd from using 50% of the processor.

---

### Post by macvr on 2009-01-07
> **desaber said:**
> I was able to stop this error by modifying my blasklist entry.

I modified "blacklist gspca" to "blacklist gspca_vc032x" This stopped the error and also stopped udevd from using 50% of the processor.

SAME ERROR:
Acer Aspire 5672 WLMi laptop
```
Jan  8 08:43:20 UBUNTU-laptop kernel: [  116.801402] usb 5-8: USB disconnect, address 33
Jan  8 08:43:20 UBUNTU-laptop kernel: [  116.801612] vc032x: I2c Bus Busy Wait 0
Jan  8 08:43:20 UBUNTU-laptop kernel: [  116.801672] vc032x: I2c Bus Busy Wait 0
Jan  8 08:43:20 UBUNTU-laptop kernel: [  116.801737] vc032x: I2c Bus Busy Wait 0
Jan  8 08:43:20 UBUNTU-laptop kernel: [  116.801797] vc032x: I2c Bus Busy Wait 0
Jan  8 08:43:20 UBUNTU-laptop kernel: [  116.801856] vc032x: I2c Bus Busy Wait 0
Jan  8 08:43:20 UBUNTU-laptop kernel: [  116.801915] vc032x: I2c Bus Busy Wait 0
Jan  8 08:43:20 UBUNTU-laptop kernel: [  116.801972] vc032x: Unknown sensor...
Jan  8 08:43:20 UBUNTU-laptop kernel: [  116.802033] vc032x: probe of 5-8:1.0 failed with error -22
Jan  8 08:43:20 UBUNTU-laptop kernel: [  117.072136] usb 5-8: new high speed USB device using ehci_hcd and address 34
Jan  8 08:43:20 UBUNTU-laptop kernel: [  117.228236] usb 5-8: configuration #1 chosen from 1 choice
Jan  8 08:43:20 UBUNTU-laptop kernel: [  117.228890] gspca: probing 046d:0892
Jan  8 08:43:20 UBUNTU-laptop kernel: [  117.436495] vc032x: check sensor header 44
```
only thing that stopped udev from using 50% cpu was blacklisting > gspca_vc032x   !!!

---

