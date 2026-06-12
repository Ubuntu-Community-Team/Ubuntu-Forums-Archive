---
title: "New W510 Thinkpad -- Can't install Ubuntu"
date: 2010-06-07
forum: Hardware
---

### Post by dwinner on 2010-06-07
Just got a new W510 last week. Exact model is a 4319-2PU.

On Friday I tried to install Lucid 10.04. "No network interfaces were found."

Tried this morning 8.04. Same thing.

I exited from the installer to a shell and ran "lspci"

Everything is coming up as "Unknown device", starting with

Host bridge: Intel Corporation Unknown device d132 (rev 11)
PCI bridge: Intel Corporation Unknown device d138 (rev 11)
System Peripheral: ""
...
Ethernet Controller: Intel Corporation Unknown device 3b64 (rev 11)
etc., EVERYTHING Unknown

This is not good! We were getting ready to hit the button to buy a whole bunch of these W510's, and I can't even get Ubuntu installed.

I've seen others who installed on a W510, even the 4319-2PU model I have ([http://www.mikesubuntu.com/2010/05/new-computer-new-ubuntu-new-topics](http://www.mikesubuntu.com/2010/05/new-computer-new-ubuntu-new-topics))

So what's /my/ problem? Did Lenovo maybe just install a new chipset and there are no drivers ready yet?

Any ideas?

---

### Post by dwinner on 2010-06-07
Update: 

It seems the problem is with 64-bit Ubuntu. I just threw in my 32-bit install live CD, and it was able to detect all the hardware, including the network card just fine. 

Any ideas on why 64-bit Ubuntu is throwing a fit a W510?

It shipped with Windows 7 64-bit, and that is working fine.

---

