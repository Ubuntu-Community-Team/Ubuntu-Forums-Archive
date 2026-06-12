---
title: "Help with dmesg interpretation"
date: 2006-05-14
forum: Hardware &amp; Laptops
---

### Post by johnwren on 2006-05-14
I have installed 5.10 on an Athlon 64 3000+ with an ASUS A8N-E motherboard, and the usb system does not work properly (see post on the AMD 64 sub-forum).  Looking at the faq on linux-urb.org, it appears I may have a problem with the PCI bus.  When I look at the output of dmesg I have many questions -- and would appreciate help in understanding this output.

1) are all the initial 'interrupt disabled' messages re the ACPI PCI bus normal?  Do they suggest a problem?
2) how about the 'invalid irq' messages from pcie_portdrv_probe, with the 'check vendor bios'.  What is that about?
3) it appears the ring buffer is being over-flowed, as I don't see a line announcing the system name.  Can this be made larger?
4) following the suggestion in dmesg, I attempted to pass 'pci=routeirq' as a boot parameter.  How can I see if this was/wasn't sucessful?

Any help, guidance, or suggestions for further reading/research gratefully accepted.  My dmesg.txt is attached.

Thanks
John

---

### Post by knudsen83 on 2008-01-03
Iff you get or have got some response to your thread i would like to know it. I been having some problems with my computer freezing, so i would like to see if the problem is caused by some dirver disfunctionality or if it my machine that is the problem

---

### Post by johnwren on 2008-01-17
I now understand dmesg output better, and the problems I had have been resolved by more recent versions of ubuntu.  I'm now running Gutsy, 7.10 on that amd system with no problems at all, and on a Dell Latitude D531 with only one unresolved problem.  If you still need help with dmesg interpretation, please let use know what system you are running on, what version of ubuntu you use, and what problems you are having.  With luck, you already have the answers.
Thanks

---

