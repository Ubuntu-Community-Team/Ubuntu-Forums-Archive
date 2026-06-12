---
title: "Asus w7sg with nvidia 9300M G and Hardy"
date: 2008-07-01
forum: Hardware
---

### Post by drollo75 on 2008-07-01
I have new asus w7sg with nvidia 9300M G and i have problem to activate nvidia driver.
If i comment line Driver "nvidia" is ok. But if i enable driver nvidia in xorg.conf notebook go in low resolution.
I have installed ultimate driver from nvidia site but nothing. I have installed ubuntu native driver but nothing. :confused:

Now i have forced xorg.conf with resolution 1280x800 but no driver and no acceleration. I have problem with compiz etc etc 

Help me. :(

Bye

---

### Post by mykii on 2008-08-10
Same problem here.

---

### Post by ebola15 on 2008-08-29
Hi I have the same laptop and teh same problem. Can you tell me how you get 1280x800_ I am stuck at 800x600

---

### Post by Ng Oon-Ee on 2008-09-18
I just bought an Asus F8SG, with the NVidia 9300M G graphics card, took me half a day to figure out how to get it to work with full 3D acceleration.

Anyway, if you're reading this, you probably have already tried a few ways to get things to work. I'd recommend reversing all of them. First, uninstall anything related to envy-ng through synaptic, then uninstall anything related to nvidia through synaptic. Be very careful when uninstalling things related to nvidia, I remember at one point one of the dependencies was gnome-desktop, which obviously would not be a good thing to remove....

Anyway, once you've removed EVERYTHING, restart ubuntu, you'll come back to that ugly 800x600, do NOT take the restricted drivers offered to you if they pop up, just immediately install envy-ng from synaptic. Choose to manually install the latest 173 (or was it 177?)-series drivers, and if you've crossed your fingers hard enough, that will work. The uninstalling previously was very needed.

---

