---
title: "Ubuntu doesn' recognize my Creative Zen"
date: 2009-01-05
forum: Hardware
---

### Post by J03y on 2009-01-05
Hello, i have Ubuntu 8.04 installed, but it doesn't recognize my Creative Zen Vision. I already installed the MTP packages but still it doesn't work.

This is the output from lsusb:

```

Bus 009 Device 001: ID 0000:0000  
Bus 008 Device 003: ID 041e:411f Creative Technology, Ltd 
Bus 008 Device 002: ID 03f0:070c Hewlett-Packard 
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 046d:c30f Logitech, Inc. 
Bus 006 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

Can anyone help me?

---

### Post by Nxion on 2009-01-05
[Gnomad2]("http://gnomad2.sourceforge.net/") Seems to be one way to go. Another would be [banshee]("http://banshee-project.org/"). Give one of those a try, or both :)

---

### Post by J03y on 2009-01-05
> **Nxion said:**
> [Gnomad2]("http://gnomad2.sourceforge.net/") Seems to be one way to go. Another would be [banshee]("http://banshee-project.org/"). Give one of those a try, or both :)Tried Gnomad2 and KZenExplorer. Ill try banshee... 

Edit:Banshee just recognized all the songs that my Creative had...

---

### Post by Nxion on 2009-01-05
[Gnomad2]("http://gnomad2.sourceforge.net/") Seems to be one way to go. Another would be [banshee]("http://banshee-project.org/"). Give one of those a try, or both :)

---

### Post by amauk on 2009-01-05
Rhythmbox should also work, if you enable to MTP plugin

Edit > Plugins > check "Portable Players - MTP"

---

### Post by J03y on 2009-01-05
> **amauk said:**
> Rhythmbox should also work, if you enable to MTP plugin

Edit > Plugins > check "Portable Players - MTP"I did that but it didn't do anything

---

### Post by Nxion on 2009-01-06
OK, lets try this.

Unplug the device for a few seconds. Plug it back in and immediately open a terminal and type this:

```
dmesg | tail
```

Can you please post the output of that command.

---

### Post by J03y on 2009-01-06
> **Nxion said:**
> OK, lets try this.

Unplug the device for a few seconds. Plug it back in and immediately open a terminal and type this:

```
dmesg | tail
```


Can you please post the output of that command.This is the output: ```
[   94.009315] Disabling IRQ #17
[   97.276794] NET: Registered protocol family 10
[   97.277545] lo: Disabled Privacy Extensions
[  107.339070] eth0: no IPv6 routers present
[  323.999665] usb 5-6: USB disconnect, address 6
[  337.389326] usb 5-6: new high speed USB device using ehci_hcd and address 7
[  337.522484] usb 5-6: configuration #1 chosen from 1 choice
[  350.429435] usb 5-6: USB disconnect, address 7
[  368.303225] usb 5-6: new high speed USB device using ehci_hcd and address 8
[  368.436472] usb 5-6: configuration #1 chosen from 1 choice
```

---

### Post by J03y on 2009-01-07
Can anyone help me please?

---

### Post by johanesbrain on 2010-09-13
You can drag mp3 you want to your device on rythmbox

---

