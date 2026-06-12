---
title: "Intel PRO/Wireless 2200 driver"
date: 2009-03-18
forum: Hardware
---

### Post by Beaslah on 2009-03-18
I just installed Ubuntu 8.04.2, kernel 2.6.24-23-generic on an old Dell Latitude D610 and I'm trying to install the driver for it's Intel PRO/Wireless 2200BG card.  Unfortunately the Synaptic Package Manager didn't find it, but I was able to download the ipw_2200 driver from Intel's website.  It's a tar file.  Does anybody know how to install all the files into their proper directories when I unzip it to make the driver work?  I didn't see any instructions with it.

---

### Post by mikewhatever on 2009-03-19
I don't think you need to install anything. The driver should be loaded and working.

---

### Post by Beaslah on 2009-03-19
The wireless isn't working properly.  It can see my router when I switch to the wireless connection, but doesn't get an IP address when I connect to the router over he wireless so I have to use a wired connection instead.

---

### Post by stchman on 2009-03-19
> **Beaslah said:**
> I just installed Ubuntu 8.04.2, kernel 2.6.24-23-generic on an old Dell Latitude D610 and I'm trying to install the driver for it's Intel PRO/Wireless 2200BG card.  Unfortunately the Synaptic Package Manager didn't find it, but I was able to download the ipw_2200 driver from Intel's website.  It's a tar file.  Does anybody know how to install all the files into their proper directories when I unzip it to make the driver work?  I didn't see any instructions with it.

That wireless card works OOB with Hardy.  I have an Intel 4965agn that works perfectly with Hardy.

---

### Post by mikewhatever on 2009-03-20
> **Beaslah said:**
> The wireless isn't working properly.  It can see my router when I switch to the wireless connection, but doesn't get an IP address when I connect to the router over he wireless so I have to use a wired connection instead.

Without the driver, your wireless device would have been undetected and non-functional. If you can see your wireless network, I think that means the driver is loaded and functioning, and something else is the problem. If you want help troubleshooting, post some relevant info:

sudo lshw -C network
ifconfig
iwconfig
dmesg | grep iwl

---

