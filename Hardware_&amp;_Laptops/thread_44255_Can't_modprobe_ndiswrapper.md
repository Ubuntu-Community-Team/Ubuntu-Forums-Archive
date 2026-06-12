---
title: "Can't modprobe ndiswrapper"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by robux on 2005-06-25
Hi, I tried to set up my wlan card like shown in the ndiswrapper-ubuntu-guide [https://wiki.ubuntu.com//HowToSetUpNdiswrapper](https://wiki.ubuntu.com//HowToSetUpNdiswrapper).

When I try the "sudo modprobe ndiswrapper" I get an error:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

What can I do?

---

### Post by phantom on 2005-06-25
[QUOTE=robux]Hi, I tried to set up my wlan card like shown in the ndiswrapper-ubuntu-guide [https://wiki.ubuntu.com//HowToSetUpNdiswrapper](https://wiki.ubuntu.com//HowToSetUpNdiswrapper).

When I try the "sudo modprobe ndiswrapper" I get an error:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

What can I do?[/QUOTE]
 do this command:

sudo rm /lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

then go the directory where you extracted ndiswrapper and do:

make clean
make
make install

ndiswrapper -i "your driver"

modprobe ndiswrapper

---

### Post by robux on 2005-06-25
[QUOTE=phantom]do this command:

sudo rm /lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

then go the directory where you extracted ndiswrapper and do:

make clean
make
make install

ndiswrapper -i "your driver"

modprobe ndiswrapper[/QUOTE]

Hmm. I only have installed ndiswrapper-utils via Synaptic. That's all.

So I can't do that.

---

### Post by az on 2005-06-25
[QUOTE=robux]Hi, I tried to set up my wlan card like shown in the ndiswrapper-ubuntu-guide [https://wiki.ubuntu.com//HowToSetUpNdiswrapper](https://wiki.ubuntu.com//HowToSetUpNdiswrapper).

When I try the "sudo modprobe ndiswrapper" I get an error:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

What can I do?[/QUOTE]


You probably have the wrong .inf file installed

sudo ndiswrapper -l

---

### Post by robux on 2005-06-25
[QUOTE=azz]You probably have the wrong .inf file installed

sudo ndiswrapper -l[/QUOTE]

I have installed the WindowsXP driver.

ndiswrapper -l
Installed ndis drivers:
wg511v2 driver present, hardware present

I think that sounds OK!

---

