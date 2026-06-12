---
title: "Wi-Fi Problem in Lenovo 7757"
date: 2010-12-24
forum: Hardware
---

### Post by gpdas on 2010-12-24
Hi, I am using Ubuntu 10.04 in my Lenovo 7757 laptop. My Wi-Fi is not working. Any help will be appreciated.

---

### Post by mikewhatever on 2010-12-24
Any idea what the wifi card model is? If not, post the output of the following:

lspci | grep -i net

---

### Post by gpdas on 2010-12-24
It is 04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (Rev 01)

---

### Post by mikewhatever on 2010-12-24
That card works well (have one myself), but requires the proprietary Broadcom driver installed. Hook up an ethernet cable, then you should get a popup about additional available drivers.

---

### Post by kevein on 2010-12-25
Thanks dear I am trying to search for it.

---

### Post by gpdas on 2010-12-26
Sorry Mikewhatever,
I have connected ethernet. Through this I browse Internet. But no Pop-Up comes to configure wireless lan. Can you just give me a link to download that driver to install in my laptop? Or installing whole s/w again will solve the problem? pl guide me..

---

### Post by mikewhatever on 2010-12-26
That's odd, anyway, the driver is in the repositories. Try System->Administration->HardwareDrivers for graphical interface. Alternatively, run **sudo apt-get install bcmwl-kernel-source**.

---

### Post by gpdas on 2011-01-07
In Ubuntu Software Centre, I searched 'Broadcom'.
Then I installed two items.
1) Broadcom 802.11 Linux STA Wireless Driver Source
2) Common Files for Broadcom  Wireless Driver

Now its working OK.

---

