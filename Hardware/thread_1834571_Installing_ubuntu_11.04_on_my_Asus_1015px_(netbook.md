---
title: "Installing ubuntu 11.04 on my Asus 1015px (netbook)...why is it not working?"
date: 2011-08-27
forum: Hardware
---

### Post by Mauroblack on 2011-08-27
So as the title says, I am trying to set up ubuntu 11.04 (using an USB drive, I already installed ubuntu on a laptop using this usb, so it works)...as I go install it and I get to select partitions or if I want it side by sides with windows (which is what I want), ubuntu just closes and restarts my computer saying the USB has been removed...

Is there a guide to over coming this issue?

---

### Post by Firezap on 2011-08-27
Hmmmm...So you already have Windows installed correct? Have you tried the Wubi installer?

---

### Post by foxy123 on 2011-10-07
> **Mauroblack said:**
> So as the title says, I am trying to set up ubuntu 11.04 (using an USB drive, I already installed ubuntu on a laptop using this usb, so it works)...as I go install it and I get to select partitions or if I want it side by sides with windows (which is what I want), ubuntu just closes and restarts my computer saying the USB has been removed...

Is there a guide to over coming this issue?

Have you solved it? I am thinking to buy it for my daughter and I'd like to install Natty or Oneiric.

---

### Post by roger_1960 on 2011-10-07
Hi

Did you disable the "fastboot" option in the BIOS.  It wont work unless you do.

I would first create the recovery image on a USB stick (as described in the asus manual).

Then use gparted or similar to delete the large empty partition on the netbook and use the "install alongside existing" option.  This would normally reformat that empty space as EXT4 and create a logical large partition for Ubuntu and a swap partition.  This should leave windows alone (but remove the d: partition) and also keep the W7 recovery image partition and the one used for Asus's own fastboot linuxOS.

If it all goes wrong you would be able to start again by reinstalling to factory state using the recovery image.

The above relates to a 1011PX, but I believe its very similar.

Roger

---

### Post by foxy123 on 2011-10-11
> **roger_1960 said:**
> Hi

Did you disable the "fastboot" option in the BIOS.  It wont work unless you do.

I would first create the recovery image on a USB stick (as described in the asus manual).

Then use gparted or similar to delete the large empty partition on the netbook and use the "install alongside existing" option.  This would normally reformat that empty space as EXT4 and create a logical large partition for Ubuntu and a swap partition.  This should leave windows alone (but remove the d: partition) and also keep the W7 recovery image partition and the one used for Asus's own fastboot linuxOS.

If it all goes wrong you would be able to start again by reinstalling to factory state using the recovery image.

The above relates to a 1011PX, but I believe its very similar.

Roger

Which Ubuntu version are you running?

---

