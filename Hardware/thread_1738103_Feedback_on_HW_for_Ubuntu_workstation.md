---
title: "Feedback on HW for Ubuntu workstation"
date: 2011-04-24
forum: Hardware
---

### Post by jebus_beler on 2011-04-24
I'm specing out a mostly productivity based ubuntu workstation and was hoping to get some feedback on my hardware choices (particularly warnings for incompatibility).  The main uses will probably be mathematica and photo-editing (unrelated) using gimp/bibble and maybe some random coding.  I might also try to run this as a hackintosh system with lightroom if bibble doesn't work well enough for me.  I doubt I will be doing any gaming but want 3-d capabilities in case gimp/bibble or mathematica ever use cuda.  I don't see myself adding another GPU anytime soon.  I am trying to build the system to run very quietly and be energy-efficient.  

Specs:

Cooler Master CM-690 II Advanced
Cooler Master Silent Pro 500W (M500)
Core i7 2600K
Asus P8P67 Pro (Rev. B3)
MSI GeForce GTX 560 Ti Twin Frozr II (1 Gb)
Corsair Vengeance - 8 Go : 2 x 4 Go - DDR3 - 1600 MHz / PC3-12800 (1.5V)
Western Digital HD - Caviar Black - 3,5“ - 1 TB - SATA III

Probably will later use a Dell U2701 screen for better color calibration.

Of course most of this hardware is will not interact with the OS so my question is mostly about the graphics card and the motherboard.

In particular:
- NVidia GTX 560 under linux
- Audio, ethernet, bluetooth etc.. of Asus p8p67 under linux
- Coolermaster CM 690 II supports hot-swappable Sata drive in AHCI mode but needs OS support. Does this work in linux?

Many thanks in advance for the feedback!

---

### Post by princeofindia on 2011-04-24
Linux has evolved greatly now.It has support for those devices also which windows doesn't support.so,I think any hardware configuration would be good.so,it should work fine with the devices you have listed.

---

### Post by jebus_beler on 2011-04-24
Thanks for the response but its not obvious that e.g. all the components on the motherboard will work though by checking them individually it seems they are mostly supported or are in the process of being supported.  

For reference or in case someone has more details here are some relevant components of the P8P67:

• Intel 82579 Gigabit LAN Dual interconnect (linux supported).
• Realtek ALC892 8-Channel High Definition Audio CODEC (linux supported) 
• VIA 6308P controller supports 2 x 1394a port(s)
• Marvell® 9120 controller 
• JMicron® JMB362 SATA controller

---

### Post by jebus_beler on 2011-04-25
A more basic question (and more general).  I was thinking of getting a bluetooth keyboard for this system but I don't have _any_ usb keyboard now.  Will this be a problem for installing the system?  That is, will I need a usb keyboard to run the install to the point where I have bluetooth setup?

---

### Post by cmcevoy on 2011-06-25
Old thread, I know, but maybe an answer will still be useful. I have the (non-pro) version of this motherboard and there is a problem with the bluetooth firmware under Linux (2.6.37.6) - it works only if you boot into Windows first to get the correct firmware loaded. I'm sure the problem is fixable but I haven't needed to spend the time to do so yet.
Apart from this the motherboard works fine (although all the overclocking and management software provided by ASUS is Windows only)

---

### Post by jebus_beler on 2011-11-07
Thanks for the answer but its turns out bluetooth and everything works pretty well on this motherboard.  In fact the whole system is pretty great for linux.  The only probably is overclocking seems to interfere with suspend in 10.04 but this might even be fixed in newer kernels.  Oh, well and I am using 10.04 because the nvidia driver seemed to have some weird bug that caused it to slow down in 11.04 after a few hours/days usage but I'm guessing this was a one-time fluke that will be ironed out by now but I'm happy using 10.04 and somewhat scared of unity so don't wanna bother upgrading to test yet.

---

