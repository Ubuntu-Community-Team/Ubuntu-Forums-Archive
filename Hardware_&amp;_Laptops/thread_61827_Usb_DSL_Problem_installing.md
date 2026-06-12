---
title: "Usb DSL Problem installing"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by Hg80 on 2005-09-02
ok ive followed all the guidelines on these forums and others to try and install my Sagem f@st 800-840 but i just get the following from eagle stat

[i]Driver version 2.0.0     Chipset: Eagle0
Vendor ID : 0x1110     Product ID : 0x9031   Rev: 0x200b
USB Bus : 002    USB Device : 002        Dbg mask: 0x0
Ethernet Interface : none
MAC: 00:60:4c:68:b8:e3
Tx Rate           0  Rx Rate           0
FEC               0  Margin            0  Atten             0 dB
VID-CPE           0  VID-CO            0  HEC               0
VPI               0  VCI               0  Delin          GOOD
Cells Tx          0  Cells Rx          0
Pkts Tx           0  Pkts Rx           0
OAM               0  Bad VPI           0  Bad CRC           0
Oversiz.          0

Modem waiting for driver response.
Please send DSP (eaglectrl -d)

root@Crystal:/home/hg80 # eaglectrl -d
Can't find any PRE or POST firmware devices.
Is your device plugged in ?[/i]

Any help would be welcomed so then i can ditch Windows for my office and internet use  :grin:

---

### Post by topa on 2005-09-03
Yesterday I installed ubuntu and I also got my modem (sagem fast 800) up and running, but today I had exactly the same problem as you and after reinstalling the eagle usb driver I got everything up and running again. But I think next time I restart my pc it won't work again. So I also need some help about this problem.

tony

---

### Post by topa on 2005-09-13
I found out something.
After the install I go to a terminal window and I do the next:

[COLOR=Blue]sudo eagleconfig[/COLOR]

after configuration

[COLOR=Blue]sudo startadsl[/COLOR]

after reboot it doesn't find my modem up till now I reinstalled it but the only thing you need to do in a terminal window is:

[COLOR=Blue]sudo eaglectrl -w[/COLOR] 

and the next is:

[COLOR=Blue]sudo startadsl[/COLOR]

So this means the modem isn't started at boot time.

You can find more on the eagle-usb faq. Just visit their site.

hope it was helpfull.

greetz 
tony

---

