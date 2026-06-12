---
title: "Recognized PCIE-USB3.0 Expansion card not detecting any USB deiv"
date: 2017-12-17
forum: Hardware
---

### Post by ping42 on 2017-12-17
Hi all,

I have recently purchased several PCIe-USB3.0 expansion card to my server running the following spec:
Intel Xeon E5-2651 v2 1.80Ghz
Intel S2600CP

The purchased model of USB 3.0 expansion card is:
Orico 5-Port PVU3-5O2I-V1 ([http://www.orico.cc/goods.php?id=6584](http://www.orico.cc/goods.php?id=6584))
Orico 7-Port PVU3-7U-V1 ([http://www.orico.cc/goods.php?id=6585](http://www.orico.cc/goods.php?id=6585))

which should support Linux as described in the item description. 

After I have plugged in the expansion card into one of the PCI-E slot on my server board, plugged in the power cord,
booting up to Ubuntu 16.04 LTS, it did not recognize my USB drive plugged into the expansion card.

The chipset of expansion cards are VL805 Chip, which I am not sure if it is the chip causing such problem.

I have used "lspci" to check whether my expansion cards are being recognized, and it gave me the following result:
```

04:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)
...
83:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)

```

The USB drive plugged on the expansion card have lights, which indicates that it has power going through it.
I tried to look into the syslog inside /var/log, but it did not indicate anything after I plugged in my USB drive to the expansion card.
I have also tried to reinstall the OS as Windows Server 2012, but it also recognized the expansion card in Device Manager, but not be able to connect any USB device on it. 

I was confused and searched for solutions online for 2 days but nothing worked.
What could possibly be the problem and what further actions should I take?

Thanks.

---

### Post by tokyobadger on 2017-12-18
The Orico FAQ suggests symptoms such as yours could be caused by insufficient power. Try the 5-port by itself and see what happens.

---

### Post by ping42 on 2017-12-19
I have tried to plug one 5-port only, two 5-port only, and three 5-port on different PCIe slots.
There should be sufficient power since I am using 750W power supply and no display card is plugged.
The cable seems to be fine also.

---

