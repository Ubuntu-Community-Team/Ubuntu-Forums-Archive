---
title: "Booting from LTSP server with i486 laptop..."
date: 2008-10-21
forum: Hardware
---

### Post by FezzFest on 2008-10-21
Hello !

I have just found how to set up an Ubuntu LTSP server.
It works very good, and I wanted to use a very, very old laptop as a thin client for booting from it.

This are the laptops specs:

- Intel 486DX2 @ 40MHz (wow)
- RAM 20MB (4MB internal + 16MB)
- HDD 200MB with Windows 95B
- Western Digital Graphics 256 colors
- Floppy 1.44 inch
- Xircom PCMCIA 16 bit Network Card

It should be possible to boot the Ubuntu LTSP server.
I followed some tutorials, and I found out the following:

To boot your laptop from the LTSP server, you need a compatibe network card. Use the site [http://rom-o-matic.net/](http://rom-o-matic.net/) and find your network cards chipset.

There's only a problem:

I don't know the chipset of the Xircom card, and even if I can find the chipset, I won't find it in the Rom-o-matic list.

The Rom-o-matic list only supports PCI cards for desktops.

The should be other ways to boot the laptop, without Rom-o-matic, but I don't know how to do that.

I really want to do this, if it works I will be very, very thankful to everyone.

Please help me.

---

### Post by FezzFest on 2008-10-24
Wow, I really get a lot of information here...

---

### Post by cariboo on 2008-10-24
If your Xircom card doesn't have a boot rom the laptop will not boot from the network. If there is any sort of number on pcmcia adapter do a search  for any of them to see what you come up with. Truthfully I think you are out of luck.

Jim

---

### Post by mikjp on 2008-10-24
Probably the BIOS does not support booting from network. Even older Pentiums cannot do the trick, they cannot even boot from CD. 

Install a lightweight Linux on the laptop and use it as a terminal. See the [Mock-Mainframe HOWTO](http://tldp.org/HOWTO/Mock-Mainframe/).

---

