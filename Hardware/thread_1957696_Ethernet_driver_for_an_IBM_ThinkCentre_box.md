---
title: "Ethernet driver for an IBM ThinkCentre box"
date: 2012-04-13
forum: Hardware
---

### Post by HandOfReform on 2012-04-13
I have an IBM ThinkCentre machine that I got from work to set up a server on. When I got this I actually got 2 machines, one of them I set up a DHCP/DNS server on using ClearOS. ClearOS immediately detected both NICs. One of them is onboard, while the other is a PCI NIC. The first is listed as:

[SIZE=-2]Intel Corporation 82562EZ 10/100 Ethernet Controller

While the, I'm assuming PCI card is: 

[/SIZE][SIZE=-2]VIA Technologies, Inc. VT6105/VT6106S [Rhine-III]

Now, on this second box, I'm 80% certain that it is the exact same board as the ClearOS box, meaning, that if I'm correct about the first ethernet controller, that it would have the 82562EZ ethernet controller. However, upon installing Ubuntu 10.04, I have no wired network. I have attempted to automatically download updates and the what not, and I know a driver for this must exist as ClearOS is a separate distro, and usually, in my experience, if there's a Linux driver, there's a Linux driver, irregardless of the distro. So I've tried grabbing a driver for it from Intel's site, however I'm not quite advanced enough of a user to actually know what I'm doing with it, in the read-me it wants me to build an RPM from the tar.gz, that was the first step, and the first step that I got an error on. 

Now there's a few possibilities here, the first is that it's a bad NIC, which I would not be overly surprised about, considering the age of the machine, however in my experience, IBM's are the computer equivalent of the Nokia brick phones from the 90's so, I sort of doubt that it's going bad. 

The second possibility is that I just don't know what I'm doing. There may be another way to get the driver, or maybe I need to switch Ubuntu versions or something like that.

The third, and as far as I've pondered, final, possibility is that it is not in face the Intel 82562EZ controller, whether I just be mistaken about which is which in the ClearOS box (which I doubt because the whole chipset of the board in that box is Intel based, so I would assume the ethernet controller would be as well), or I'm mistaken about the 2 IBM boxes being identical (which seems more likely to me). 

If it is the third choice, then I'm sure it's easy to find out, coming from a Windows environment, I would typically go into device manager and find the hardware ID of the NIC and google that to find out exactly, however I haven't found an equivalent of Device Manager to use in this specific incident.

Any help that you all can provide would be extremely appreciated as I'd like to get this box set up on the Network as soon as possible.
[/SIZE]

---

### Post by HandOfReform on 2012-04-13
Shameful self bump.

---

