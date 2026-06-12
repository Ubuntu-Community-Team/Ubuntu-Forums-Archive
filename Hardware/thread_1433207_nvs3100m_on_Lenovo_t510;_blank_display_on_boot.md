---
title: "nvs3100m on Lenovo t510; blank display on boot"
date: 2010-03-18
forum: Hardware
---

### Post by KB1JWQ on 2010-03-18
Just got a new Lenovo t510 today with the discrete nvs3100m graphics card.  I've attempted to install both Karmic and Lucid, with minimal success.

On boot, as soon as the grub screen fades, the display blanks; this occurs using the graphical installer as well.  I managed to get Karmic installed via text mode installer, but I can't get it to boot without killing the display; this happens even when Single is appended to the kernel line in grub.

I've managed to get a shell inside the install by using the installer CD to fire up rescue mode, and once there I've installed the Nouveau package; however a reboot leaves me back at square one.

I've seen reference to others in this forum having succeeded; what key piece am I missing / what can I try next?

---

### Post by KB1JWQ on 2010-03-19
Found the issue after much wailing and gnashing of teeth.  The kernel was held back; a dist-upgrade throw to apt-get solved this.

If anyone else is having trouble getting this to work, the step by step is as follows:

Install Lucid from the latest Alpha/Beta.
Hold down Shift on boot; edit the kernel line to end in init=/bin/bash 
This will drop you to a shell.

mount -n -o remount,rw /
dhclient eth0 (adjust for your networking environment)
apt-get update
apt-get dist-upgrade
reboot, and rejoice.

Please let me know if this works / doesn't work for anyone else.

---

