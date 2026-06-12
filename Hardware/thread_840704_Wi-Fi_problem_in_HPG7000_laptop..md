---
title: "Wi-Fi problem in HPG7000 laptop."
date: 2008-06-25
forum: Hardware
---

### Post by ilusha2007 on 2008-06-25
I have a HP G7035R Laptop. According to Everest (Windows), it has Atheros 50007 WiFi adapter. It works well with Mandriva, but as for Ubuntu, it is recognised but it doesn't work; as far as I can understand, it lacks driver. There is a MedWiFi solution, but I failed to make it work. Could you explain how I can apply the MedWiFi solution to my laptop, or how I can use (if possible) the Mandreva's driver?

I would appreciate your help.

---

### Post by sergiom99 on 2008-06-25
please post the output of:
```
sudo lspci
``` 
so that we can see if its recognized and how by Ubuntu.
Then, with that data its easier to find howto's for madwifi drivers.

---

### Post by ilusha2007 on 2008-06-25
_(from kubuntu)_

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controlle
r Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Grap
hics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
 (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (r                      ev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll                      er #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll                      er #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll                      er #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Control                      ler #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller                       (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Contro                      ller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHC                      I Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wirele                      ss PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139                      C+ (rev 10)

---

### Post by sergiom99 on 2008-06-25
Hey there. I have a Broadcom chipset, so Im not sure how to install yours, but a quick search in the forums gave me this hints:
[http://ubuntuforums.org/showthread.php?t=795984&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=795984&highlight=AR242x)
[http://ubuntuforums.org/showthread.php?t=766169&highlight=atheros+AR242x](http://ubuntuforums.org/showthread.php?t=766169&highlight=atheros+AR242x)
[http://ubuntuforums.org/showthread.php?t=789824&highlight=atheros+AR242x](http://ubuntuforums.org/showthread.php?t=789824&highlight=atheros+AR242x)
take a look at them to find out which applies better to your wireless card.

Hope this helps- Sergio

---

