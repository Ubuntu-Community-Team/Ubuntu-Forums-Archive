---
title: "wlan and booting issues"
date: 2006-01-21
forum: Hardware &amp; Laptops
---

### Post by superuser on 2006-01-21
Hello!

After having used gentoo exclusively on my two desktop pcs for a while now, I became tired of the ever-so-slow compiling procedures and installed ubuntu as the distribution of choice on my new hp nx6110 laptop.

I experienced a bit of trouble with the 5.10 Breezy Badger release recently, though.

While booting, my lapotop needs tremendously long a time to finish the steps "configuring network interfaces" as well as "waiting for network interfaces to come up", when there is no network cable plugged in.

I have set up a broadcom 54g WLAN device wlan0 using ndiswrapper. Besides, the laptop also has got an ethernet 100 mbit card eth0. 

Here's my /etc/network/interfaces: ```
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# the primary network interface
auto wlan0
iface wlan0 inet dhcp
wireless-essid MYESSID
wireless-key MYKEY

iface eth0 inet dhcp
auto eth0

```

Can't this process at least be backgrounded?

Furthermore, my WLAN doens't automatically log in. With no changes to anything else, I can get it to work with network-admin by just simply clicking deactivate - activate which seems a little odd to me.
/edit: Surprisingly enough, after having quited the procedure with CRTL+C last boot, I am now automatically loged in.

thanks a lot,
superuser

---

### Post by localzuk on 2006-01-21
The problem with backgrounding that task would be that the next task, connecting to NTP Time Servers, would not be able to run if the prior one hadn't finished.

The simplest solution that I see to this is to remove the line 'auto eth0' from your interfaces file. That way you don't get the delay if no cable is plugged in - but you can still enable it via network-admin as usual.

---

### Post by mark_g on 2006-01-21
I had the same problem. Solved it by disabling the network services at startup, writing a simple shell script and executing it as a Gnome startup script.
Also try InitNG if you want your pc to boot up faster. Makes a big difference for me. Really a great program you should check out.

---

### Post by scubajeff on 2006-01-24
i use wifi-radar to automatically scan and connect to different wireless APs at home and/or at work. it's very easy to install, highly recommended.

My /etc/network/interfaces file looks pretty clean after installing wifi-radar.
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
iface eth1 inet dhcp

#auto eth0

```

---

### Post by superuser on 2006-01-29
Now that's bizarre: Once I automatically got a connection to my AP, the internet access becomes horribly slow (for my laptop as well as for my desktop computers that are connected through ethernet). I'll have to re-establish the link with the router's web interface (which then again surprinsingly comes up with usual speed).

However, if I manually log in through "ifup wlan0", this does not happen!

Here is my interfaces file: ```
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid wlan

```

---

