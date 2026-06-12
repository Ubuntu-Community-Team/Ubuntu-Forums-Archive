---
title: "Acer 5920 - Card Reader doesn't work"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by Ludwix on 2008-01-08
Hello,

This is my first post on this forum.
I've installed Ubuntu Gutsy on my new laptop and I must say it works like a charm.

I would like to ask for help in finding a solution to get the card reader to work. Now when I insert a Memory stick Pro it doesn't automatically mount like a usb key

I do not find much info about this on this forum.
Is there anyone who has this card reader working or is it a known problem for Acer 5920 ?

This is what I find in my lspci output:
0a:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


Another question does you LED work for the wireless button on the left ?

Thank you for your help,
Ludwix

---

### Post by Ludwix on 2008-01-19
A little nuance in to be put in my previous post.

An SD flash card works without any problem.

Greets,
Ludwix

---

### Post by Bartender on 2008-01-19
There must be dozens of different versions of the 5920.  Mine's a 5920-6470.  Doesn't have a card reader at all!

The Intel 4965 wireless card does work for the most part, but my impression is the drivers are not fully functional.  I've only tried to go online wireless a few times.  It worked most of the time but slower than vista.  I don't remember seeing the lighted key flickering.  The last time I was at the library it saw the network and appeared to connect but Synaptic couldn't get updates and Firefox was non-functional.  Went into "Network" and the box next to Wireless device had a "minus" sign instead of a check.

Is yours also equipped with the 4965?  It's a new card from Intel.  I expect (hope?) that drivers will be improved in 8.04.  I don't know how much work it would take to make the key light up but not holding my breath on that one.

---

### Post by Ludwix on 2008-01-25
Hello Bartender,

Yes mine has the same wireless network card and works fine out of the box in Gutsy.
-> Inter PRO/Wireless 4965 AG

This is what I find in dmesg:
iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1

My orange LED doesn't work on the button aswell, which is sometimes anoying.
The only "tweak" I had to do, because I suffered slow network speed (+/- 10 kbps) aswell was the following:

In a terminal:
 sudo gedit /etc/sysctl.conf

And copy this at the end of the file:
# Tweaks for faster broadband...
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_fack = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1
net.ipv4.tcp_sack = 0
net.ipv4.tcp_window_scaling = 0

-> Save the file and reboot your system

This is a solution I found on this or another forum and works for me.

Hope it helps,

Greetz

---

### Post by imopen on 2008-02-02
Hi Ludwix,

I have exactly the same notebook of you, a 5920 602G25Mn ;)

not only the light of wifi card doesn't work with the driver of the kernel but the driver itself it's immature, I don't know if it's a problem of my wireless router, but the connection is very slow with default driver.

I blacklisted it and I use Windows XP driver with latest release of ndiswrapper (1.51, downloaded from official web site) and the speed now is like in Windows. And works the wifi light too.

I don't know if next release, 8.04, will include better drivers, but I suggest you to use ndiswrapper. :)

---

