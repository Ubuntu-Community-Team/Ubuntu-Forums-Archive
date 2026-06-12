---
title: "Choosing a PCI NIC card with Ubuntu support"
date: 2014-06-15
forum: Hardware
---

### Post by Riothamus on 2014-06-15
My desktop computer is a 2011 Asus Essentio model AMD Athlon™ II X2 Processor-CM1630RF-05 with a 64-bit architecture. It's partitioned with Windows 7 and Ubuntu 12.04 LTS. The NIC is integrated onto the motherboard.

It seems a recent thunderstorm shorted out the NIC, because the computer is now always saying there's no network connection, and other computers are able to connect to the Internet using the same ethernet cable that I'm plugging into the computer. Also, the LED light on the ethernet port is now always lit, whereas it only used to light up while data was being transferred (it would flicker as I downloaded content from the Internet). When I've run the Windows Troubleshooter, it says it can't find an installed network adapter and that I may need to install the driver, but when I go to the next step, it says Windows can't find a driver for the installed network adapter. (The NIC is a Realtek one.) I've tried downloading the driver from the Asus website, and it installs fine, but then at the end, says it can't find any network controller installed. Additionally, there's no option to disable the NIC or network adapter in the BIOS or in Windows Device Manager. It's like the computer does not know that it exists. I've also even tried removing the CMOS battery for 20 minutes to see if that changed anything. All the system settings reset, but still no NIC recognized.

If there's anything left to try, please let me know. But I'm not sure what else to do besides buy a PCI NIC and see if that works. Since I want to be able to access the Internet from both my Windows and Linux partitions, can anyone recommend a NIC that has good Ubuntu support?

---

### Post by Yellow Pasque on 2014-06-16
Are you using anything in the PCI-e x1 slot? If not, that would be better than a PCI card.

---

### Post by Riothamus on 2014-06-16
I was just thinking the same thing. A PCIe x1 card will also be fine, if one can be found that has adequate Ubuntu support. There's also a PCIe x16 slot available, although I don't think I'll need to go that high, as I've never used terribly-fast Internet, so I may want to keep that open for something else.

ADD: The only reason I'm not buying another Realtek straight off the bat is because I have no knowledge of whether the PCI cards will be supported by Ubuntu just like the integrated motherboard one. If they will, then I've got no problem just buying a Realtek card.

---

### Post by Yellow Pasque on 2014-06-16
I'm using a Realtek 8111/8168D and it works. I also know that the RTL8111/8168E works, so something like this should work: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833114095](http://www.newegg.com/Product/Product.aspx?Item=N82E16833114095)

I would avoid RTL8111/8168B variant [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343).

---

### Post by Riothamus on 2014-06-16
Alright, thanks for the info.

---

