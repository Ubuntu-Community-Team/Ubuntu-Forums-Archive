---
title: "Palm Z22 not connecting"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by The Bird Man of Alcatraz on 2007-07-30
Hola,
   I'm trying to connect my Palm Z22 to my Feisty Fawn setup, and so far I have gotten no sign that the Palm is connecting to the computer.  I have a simple USB cable connecting the Palm, but the Palm will not connect when I work through the PalmOS Devices wizard.  I'd greatly appreciate any advice or walk though of this problem.  Thanks a ton!

---

### Post by linuxwizard on 2007-07-30
Read over this. In the notes their is an issue with Feisty need to add module.

[https://help.ubuntu.com/community/PortableDevices/PalmOS](https://help.ubuntu.com/community/PortableDevices/PalmOS)

---

### Post by The Bird Man of Alcatraz on 2007-07-31
Thanks for the help, but I am still unable to connect to my Palm Z22.  In the gnome-pilot wizard, I reach the window "About to retrieve Owner Name..." and I press the hotsync button on the Palm, but a window pops up on my computer that says
"Failed to connect using device 'Cradle", on port '/dev/pilot'.....'ttyUSB' syncing, but do not have the usbserial 'visor' kernel module loaded.  You may need to select a 'usb:' device."

Thanks a ton for all the help,  The Bird Man

---

### Post by The Bird Man of Alcatraz on 2007-07-31
Great, I got it working.  Just had to manually start the visor module.  Thanks!

---

### Post by linuxwizard on 2007-07-31
Glad to hear you got it working.

---

