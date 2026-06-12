---
title: "PCI Ethernet advice"
date: 2010-07-06
forum: Hardware
---

### Post by ReeceWeb on 2010-07-06
Hello,

I'm setting up a system to run my CNC milling machine, and I am having trouble with the on-board ethernet.  I'm installing Hardy Heron from the [EMC2 live CD]("http://www.linuxcnc.org/content/view/21/4/").  The MLB is a [Gigabyte  GA-G31M-ES2L]("http://www.gigabyte.us/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=3136&ProductName=GA-G31M-ES2L"), which seems to work very well, except that the NIC isn't recognized.  [This blog]("http://dtbaker.com.au/random-bits/ubuntu---ethernet-controller-attansic-technology-corp.-device-1063-rev-c0-.html") tells me how to get the NIC supported, but it requires network access to get the required packages to build the driver.

I tried getting the [packages]("http://packages.ubuntu.com/hardy/devel/build-essential") from my Mac and moving them over via memory stick, but quickly found it very hard to handle the seemingly unbounded dependency chain.

I am a Linux noob, so I figured the easiest way out was just to buy a cheap NIC supported by the default install.  I could just use that as my NIC, or I could use it to get the on-board NIC going.  But, I can't seem to find a good list of NICs that the live CD install will support.

Any advice you can provide regarding a supported NIC, or other way to solve this issue would be greatly appreciated.

Cheers,
 - Dean

---

