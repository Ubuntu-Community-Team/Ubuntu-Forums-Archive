---
title: "NIC &amp; sound card not detected in my system with Geforce 6100 nForce 405"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by pinguin on 2006-11-15
I have a new PC with AMD Athlon(tm) 64 Processor 3500+
Acer Aspire T180
Mainboard : Acer EM61SM/EM61PM
Chipset: Advanced Micro Devices (AMD) Athlon 64 / Opteron HyperTransport Technology Configuration
Video adapter: NVIDIA GeForce 6100 nForce 405
NIC: Generic Marvell Yukon Chipset based Ethernet Controller
Sound card chip: Realtek HD Audio
(data from sisoft sandra in winxp)
I tryed Ubuntu 6.06 amd64 and 6.10 amd64
Both do not detect NIC & sound card. :confused: 

Someone can help me, please? :-k 
bye

---

### Post by slackware on 2006-11-17
Just an edit to my previous reply. I've had more time to test the system you own. The motherboard is supported using the 2.6.18 kernel. The onboard graphics are properly detected with it and works fine with the current beta driver from nvidia. The onboard nic uses the sky2 module. I havent tested the onboard sound yet because I use a pci soundcard based on envy24.

---

### Post by lchata on 2007-09-06
> **slackware said:**
> Just an edit to my previous reply. I've had more time to test the system you own. The motherboard is supported using the 2.6.18 kernel. The onboard graphics are properly detected with it and works fine with the current beta driver from nvidia. The onboard nic uses the sky2 module. I havent tested the onboard sound yet because I use a pci soundcard based on envy24.

I'm thinking of buying the Acer AST180-VD440A with the above NVIDIA 6100 nForce 405 MB.  Have googled for a day before stumbling on the thread looking for Linux (Ubuntu) compatibility.  Are there any known issues with the Realtec HD audio(on board) and DVB R/W, HL-DT_ST DVB-RW_GSA-H4IN ATA servic regarding driver availability and functionality.  A quick reply is needed before sale ends Saturday, 9/8/2007.
Thanks for any response.

---

