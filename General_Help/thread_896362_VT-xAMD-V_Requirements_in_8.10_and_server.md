---
title: "VT-x/AMD-V Requirements in 8.10 and server"
date: 2008-08-21
forum: General Help
---

### Post by bthoward on 2008-08-21
So when trying to run 8.10 in Virtualbox with 8.04 as a host I'm unable to boot the system.  I have this same problem with 8.04 server.  I filed a bug on server for this and it was closed saying that all I need to do is enable VT-x/AMD-V.  Problem is that my laptop (Dell D610) doesn't seem to support these features.  I've grepped the processor features and searched high and low in the bios and there is nothing to turn on to allow these things.  

So I'm hoping that this only prevents me from running these OSes in a VM.  Once 8.10 is released will I be able to install it natively on this machine or am I just screwed until I upgrade to a new laptop?  With this thing running at 2Ghz with 2G of RAM I honestly don't really need much more system for a beater laptop at the moment.  At work sure but at home for just screwing off this is more than enough.  

Some day I'll get a sub compact but probably not until this thing croaks.

---

### Post by amitkher on 2008-08-21
Can you give the bug number here?

VT-x and AMD-v should be required only when running the virtual machine in fully virtualized mode. There should always be a software virtualization mode where these processor features are not required. This software virtualization mode is slightly slower than the full virtualization but it gets the job done.

Yes, it only prevents you (if that) to run the OS in a VM. You can always install it on the laptop and it would run fine.

Note that desktops have started to get VT processors for more than 3 years now. Laptops still generally don't get this feature, and it is unlikely in the future. Laptop processors get other features though e.g. much more advanced power throttling to save battery.

---

### Post by bthoward on 2008-08-21
Looks like it got lumped into a duplicate:

[https://bugs.launchpad.net/bugs/151942](https://bugs.launchpad.net/bugs/151942)

Anyway I've not seen any way to get the thing to run in a software virtual mode.  I've yet to successfully get an 8.10 ISO to boot in VirtualBox with an 8.04 host on my Dell D610. 

I can boot XP and other 8.04 iso's and I have a fedora install and a suse install and several other dedicated firewall distros and they all work but 8.10 and server are a no go.

A similar report of what is being seen with 8.10 can be found here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246067](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246067)

---

### Post by amitkher on 2008-08-21
In virtualbox, for settings of your virtual machine, click on general. In advanced tab, you will find a checkbox for Enable VT-x/AMD-V. Sun has enforced its trademark horrible retarded button-scheme on virtualbox but you can try keeping this in all 3 states it can be in and try booting your virtual machine. Hope it fixes your problem.

---

### Post by bthoward on 2008-08-22
I end up getting a kernel panic just trying to select install ubuntu with the intrepid 8.10 discs with the setting in all 3 states...

So what is it about the new stuff that makes them require this CPU feature to be virtualized but its not needed when installed natively?

---

