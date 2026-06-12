---
title: "Noob help with virtual Install"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by gwmbox on 2009-03-30
Is it possible to install a 64 bit version on a Vista PC running 32 bit version of Vista?

I want to test out Ubuntu and see if it is better before I go and do a dual boot etc, but would like to test out the 64 bit capabilities.

System is Q6600, 4GB Ram blah blah....  I was trying to get it to install in Virtual PC with 20GB space and 1024 Ram allocated but it comes up saying that the Q6600 is an i686 and not 64 bit - but I know the Q6600 is 64 bit....

Cheers for you help

---

### Post by dandnsmith on 2009-03-30
My thinking would be:
not at all surprised, as you can't get more on the virtual PC than the OS it's installed under will give you.
So, you can only get a 32-bit OS on the virtual PC.

- or does anyone have experience to the contrary?

---

### Post by namaku0 on 2009-03-30
That depends on the virtualization software. VirtualBox
does support running 64-bit guest on a 32-bit host.

> 
Starting with Version 2.0, VirtualBox also supports 64-bit guest operating systems. Starting with Version 2.1, you can even run 64-bit guests on a 32-bit host operating system, so long as you have sufficient hardware.
In detail, 64-bit guests are supported under the following conditions:

- You need a 64-bit processor with hardware virtualization support (see Section 1.2, &#8220;Software vs. hardware virtualization (VT-x and AMD-V)&#8221;).

- You must enable hardware virtualization for the particular VM for which you want 64-bit support; software virtualization is not supported for 64-bit VMs.

Note
On most systems, the hardware virtualization features first need to be enabled in the BIOS before VirtualBox can use them.

- If you want to use 64-bit guest support on a 32-bit host operating system, you must also select a 64-bit operating system for the particular VM. Since supporting 64 bits on 32-bit hosts incurs additional overhead, VirtualBox only enables this support upon explicit request.
On 64-bit hosts, 64-bit guest support is always enabled, so you can simply install a 64-bit operating system in the guest.

Warning
On any host, you should enable the I/O APIC for virtual machines that you intend to use in 64-bit mode. This is especially true for 64-bit Windows VMs. See Section 3.7.1.2, &#8220;"Advanced" tab&#8221;. In addition, for 64-bit Windows guests, you should make sure that the VM uses the Intel networking device, since there is no 64-bit driver support for the AMD PCnet card; see Section 6.1, &#8220;Virtual networking hardware&#8221;.
If you use the "Create VM" wizard of the VirtualBox graphical user interface (see Section 3.2, &#8220;Creating a virtual machine&#8221;), VirtualBox will automatically use the correct settings for each selected 64-bit operating system type. 


---

