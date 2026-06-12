---
title: "upg to Breezy, lost wireless Sony S270"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by jliedeka on 2005-11-08
I know trying to run linux on a Sony Vaio is not for the squeamish, even a modern distro like Ubuntu.  Under Hoary I had 2 kernels installed, 2.6.11 for when I wanted sound and 2.6.10 for when I wanted my touchpad to work right.

This weekend I did a dist-upgrade to Breezy and now I have lost wireless.  The good news is the touchpad works great but no sound and no wireless.  The 10/100 ethernet works, though.

I searched these forums and found instructions for downloading/installing the latest firmware for ipw2200 and the ipw2200 driver plus ieee80211.  No dice.  My dmesg output says:

ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: device failed to start after 500ms
ipw2200: Unable to load firmware: 0xFFFFFFC2
ipw2200: failed to register network device
ACPI: PCI interrupt for device 0000:02:0b.0 disabled
ipw2200: probe of 0000:02:0b.0 failed with error -5

I manually loaded ipw2200 with modprobe which automatically picked up ieee80211 but I still have no wireless device.

Google wan't my friend today, can anyone help?

     Jim

---

### Post by jliedeka on 2005-11-08
Since posting this, I searched the networking forum.  A few threads suggested creating a file in /etc/modprobe.d called ipw2200 with the line "options ipw2200 hwcrypto=0"

I don't know why it worked but I created the file, ran a modprobe -r on ipw2200 then reloaded it and voila, wireless!

I'll have to try rebooting now.  If it comes back up with wireless, maybe I can figure out the sound issue.

     Jim

---

### Post by jliedeka on 2005-11-08
I had the same problems at boot.  However if I run these commands, I get wireless:

sudo modprobe -r ipw2200
sudo modprobe ipw2200
sudo /etc/init.d/networking restart
sudo dhclient eth1

Go figure.

     Jim

---

