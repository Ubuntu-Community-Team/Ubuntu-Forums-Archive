---
title: "How to find driver version being used?"
date: 2008-07-24
forum: Hardware
---

### Post by alii on 2008-07-24
Hi, I have a bit of an odd request in that I want to find out what Ubuntu thinks my wireless card is, so I can then download the appropriate drivers for WindowsXP.

Usefully, Ubuntu simply autodetected the card and installed the correct drivers from the installation CD. Windows can't do that and therefore has no internet.

So how can I tell what my card is so that I can download Windows drivers?

---

### Post by Dark_Stang on 2008-07-24
Drivers cards are normally hooked up via pci. So if you run "lspci" in a terminal you should see your card in there. Some are hooked up usb however, so if you don't see it under pci devices run "lsusb" and you should find it there. Post the results here if you need help finding it.

---

