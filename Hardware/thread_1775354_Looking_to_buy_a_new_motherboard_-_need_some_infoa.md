---
title: "Looking to buy a new motherboard - need some info/advice"
date: 2011-06-04
forum: Hardware
---

### Post by mniasfreemag on 2011-06-04
Hi,
I am looking to upgrade my PC to the new sandybridge core i5-2500k processor. I have been looking into motherboards made by ASUS, MSI,ASROCK and GB. I have some questions  regarding the compatibility in ubuntu.

1) USB 3.0: 
ASUS uses NEC USB3.0 controller on the older MOBOs and ASMedia usb 3.0 controller on the newer and cheaper Mobos.

GB uses Renesas D720200 chip and VLI VL810 hubs on their mobos, the newer ones have etron chips

MSI uses NEC usb3.0 chips for their mobos

Which of these USB 3.0 chips are supported by ubuntu?

2) Most of the MB's use Marvell chipset for SATA 6 gps, are these supported by ubuntu?

3) Are the realtek (e.g. RTL8111E)  lan chips supported by linux?

4) is the iTE IT8728 chip supported in ubuntu

If anybody has more info on these questions feel free to share it.

Thanks

---

### Post by Yellow Pasque on 2011-06-04
No idea about the USB3 stuff, but
2) On Ubuntu 11.04 and later, yes: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2648689.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2648689.html)
3) Yes
4) Not yet: [http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices)

---

### Post by mniasfreemag on 2011-06-04
Thanks for the quick reply and links. If only someone could clear up the USB 3.0 issue.

---

### Post by cascade9 on 2011-06-05
1- I've used the NEC D720200F1 USB 3.) chip with linux (not ubuntu though). It worked no problem, but I didnt test with a USB3.0 device, and IIRC the full speed of USB 3.0 isnt currently avaible with linux distros. 

2- Err...what? Some of the LGA1155 motherboards have marvel/jmicron SATAIII controllers, but not 'most'. 

All the LGA1155 motherboards have at least 1 SATAIII port from the intel controller, and from everything I've ever seen, you are much better of using the intel SATAIII controller. 

Then again, you've speced a i5-2500K CPU, so you are probably looking at the tweaky 'overclockers' motherboards.  They are more likely to have extra addon SATAIII controllers, but still you are better off using the intel SATAIII ports.

---

