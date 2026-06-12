---
title: "Bluetooth keyboard + mouse problem: &quot;Too many links&quot;"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by eindgebruiker on 2008-03-20
Hi,

I have:

Ubuntu Gutsy AMD64
A Bluetooth dongle
An Apple wireless keyboard
An Apple wireless mouse

This is my Bluetooth dongle:

> lsusb
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

The dongle can find both devices:

> hcitool scan
Scanning ...
        00:1e:52:xx:xx:xx       My Keyboard
        00:1e:52:yy:yy:yy       My Mouse

The problem is that I can connect either the mouse or the keyboard. If I try to connect the second device I get:

> sudo hidd --connect 00:1e:52:xx:xx:xx
[B]Can't get device information: Too many links
[/B]

Google didn't give me any information on this error message.

What's happening? Is the problem in the adapter or the keyboard/mouse?

---

### Post by eindgebruiker on 2008-03-20
So currently my wireless mouse is connected, my wireless keyboard is not.
I tried to connect another device: a bluetooth phone. Same error message.

---

### Post by eindgebruiker on 2008-04-06
bump

---

### Post by boas on 2008-04-19
I know the thread is old but anyway:
I had the same problem when trying to browse my phone via bluetooth.
The sollution for me was simple:

In terminal I typed: "sudo apt-get install gnome-vfs-obexftp"

After that it worked with my phone.

---

### Post by eindgebruiker on 2008-04-22
Thanks. However this didn't solve my problem.

---

