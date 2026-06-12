---
title: "Booting from USB drive?"
date: 2016-11-11
forum: Hardware
---

### Post by lastopier on 2016-11-11
Hi, I've been dual booting for a long time and I am slowly but surely growing tired of it. Windows tends to die a lot, which means it has to be reinstalled and that is a giant pain. 

Therefore I decided to dedicate the whole disk to Win and boot Ubuntu from USB. Buying an external hard drive or SSD is an option, but I don't really need all the free space offered, which makes them overly expensive. Personal data can stay on laptop HDD. 

I'd like to ask about your experience with booting from USB drive (through USB 3.0 of course). Does it work well? Is the speed sufficient? What capacity and speed should I aim for?

Thank you for your responses.

---

### Post by TheFu on 2016-11-11
My systems will not boot from USB3 devices. Only USB2. Very frustrating.  But I only have a few systems that even have USB3. 2 systems are running add-on USB3 cards. Never tried to boot with those systems.  Neither of my chromebooks will boot from the USB3 port, very frustrating. Seems to have been a conscious decision NOT too allow USB3 booting on those devices.  Actually, if any storage is connected to the USB3 port on my main chromebook at boot, the trackpad usually doesn't work. Think it alters the order of USB devices, confusing the trackpad drivers. Just to be clear, my chromebooks do not have ChromeOS.

Also worth considering is using a portable SSD.  That doesn't impact the boot with USB aspects, at least not in my experience. Love my portable SSD.

Unless you really need direct HW access, I'd run one of these OSes inside a VM. Depends on the RAM and CPU available, but pretty much any system over $300 can do virtualization well.  Which OS you choose as the host is really the only question.  If Windows is giving you issues, having a 100% snapshot for the VM means never really having to reinstall again.

Just sayin'.

---

### Post by C.S.Cameron on 2016-11-11
My office desktop boots USB3 OK, My office laptop seems to boot faster when the dongle is plugged into USB2.
Not sure if this is a driver thing or what, the laptop is almost 5 years old.
I will be watching this thread to see other's comments.
My best setup so far is running Windows 10 in a virtual box with Ubuntu host, when I need it.
I can even carry this around on a pendrive.

---

### Post by sudodus on 2016-11-12
Most computers boot willingly for me from USB 3 as well as from USB 2. The exceptions are some very old computers (more than 12 years old, too old to manage booting from USB) and some very new computers, where the manufacturers have made it hard to boot anything but the installed operating system (Windows or MacOS). See this link and links from it,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

I would consider not only the nominal speed of the USB drive, but also the real life speed as described in the following link and links from it,

[FromUSBStick#Notes about speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

---

### Post by lastopier on 2016-11-13
Okay, I decided to go ahead and buy a USB 3.0 flash drive. It's not a huge investment and I can always use it if things don't work out very well. Thank you for flash drive comparison, it came in very handy when deciding what to buy. I will report here how it worked out.

All right, everything is installed and works fine. The system (Lubuntu) boots up nice and quickly. Even faster than from the hard drive (Kids, don't every buy 5400 RPM disk). The only problem is that I can't get my laptop to boot from USB first - I have to manually select if from boot order menu each time.

---

