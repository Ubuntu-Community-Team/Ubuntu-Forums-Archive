---
title: "BeWAN PCI ADSL Modem in Ubuntu Help"
date: 2005-03-23
forum: Hardware &amp; Laptops
---

### Post by wellso on 2005-03-23
Hello there everyone, im a newbie to Ubuntu and Linux in general.

I recently purchased a BeWAN PCI ADSL modem due to its compatibility with Linux, but due to my lack of knowledge and experiance in Linux I an completely stumped when going about installing it. I have included the installation instructions (which I think are a bit vague) and was wondering if any Ubuntu expert could give me some tips or tricks for installation of this device? 

Please bear in mind that I have no Internet access from my Ubuntu installation, so any additional pakages will have to be obtained manually. Heres an extract of the installation file:

> INTRODUCTION:

The software for the UNICORN ADSL PCI card consists of two loadable drivers, 
the unicorn_atm.o and unicorn_pci.o. The unicorn driver is a standard Linux 
ATM driver, that performs segmentation and reassembly (SAR) and flow control.
The unicorn_pci driver contains the ADSL modem software and hardware related
functions. It has been tested with the Linux 2.4.x kernels. Note that to use
PPPoE, PPPoA or RFC2684 protocols, the kernel may need to be patched.

COMPILATION:

To compile the drivers, unzip and untar the file. In the unicorn directory you 
will find the two subdirectories unicorn_atm and unicorn_bus.
You may compile the drivers based on the include files in the kernel source
or standard kernel include files. Set the variable KERNELDIR in the Makefile's
to point to your kernel sources if the first option in chosen. 
If you choose the latter, you may need to copy the contents of the kernel 
source "include/net" directory into "/usr/include/net/".
Go into these subdirectories and do a "make" and a "make install".
If the compile option "USE_HW_TIMER" is set, the performance is increased, 
but the CPU load increased. 
Use the same compiler as you use when compiling the linux kernel. The driver has
been tested using gcc-2.96, gcc-2.95.2, gcc-2.91.66 and gcc 3.0.3.


INSTALLATION:

To start the ADSL software, do a "modprobe unicorn_pci". Check in the syslog that
the drivers are started OK. The ADSL line should come up automatically. The status
can also be checked using the "proc" interface (/proc/net/atm/UNICORN\:0". 
SHOWTIME in the log or in the status means that ADSL connction is up and ATM cells
may be transmitted and received.
Depending on your network setup, you will need additional software as with any other
ADSL ATM card. For bridged ethernet (RFC2684), the br2684.o module and brctl is needed.
For PPPoE, any pppoe client over the bridged interface (nas0) should work 
(Roaring Penguin pppoe client has been tested). 

Thanks for any help availible ppl, I really appreciate it

---

### Post by wellso on 2005-03-23
Attached the full documentation here.

---

### Post by www.rzr.online.fr on 2007-12-24
**This post could be related to an Ubuntu bug filed at**: [http://rzr.online.fr/q/unicorn](http://rzr.online.fr/q/unicorn) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **wellso said:**
> Hello there everyone, im a newbie to Ubuntu and Linux in general.

I recently purchased a BeWAN PCI ADSL modem due to its compatibility with Linux,


can you show us the results of :
lspci

---

