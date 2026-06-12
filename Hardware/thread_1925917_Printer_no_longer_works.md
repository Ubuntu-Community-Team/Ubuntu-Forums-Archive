---
title: "Printer no longer works"
date: 2012-02-15
forum: Hardware
---

### Post by WA1DH on 2012-02-15
I switched from ubuntu to xubuntu since I found I liked xfce better than unity. The only issue I am having so far is that my printer no longer seems to work. I have a Brother Intellifax 1860C which used to work fine under ubuntu. I went ahead and installed the CUPS and LPR drivers in synaptic (packages brother-lpr-drivers-bh7 and brother-cups-wrapper-bh7), but when I go to add a printer I only see 'Serial Port #1', 'Enter URI' and 'Network Printer' as options. I used to be able to see the Brother driver in that column when I went to add the printer. Note that this is a USB printer, not serial, and everything is connected and the printer is powered on.

I went into CUPS at [http://localhost:631/admin](http://localhost:631/admin) and tried clicking 'Add Printer', but it is asking me for a username and password which I don't have. I tried my root password but that isn't working.

Anyone know how can I get my printer working again?

Thanks.

Edit:
If it means anything, lsusb reports this:
Bus 010 Device 009: ID 04f9:01bb Brother Industries, Ltd

---

### Post by WA1DH on 2012-02-18
I have still not had any luck with this. The only conclusion I can come to is that there is some package which is not installed by default in xubuntu which is installed in ubuntu. I'm beginning to wonder if it was a mistake to do a clean install of xubuntu...

Any ideas on this? I really need to get this printer working again.

---

