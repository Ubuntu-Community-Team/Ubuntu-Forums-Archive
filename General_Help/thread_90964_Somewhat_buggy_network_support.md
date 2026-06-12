---
title: "Somewhat buggy network support"
date: 2005-11-16
forum: General Help
---

### Post by toon on 2005-11-16
Hello,

Any other experience a somewhat random successrate ragarding networking? I don't know if this is related to ndiswrapper, but I have 2 nics; eth0 and wlan0, and every 2-4 reboot I have to go through this enable/disable ritual where I mix and match sudo ifconfig eth0/wlan0 down/up, the networking controlpanel and sudo rmmod/insmod ndiswrapper.

Using static IP for eth0, I will be able to ping say 192.168.0.1, but not use it as a default gw (route hangs). A few ups/downs later, and it works fine. There doesn't seem to be any coherent solution to this; I've managed to fix it by having both cards enabled, or just the one I need. Oh, sometimes "sudo rmmod ndiswrapper" doesn't actually remove it (it's still showing up with lsmod).

Another thing, this happened to me an hour ago, and I decided just to try and reboot. The computer acted like a freggin calculator on the consequent boot; boottime alone took well over 15 minutes. Finally logged into gnome (took SEVERAL minutes as well), I got an error, "failed to initialize HAL", and when I clicked okay I got booted to GDM. I then picked shut down, which it did after a couple of minutes, and then powered it up. All fine. This is the second time that happens. Any ideas?

Oh, my hardware is a HP Pavilion zd8000; 3.4GHZ P4 (which noises a lot and you can't control the fan:/ ), 2GB ram and the works...

---

### Post by ScreemingBlue on 2005-12-07
Do you have DHCP running at all (I mean anywhere on your network)? If so try disabling it and use fixed IP addresses for awhile to see if that cures your problem.

---

