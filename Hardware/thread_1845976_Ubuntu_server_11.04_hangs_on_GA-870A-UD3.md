---
title: "Ubuntu server 11.04 hangs on GA-870A-UD3"
date: 2011-09-18
forum: Hardware
---

### Post by redscorp on 2011-09-18
Hi All!

I've build my small home server based on following HW:
MB: Gigabyte **GA-870A-UD3** Rev. 3.1
CPU: **AMD Athlon II X4 615e** 2.50GHz
RAM: 8GB **Exceleram Black Sark DDR3-1333** Dual Kit
Graphics: 512MB **EVGA GeForce 8400GS**
Power: 1000W **Cooler Master Silent Pro M1000** 80+ Bronze Modular
HDD: **4x** 3000GB Western Digital Caviar Green **WD30EZRX** SATA 6Gb/s (in software RAID)

Now I have problem: my server hangs regularly during high network/HDD load (I've copied several thousands of files over NFS). After I connect a display to hung server I see nothing except garbage on the screen. The system is also reacts no on any keyboard activities and on short press of power button (long press of course makes his dirty business). So I suspect that problem is located somewhere in HW area.

I think about my MB GA-870A-UD3 as a most probable harm maker here and especially Realtek 8111D/E network chip it is equipped with. This chip when soldered on Gigabyte MBs is known to behave buggy under linux. I own another system based on MB GA-EX58-UD5 equipped with a couple of Realtek 8111D where linux OS sometimes (50/50) detects no network activity. So I'm assuming that design of Gigabyte MBs is somehow not compatible with linux.

Can anyone confirm my thoughts are right? Or maybe someone can even suggest how to fix earlier described behavior of my Ubuntu server box.

Thanks in advance!

---

