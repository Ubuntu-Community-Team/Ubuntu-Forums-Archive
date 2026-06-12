---
title: "USB not working in fresh Gutsy install"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by tseo on 2007-11-08
I just installed the new Ubuntu and was impressed by how everything is running smoothly from the beginning. Then I tried to plug my USB mouse and then my iPod and they just don't work.
I am absolute noob about linux so I don't know what exactly do I have to check before posting here but in Hardware Information i saw that it sees MCP51 USB Controller and under it OHCI controller and EHCI controller. 
Do I have to provide any more info and can somebody help please?

---

### Post by wolframarnold on 2007-11-12
I have a similar problem.  Fresh Gusty install and no USB devices seem to be recognized at all.  This was not a problem in Feisty.

syslog does not record any connect events.  I ran "lsmod | grep usb", "lsmod | grep uhci", "lsmod | grep ohci", and there are no kernel modules loaded!  I saw a report where modprobe crashed during bootup, but I can find no evidence for that in the logs.  "lsusb" also produces no output.

I'm puzzled as to why the kernel fails to load any of the usb modules.  I could throw these into /etc/modules by hand, but I don't even know which ones to put there.

Something more fundamental seems broken.  Help is appreciated.

---

### Post by wolframarnold on 2007-11-12
Actually, thanks to reading about bios settings in another post, I have since been able to figure this out.  I had disabled the BIOS flag for "legacy USB support" in the BIOS configuration. It turned out that this was necessary for the kernel to recognize the USB system.  Once I turned that flag back on in the BIOS settings, Kubuntu is OK and recognizes my external mouse and automounts my usb stick just fine.

---

### Post by tseo on 2007-11-13
I don 't know what you mean BIOS setting but if this is the BIOS setup on boot I don't have setting for almost nothing there unfortunately:(
Now I noticed that the USB devices work if you boot the computer with them but don't work when you just plug it in...

---

