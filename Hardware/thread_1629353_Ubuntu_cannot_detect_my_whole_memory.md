---
title: "Ubuntu cannot detect my whole memory"
date: 2010-11-23
forum: Hardware
---

### Post by yangjiangnan on 2010-11-23
Help needed. 
I bought HP Pavilion dv6 with 64bit Windows 7, i5core CPU and 6GB ram memory (2GB+4GB). Then I installed  32 bit Ubuntu Linux 10.04 (updated to 10.10 now), as 32 bit was recommended by the official website. However, in the System Monitor, it says that I have only 2.4 GiB memory (4.5 GiB Swap). I swithed the position of the two memory cards in my laptop but the problem still remains.
Does any body understand why this happens? How can I fix it (better without reinstall the whole system)?
Many thanks.

---

### Post by trundlenut on 2010-11-23
32 bit has a memory limit of 4gb unless you use the PAE kernel.

Try the 64 bit version instead.

Look at [this]("https://help.ubuntu.com/community/32bit_and_64bit")

---

