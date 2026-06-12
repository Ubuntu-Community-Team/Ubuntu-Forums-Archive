---
title: "USB drives not properly detected anymore with Hardy"
date: 2008-05-06
forum: Hardware
---

### Post by tik on 2008-05-06
Since I reinstalled my computer with Hardy last weekend my USB devices aren't detected properly anymore. I tried with an external harddisk and a DVD writer, both with the same result:

dmesg shows that the drive is recognized:

```
[25830.091993] usb 7-4: new high speed USB device using ehci_hcd and address 6
```

but lsusb shows nothing:

```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

Is this a known bug? Does anyone has a hint, how to further debug this?

Thanks
-Tim

---

### Post by njparton on 2008-05-06
Have you tried a simpler USB device such as a thumb drive?
 
My USB printer is detected fine.

---

### Post by tik on 2008-05-06
Ok, just tested with a MP3-Stick. That worked like a charm, it got detected and Rhythmbox popped up like expected.

Before I reinstalled to Hardy x64 I was running Feisty x86. Everything was working there. Can the problems be related to the architecture change.

---

### Post by timcredible on 2008-05-06
IMHO, I would suggest using the 32 bit version of linux.  i think there's still major issues with flash on the 64 bit.  besides, there's not really any performance difference.

---

### Post by tik on 2008-05-06
> **timcredible said:**
> IMHO, I would suggest using the 32 bit version of linux.  i think there's still major issues with flash on the 64 bit.  besides, there's not really any performance difference.

32bit is not an option. This is a development machine and I upgraded to 6GB RAM, so I need the 64bit version. And by the way, flash, altough not really important for me, is working just fine with the default installation (flashplugin-nonfree + nspluginwrapper).

---

### Post by tik on 2008-05-07
Finally solved this.

It turned out either the BIOS update I made while reinstalling enabled the 'BIOS EHCI Hand-Off' option in the USB configuration or it was always on and Feisty just don't cared. Whatever, disabling this option solved my problems, all devices are working now.

---

### Post by txtinman on 2008-05-22
> **tik said:**
> Finally solved this.

It turned out either the BIOS update I made while reinstalling enabled the 'BIOS EHCI Hand-Off' option in the USB configuration or it was always on and Feisty just don't cared. Whatever, disabling this option solved my problems, all devices are working now.

I'm having this problem also. Could you explain how you did this?

---

