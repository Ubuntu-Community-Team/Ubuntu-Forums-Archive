---
title: "USB to Serial Adapter"
date: 2006-09-18
forum: Hardware &amp; Laptops
---

### Post by A. J. Rimmer on 2006-09-18
I was looking for some help with my IoGear USB to serial adapter, but wasn't able to find much of use on the forums regarding this topic.  I started digging around on my own and came up with success, so I thought I would post what I found in the hope that it will help others.

Under Windows I use the adapter on my laptop to control external equipment by toggling the DTR and RTS lines.  I have found software that I can run under Ubuntu to do the same tasks, plus, I was hoping to be able to drive an external modem.  My laptop's modem is only supported by the Linuxant pay-for-play drivers, and I have a serial modem available that I can use.

With a bit of poking around, I discovered that when the adapter is plugged in there is a device called /dev/ttyUSB0 listed in the /dev folder (and it goes away when the adapter is unplugged).  Surely, I reasoned, this is what I'm looking for.

I planned out a multi-step test whereby I would test the adapter and modem under Windows, then I would ... "Oh, nuts," I thought, "just go for it!"

Under System > Administration > Networking > Connections > Modem Connection, I entered all the appropriate information and set the modem to /dev/ttyUSB0.  Then, with the computer (HP Pavilion dv5220us) turned off, I connected the USB to serial adapter, connected and powered-up the modem, and connected the telephone line.  I turned on the computer and waited while GRUB, then Ubuntu started up.

While the Ubuntu splash screen was still up, and as the list of startup routines scrolled by, I couldn't believe my ears: eeeeee deet deet deet deet deet deet deet waaaaa buzzzz waaaa chhhhh ...

By the time the Desktop came up I was connected, logged in, and on line.  One click and Firefox came up, and another click took me to the Ubuntu Forums.

Wow, I wish they were all that easy!  Now if I can just get audio into the thing via the microphone jack... ;)

---

