---
title: "Hp Compaq 6715s hardware issues"
date: 2008-11-10
forum: Hardware
---

### Post by natschil on 2008-11-10
This is a thread dedicated to hardware related problems related to the Hp Compaq 6715, and possible fixes. Please feel free to post any fixes or further problems in this thread.

Hardware :
AMD Turion(tm) 64 X2 Mobile Technology TL-60
ATI X1250 Graphics Card - Works  very well with the propetary ati fglrx driver
Broadcom Network Card - Works with the tg3 kernel module, no setting up required. 
Bluetooth - Not tested
Broadcom Wireless- Worked well in hardy, but stopped working now. Unknown whether this is a hardware or software issue.

Using Kubuntu Intrepid, but these problems are probably also there in Ubuntu Intrepid.
Generally, I have found that this laptop works quite well, but after kernel 2.6.27 there have been several issues:
Firstly, without adding something similar to noapic as a kernel boot argument, there is a problem with acpi, causing the processor speed to go down seriously. Even with this boot argument, only one of the two processors is used. 

Broadcom Wireless - strangely, the output of lspci does not show me the Broadcom wireless card, it only does so if I add the -H1 argument to lspci. Sometimes it works without it, and sometimes this doesn't even work. I do not know whether this is the hardware's fault or not. On Windows Vista the wireless works. 

These problems were also in Gentoo on the same laptop.

Otherwise, this laptop works quite well on ubuntu

---

