---
title: "How to enable Ubuntu computer to detect and work with HP printer\scanner?"
date: 2016-10-23
forum: Hardware
---

### Post by GwibberFooey on 2016-10-23
I have Ubuntu MATE 14.04 AMD64; Samsung laptop with hybrid graphics system ([AMD/ATI] BeaverCreek [Radeon HD 6520G] & [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]);  HP Envy 4524 printer plus scanner. The printer and computer are connected by a USB cable.
 
I run the command ```
hp-setup
``` in terminal. Here is the output: 
```
Got bus address:  "unix:abstract=/tmp/dbus-GM6cmC6SAM,guid=04864e7cd5fba63916c47ef5580d126f" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-GM6amC1SAM,guid=04d64b7cdafba3c916c47ef4570d12af" 
Registered DEC:  true 
Registered event listener change listener:  true 
Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb

```

I have also run the command ```
hp-doctor
```. 

At some point I noticed a small popup beside the ubuntu system tray (top right of screen) saying "missing printer driver for hp 4520 envy". So the obvious question is how to get this driver implemented? 

PS. This very same printer and this very same laptop computer have worked together in the past. However, that was when the laptop had Ubuntu MATE 16.04 AMD64 LTS installed. Due to display driver problems it became necessary to upgrade to an older version of Ubuntu.

---

### Post by GwibberFooey on 2016-10-23
The command ```
apt-get install hplip
``` makes available version 3.14 of hplip, which is too old for the particular printer that I have. On the other hand, the webpage [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html) contains instructions for how to get hplip version 3.16. After following said instructions and thereby obtaining the updated hplip software, I can now use the printer as desired. Problem Solved.

---

