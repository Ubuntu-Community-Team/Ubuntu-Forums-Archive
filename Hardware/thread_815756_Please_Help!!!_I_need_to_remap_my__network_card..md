---
title: "Please Help!!! I need to remap my  network card."
date: 2008-06-01
forum: Hardware
---

### Post by egor08 on 2008-06-01
Please help!

I am trying to install Maple 11 on my laptop (Toshiba A305-S6825). However,
installation program can not determine the host ID of my system, and hence
I can not complete the activation process. I think that this is because it looks
for network card labeled eth0. Unfortunately, I had to disable my lan card in bios,
as this is the only way to boot Ubuntu without installing different kernel, which
may not support my other hardware.  So I was wandering if there is a way
to make eth0 to point to my wireless card.

---

### Post by gradedcheese on 2008-06-02
If you're running 8.04, you could add an interface using iw.  Assuming that your WiFi interface is wlan0, it would look something like this:

```

sudo iw dev wlan0 interface add eth0 type station

```

After that, run 'ifconfig -a' and you should see a new interface with the same MAC address as wlan0.  However if instead of 'eth0' it gets named something like 'eth0_rename', you will need to read this:

[http://linuxwireless.org/en/users/Download#Knownissues](http://linuxwireless.org/en/users/Download#Knownissues)

...and follow the instructions on changing the udev rules.  If you need to delete an interface (ex: 'eth0_rename') to try again, it's:

```

sudo iw dev eth0_rename interface del

```

---

### Post by egor08 on 2008-06-02
> **gradedcheese said:**
> If you're running 8.04, you could add an interface using iw.  Assuming that your WiFi interface is wlan0, it would look something like this:

```

sudo iw dev wlan0 interface add eth0 type station

```

After that, run 'ifconfig -a' and you should see a new interface with the same MAC address as wlan0.  However if instead of 'eth0' it gets named something like 'eth0_rename', you will need to read this:

[http://linuxwireless.org/en/users/Download#Knownissues](http://linuxwireless.org/en/users/Download#Knownissues)

...and follow the instructions on changing the udev rules.  If you need to delete an interface (ex: 'eth0_rename') to try again, it's:

```

sudo iw dev eth0_rename interface del

```

Thank you for a quick reply! When I run the first command, 
I get "iw: command not found". What do I do to install it?
Sorry, I am really new to Linux.

---

### Post by gradedcheese on 2008-06-02
'[iw]("http://linuxwireless.org/en/users/Documentation/iw")' should be present on any 8.04 ('Hardy Heron') system.  Are you running an older version of Ubuntu?  It's a relatively new command for mac80211 drivers.  Actually, that said, it would only work for you if you have a wireless chipset that uses mac80211 anyhow.  Perhaps there's an easier way to do this, such as forcing the desired mapping (ie: naming your WLAN interface 'eth0') by editing some udev rules.

---

### Post by gradedcheese on 2008-06-02
Actually, try editing this:

```

sudo gedit /etc/udev/rules.d/70-persistent-net.rules

```

...you should be able to change the desired name of your WLAN interface there.  Note that they're detected by name and MAC address.

---

### Post by egor08 on 2008-06-02
Thanks gradedcheese,

You were very helpful! However, right after my second post,
automatic update icon popped up and offered to update my 
kernel headers and stuff. After the update, I enabled lan
card, and... it worked. I installed Maple without any 
problems!!!

---

