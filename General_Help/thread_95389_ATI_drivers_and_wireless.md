---
title: "ATI drivers and wireless"
date: 2005-11-26
forum: General Help
---

### Post by kougaru on 2005-11-26
I'm trying to install the ATI drivers from the repository but to do it right I have to uninstall the linux-restricted-modules first then restart the computer, but when I restart, my wireless card doesn't work anymore so I can't get the drivers from the repository. I tried the madwifi thing in the new drivers thread but that didn't work. Any help :(

---

### Post by rsankuratri on 2005-11-26
I am not sure what version of the driver you are trying to install.  But here's what you could do.

1.  Get your wireless back to a working condition
2.  sudo apt-get install xorg-driver-fglrx
3.  sudo gedit /etc/X11/xorg.conf and replace the "ATI" with "fglrx" in the device section. Restart your computer

I did exactly the same (except I did not have to do anything with my wireless) on my Dell Inspiron 9100.  If you need I can post my xorg.conf file

---

### Post by charlesbrooking on 2005-11-26
[QUOTE=kougaru]I'm trying to install the ATI drivers from the repository but to do it right I have to uninstall the linux-restricted-modules first then restart the computer, but when I restart, my wireless card doesn't work anymore so I can't get the drivers from the repository. I tried the madwifi thing in the new drivers thread but that didn't work. Any help :([/QUOTE]

Once you get wireless back, you should be fine. There are instructions around for how to install the ATI drivers, and none that I've seen require other modules to be removed. As rsankuratri said, you should only need to remove (or comment out) references to old driver from /etc/X11/xorg.conf.

Ignore the ATI drivers to for now and use someone else's Internet connection to download drivers for your wireless card. If you search the forums for your particular card, you should find instructions on how to do this.

---

