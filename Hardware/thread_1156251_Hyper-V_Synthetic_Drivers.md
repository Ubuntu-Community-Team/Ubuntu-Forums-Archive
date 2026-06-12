---
title: "Hyper-V Synthetic Drivers"
date: 2009-05-11
forum: Hardware
---

### Post by matthew.mattoon on 2009-05-11
Does the Ubuntu team have any plans on implementing support for Microsoft's Hyper-V Virtualization platform Synthetic Drivers?

I understand that Ubuntu works with Emulated Drivers, however these perform much worse on a production server.

Microsoft has the Integration Components, which as far as I can tell builds a couple of kernel modules for the Synthetic devices, however they way they do it appears to only work on linux kernel 2.6.20 and prior which is pre-Hardy which is not really helpful for most.  The issue seems to be related to a change in how INIT_WORK is implemented.

It seems like Ubuntu could better implement this "hardware" within the distro, and at the same time create a niche market.

Does anyone have any experience installing the Hyper-V Integration Components into Ubuntu 8.04, 8.10, or 9.04?

---

### Post by nebosphere on 2009-05-11
I recently made an attempt (and hence a total mess out of my ubuntu install) to install the MS LIC on Intrepid.  I've read some posts about installing the Xen 3.3 hypervisor and Xen-ified kernal but I am still rather new to Linux and couldn't get all the way there. Also, I couldn't find a post that indicated success with this configuration and the LIC specifically anyway so I'm really not sure if it's worth the effort.  

Anyone out there get this to work?

---

### Post by matthew.mattoon on 2009-05-12
I have been working on this non-stop since I posted this comment and I have finally made some traction. I still think this is better implemented as hardware instead of kernel modules, however this is what I did to work around it documented fully...
 
[http://blog.allanglesit.net/Blog/tabid/66/EntryId/22/Hyper-V-Guests-Linux-Integration-Components-Ubuntu-and-Debian.aspx](http://blog.allanglesit.net/Blog/tabid/66/EntryId/22/Hyper-V-Guests-Linux-Integration-Components-Ubuntu-and-Debian.aspx)[]("http://blog.allanglesit.com/2009/05/hyper-v-guests-linux-integration.html")
 
 
-matt

---

