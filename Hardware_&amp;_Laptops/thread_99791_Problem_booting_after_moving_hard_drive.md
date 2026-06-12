---
title: "Problem booting after moving hard drive"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by sitara on 2005-12-06
I have a problem booting Kubuntu. I followed this procedure on two PCs, an old one (with a new disk) and a newer one (with an old disk):

1) Installed Ubuntu 5.04 from CD
2) Upgraded to 5.10 using apt-get
3) Installed KDE (kubuntu.desktop) from Synaptic
4) Copied my live data onto the new disk on the old machine

Everything was working fine. Then I swapped the hard drives in the two systems to get the new disk with the live data on the newer machine. 

The old machine with the old disk works fine, but the new machine with the new disk won't boot. I have had a couple of different errors, but usually it runs through the whole startup process and then dumps me in a terminal.

It seems that it's just KDE that won't load.

The other thing that happens sometimes is that a message is displayed regarding the state of the battery, and then hangs. These are both desktop machines, so there is no battery.

I would really appreciate some help. I don't have a 5.10 CD, so the installation process is quite laborious and I really don't want to have to go through the process of migrating all the data again.

Thanks in advance,

Keith

---

### Post by Lambert on 2005-12-06
Try this.

Log in then run this command

sudo dpkg-reconfigure -phigh xserver-xorg

Your systems have different graphics and monitor settings probably so what's on the disk matches to the other pc. The above command will reconfigure your settings to match this pc.

---

### Post by sitara on 2005-12-06
Thanks for the lightning fast response!. That's done the trick. Everything's now working fine.

Keith

---

