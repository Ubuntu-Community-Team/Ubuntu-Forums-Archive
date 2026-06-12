---
title: "grub-instal /dev/sda Not found or not a block device (Fix)"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by Orbital_sFear on 2009-05-18
I recently installed windows on a HD already containing Ubuntu.
After the windows installation I used a liveCD to get back into ubuntu to fix Grub.

I ran the following command and got the follow error

sudo grub-install /dev/sda1
Not found or not a block device

I had to dig into the script to find the fix, so here it is:
cd /media
sudo mkdir sda1
sudo mount /dev/sda1 sda1
sudo grub-install --root-directory=/media/sda1 /dev/sda1
cd /
sudo reboot

*Ding, now when I rebooted I had ubuntu back

---

