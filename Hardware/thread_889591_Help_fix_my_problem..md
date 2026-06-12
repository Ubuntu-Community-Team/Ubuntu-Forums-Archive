---
title: "Help fix my problem."
date: 2008-08-14
forum: Hardware
---

### Post by bOiKIDZ on 2008-08-14
I am new to ubuntu. I just installed it to my laptop with Windows XP Service Pack 3. I have done nothing yet. After I installed ubuntu, it works well except for my Wireless Lan. I typed in the terminal "lspci" and this is the result:

-------------------------------------
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
--------------------
I did not installed any drivers or something because i dont know how.
My Wireless lan wont work and i cant set the brightness. Anyone can help me? by the way, can you please guide me step by step because this is my first time to use this.


The model of my Laptop is HP Compaq Presario C793TU

---

### Post by Compwiz on 2008-08-14
This post should help: [click here](http://ubuntuforums.org/showpost.php?p=5549249&postcount=8), read through it carefully, as it has some good information.

---

### Post by bOiKIDZ on 2008-08-14
the link you have provided seems not to work with mine.

when i typed in
sudo iwconfig

the result is 
lo no wireless extension
eth0 no wireless extension

---

### Post by bOiKIDZ on 2008-08-14
still no wireless.

---

### Post by bOiKIDZ on 2008-08-15
i got this to work. thank God. I am getting a hard time because i am fooled by the model of the wireless adapter. I thought it was AR5006X but then it was AR242. Sorry for the thread. can i make this thread as my general query of my problems? thanks.

---

