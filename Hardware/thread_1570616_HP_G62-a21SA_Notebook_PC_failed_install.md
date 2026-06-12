---
title: "HP G62-a21SA Notebook PC failed install"
date: 2010-09-08
forum: Hardware
---

### Post by Ingotian on 2010-09-08
I have just bought a new HP laptop. Ran 9.1 live and installed it, upgraded to the latest updates rebooted from hard drive then upgraded to 10.04 reboot after a short time blank screen and installation dies.

Tried the latest 64 bit Sabayon linux and it runs from live DVD but when installed to hardrive gets to 

waiting for uevents to be processed..

early in the booting and then it fails with a blank screen.

Anyone any ideas? Also tried 10.10 beta 64 bit and it failed in a similar manner so it seems to be something that has changed between 9.1 and 10.04. 

Laptop hardware details
Microprocessor	2.13 GHz Intel Core i3-330M Processor
Microprocessor Cache Level 2 cache 3 MB
Memory	2 GB DDR3 (1 x 2048 MB)
Memory Max Supports up to 4 GB DDR3 memory
Video Graphics Intel HD Graphics
Video Memory up to 762 MB total available graphics memory
Display	39.6 cm (15.6") diagonal High-Definition LED HP BrightView Display (1366 x 768)
Hard Drive 250 GB SATA Hard Disk Drive 7200 rpm
Multimedia Drive SATA optical drive: LightScribe SuperMulti DVD±R/RW with Double Layer Support
Network Card Integrated 10/100BASE-T Ethernet LAN
Wireless Connectivity Bluetooth wireless networking
802.11 b/g/n
Sound	Altec Lansing speakers
keyboard Full size keyboard with One touch launch keys and Action keys
Pointing Device	Touch Pad with On/Off button and 2-way Scroll pad support
PC Card Slots	5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro or xD Picture cards
External Ports	
1 VGA port
1 HDMI port
1 stereo headphone-out
1 microphone-in
3 USB 2.0 ports
1 RJ45 ethernet port

---

### Post by Ingotian on 2010-09-09
Replying to my own post as I have found out a bit more :-). This laptop also uses Broadcom wireless that was not recognised in 9.10. I fixed this using the information at [Broadcom]("http://www.broadcom.com/support/802.11/linux_sta.php") and these lists (Thanks community). 

The "latest ATI Mobility Radeon HD4250 graphics technology" seems to be the real problem. 9.10 reports no proprietary drivers even after using synaptic to install the Radeon drivers there. The machine works in 1024 x 768. I can live with this for a while but the real snag is that upgrading to 10.04 kills the boot. I bought this laptop because it was significantly the least expensive core i3 350m laptop (from Staples) I could find so I guess quite a lot of people will buy them. It would be nice to have a fix for 10.10 coming up. I'll have another go at the graphics driver but if anyone has a definitive fix, it would help since I'm a bit pushed for time, thanks.

---

### Post by welshmike on 2010-09-09
Sorry to read about your struggle but thanks for posting the info. I saw the Staples ad on TV tonight and until reading your message was going to order a HP G62-a21SA Notebook from them.
However as I've read [COLOR="RoyalBlue"]***[here]("http://forum.novatech.co.uk/showthread.php?t=22705")***[/COLOR] and [COLOR="RoyalBlue"]***[here]("http://forum.novatech.co.uk/showthread.php?t=22839")***[/COLOR] that Ubuntu install easily and works well on the Novatech i3 I guess I'll pay the extra and get that laptop.

---

