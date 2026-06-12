---
title: "X server crashing on login - Ubuntu 11.10 w/ ATI e350"
date: 2011-11-25
forum: Hardware
---

### Post by Andrew_Balls on 2011-11-25
Hey guys, 

I built a small box to run on my big flatscreen TV in my living room to serve several purposes and I'm having a little bit of trouble with the onboard video card. It's an ITX micro board, specs are as follows:

MSI E350IA-E45 motherboard
(onboard graphics, ATI E350 fusion, this is where my main problem is)
1 TB SATA HD
2 GB DDR3 memory
AMD e350 dual core CPU

After installing Ubuntu 11.10 on it, everything worked great. Video was slow, but it worked. I figured this was due to the lack of proper drivers, so I installed the proprietary ATI driver (go figure). After that, I rebooted and attempted to log into the LightDM login screen. It accepted my password then the X server craps out, cuts to a terminal for a few moments, then cuts back to the LightDM login screen. I installed SSH on it so now I can access it over the network, but every time I try to log in, the X server craps and kicks me back to the login screen. I've tried uninstalling the drivers and reinstalling, downloading the independent driver package from the ATI website, I can't seem to get passed the login page. Unfortunately this isn't a very popular or well-supported board, so I haven't found anyone with the same problem on google or the forums. I'd be more than happy to provide any additional information if anyone has any ideas.

Thanks!

-Andrew

---

### Post by deonis on 2011-11-25
How did you uninstall your driver? You have to reconfigure back your xserver. Use ctrl+alt+F1-6 to go to terminal and then try this out:

apt-get remove --purge  xorg-driver-fglrx
dpkg-reconfigure xserver-xorg -phigh
reboot

You should be able to login normally ...

---

### Post by fdrake on 2011-11-25
also can you post
```

less /usr/share/xresprobe/xorg.conf
lsmod
sudo lshw -c display

```

---

### Post by Andrew_Balls on 2011-11-26
I feel sort of daft. After playing with it for a while, I realized I hadn't yet finished updating it so I ran apt-get update and apt-get upgrade and now the X server works like a charm. I just need to get the resolution looking good and install VNC. Thanks everyone!

---

