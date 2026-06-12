---
title: "Advantech DAQ PCI card"
date: 2010-09-08
forum: Hardware
---

### Post by patrick@vialis on 2010-09-08
Hi guys,
 
I'm new to the wonderfull world of Linux and I'm wondering if someone can help me with the following. I have an Advantech PCI-1730 I/O card. The Linux drivers from Advantech are very old and they don't want to deliver new ones for Ubuntu. They suggest I compile the drivers myself with the source. 
I succeeded to compile everything with a few minor tweaks and installed it. The drivers are loaded but for some reason it doesn't sees the I/O card. With the utility advdevice_list it should show all installed cards but it returns an error. 
 
Is there someone who has experience with these I/O cards/drivers or has suggestions what I can do next? 
 
Are there big changes in the kernel drivers of Ubuntu 10.04 LTS compared to the older distributions?
 
This is what Advantech supports:
**[SIZE=2]Red Hat Enterprise Linux 4  [/SIZE]**[SIZE=2]2.6.9-5-EL [/SIZE][SIZE=2]gcc-3.4.3-9.EL4 [/SIZE][SIZE=2]glibc-2.3.4-2 [/SIZE][SIZE=2]binutils-2.15.92.0.2-10.EL4[/SIZE]
**[SIZE=2]Fedora Core 6  [/SIZE]**[SIZE=2]2.6.18-1.2798.fc6 [/SIZE][SIZE=2]gcc-4.1.1-30[/SIZE][SIZE=2]glibc-2.5-3[/SIZE][SIZE=2]binutils-2.17.50.0.3-6[/SIZE]
**[SIZE=2]Debian 4.0  [/SIZE]**[SIZE=2]2.6.18-4-686 [/SIZE][SIZE=2]gcc-4.1.1-15 [/SIZE][SIZE=2]glibc-2.7 [/SIZE][SIZE=2]binutils-2.18.1[/SIZE]
**[SIZE=2]Red Hat Linux 9 [/SIZE]**[SIZE=2]2.4.20-8 [/SIZE][SIZE=2]gcc-3.2.2-5 [/SIZE][SIZE=2]glibc-2.3.2-11.9 [/SIZE][SIZE=2]binutils-2.13.90.0.18-9[/SIZE]
 
[SIZE=2]Many thanks.[/SIZE]
[SIZE=2]Patrick[/SIZE]

---

### Post by Fafler on 2010-09-08
Try giving us the output from lspci and if possible post a highres picture of the card or atleast the name of the chip.

I think theres a standard for such cards and i might be supported by adding vendor and device IDs to the right file.

---

### Post by patrick@vialis on 2010-09-15
Hi Fafler, thanks for ur reply. There is only one major chip on it from Lattice MachXO with type number LCMXO1200C.  
 
The output from lspci is:  
03:05.0 Class ff00: Advantech Co. Ltd Device 1730 (rev 10)
 
Is this helpfull?
 
Many thanks.
 
Regards,
Patrick

---

### Post by Fafler on 2010-09-15
I can't find anything but the official driver.
The Lattice chip is a PLD, a chip than can be programmed to do a number of things, so it doesn't really help. Neither does the device ID.

What about installing one of the officially supported Linux distributions for testing?

---

### Post by patrick@vialis on 2010-09-16
I found out that Ubuntu the card already automaticly detected and installed using a comedi driver. So maybe that's why the driver I compiled was not working?
 
Comedi seems a bit out-dated or is it still widely spead used and supported?
 
Should I try using the comedi driver or better de-install the comedi driver and use the official compiled driver? 
 
Many thanks.

---

### Post by Fafler on 2010-09-16
It could very well be the reason the other driver didn't work. Rmmod both drivers and modprobe the one from advantech. How did you get the comidi driver? It's not in my repository.

What do you need it for? The comidi drivers seems quite well documented. Theres even programming examples. [http://www.comedi.org/doc/index.html](http://www.comedi.org/doc/index.html)

---

### Post by patrick@vialis on 2010-09-16
On the driver CD from Advantech was also a folder "old linux driver" and this contained a comedi driver. Because it is said old I didn't use it. Since the "new" driver was not working I took a look at the comedi driver but the installation was rather complex and because it's old I didn't want to spend much time on it. 
 
How come a comedi driver is installed I have no idear. I only try the new driver so far. I can only think of that Ubuntu auto detect and installed the drivers. Is that possible?  
 
I unloaded the comedi driver like u said and now the advantech driver works too :D
 
How to remove the comedi driver permanent? I want to use the advantech driver in stead.
 
Many thanks for ur help so far

---

### Post by Fafler on 2010-09-17
It's quite possible Ubuntu installed the driver itself, i'm just wondering because it doesn't seem to be in my repository. Anyway, just follow this tutorial: [http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

---

