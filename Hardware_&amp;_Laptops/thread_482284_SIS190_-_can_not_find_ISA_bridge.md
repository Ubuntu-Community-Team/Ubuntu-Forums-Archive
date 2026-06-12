---
title: "SIS190 - can not find ISA bridge"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by robertobech on 2007-06-23
I'm running feisty on an ECS motherboard. Everything works fine, except for the onboard Gigabit Ethernet. 

First, some info (edited to contain only the relevant info:

```
# lspci -v
00:04.0 Ethernet Controller: Silicon integrated systems (SIS) 190 Gigabit Ethernet Adapter (Rev 01)

# lspci -n
00:04.0 0200: 1029:0190

# dmesg | grep 00:04.0
0000:00:04.0: Can not find ISA bridge
sis190: probe of 0000:00:04.0 failed with error -5

```

I'm assuming this is a problem on the ISA bridge, right? And seems like sis190, the module, has a history of trouble with this:
[http://www.uwsg.iu.edu/hypermail/linux/kernel/0405.2/0157.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0405.2/0157.html)

I've got the kernel source, so I can fix the sis190.c. But what should I do to fix it? It seems like everything lies on these lines:
 
```

        isa_bridge = pci_get_device(PCI_VENDOR_ID_SI, 0x0965, NULL);
        if (!isa_bridge) {
                net_probe(tp, KERN_INFO "%s: Can not find ISA bridge.\n",
                          pci_name(pdev));
                return -EIO;
        }

```

UPDATE: the ID of my ISA is 1039:0966... hm, there is a 0965 on the code of the driver. Maybe I should change it...

---

### Post by robertobech on 2007-06-23
Solved! Changed 0965 to 0966, compiled it and now it's working.

---

### Post by alexmatos on 2007-06-30
Could you please explain step-by-step how you got it working? I'm new on dealing with the kernel source and I've got the same problem here.

---

### Post by robertobech on 2007-06-30
Well, I don't remember the exact steps, but it's not as hard as it seems. You won't even need to compile a kernel :-)

You'll need to compile a new sis190 module. This module comes packed in the kernel package, so you must get the kernel source that matches your current kernel version. To discover what kernel version you're running, type uname -r, and then apt-get install linux-source-2.6.20 or something like that. Once you get the source, go to /usr/src and you should see a tar.bz package of the source. Untar it. Now cd to linux-source-2.6.20/drivers/net - I guess thats the correct path. There you'll find this file called sis190.c, that is, the source code of the sis190 module.

I forgot to mention, you'll need build-essential to compile this module, so apt-get it. Then open sis190.c on your favorite text editor and look for these lines:

```

        isa_bridge = pci_get_device(PCI_VENDOR_ID_SI, 0x0965, NULL);
        if (!isa_bridge) {
                net_probe(tp, KERN_INFO "%s: Can not find ISA bridge.\n",
                          pci_name(pdev));
                return -EIO;
        }


```

This "0x0965" refers to the ISA bridge. That is the problem: it's looking in the wrong place!!! That's not 0965, at least on my PC. You can find out the correct number by issuing an "lspci | grep ISA" command. I got this result here:

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)

The important part here is "00:02.0" - it may be different on your PC, so check it. Now do an "lspci -n | grep 00:02.0". I got this:

00:02.0 0601: 1039:0966 (rev 59)

1039:0966 is the answer. To be more precise, 0966. So I substituted 0x0966 for 0x0965 on the sis190.c file.

Now you must compile the new module. And then... man, I forgot how I compiled it... I guess I have the instructions around here, I'll look for it. Now try to get to this point and post here, and then I'll keep telling you what to do.

---

### Post by robertobech on 2007-07-01
Ha! Found it! I knew I would end up forgetting how I had done it, so I sent myself an email with the procedures :-)

To compile the module, after having downloaded the source and doing all the stuff I have already mentioned, go to /usr/src/cd linux-source-2.6.17. Then:

```
sudo make menuconfig
```

Select Exit and Yes to save configuration. Then :

```

sudo make drivers/net/sis190.ko
sudo rmmod drivers/net/sis190.ko
sudo cp drivers/net/sis190.ko /lib/modules/`uname -r`/kernel/drivers/net/
sudo modprobe sis190
```

Line 1 compiles the driver. Line 3 will put the newly compiled module in it's proper place. Line 4 loads the new module. Now it should work.

...

Guess I'm being pretty stupid... maybe I could just send you my compiled module, and then all you would have to do is to copy it to the proper place and load it... 

Ok, let's try it. It's attached on this message. Once you get the file unload your current sis190.ko module with a "sudo rmmod sis190" command. I suggest you make a backup of the current module, just in case you screw up something:

cd /lib/modules/`uname -r`/kernel/drivers/net/
cp sis190.ko sis190.ko_bk

Unzip the file I sent you and place the sis190.ko file in /lib/modules/`uname -r`/kernel/drivers/net/

Now, sudo modprobe sis190 and cross your fingers!

---

### Post by alexmatos on 2007-07-01
Hey man! Thanks for the quick answer. I really appreciate the help. I'm an Ubuntu user for almost a year and now I'm trying to put my girlfriend's computer to work with Ubuntu 7.04. It's being harder than I thought. I always solve my problems with an internet connection and since that one needs the onboard network to work, I have to download everything at home and take there (that's a very annoying thing) so I guess I'm going to choose the second option and use your compiled module. For that to work, I think you would have to be running the same Ubuntu version I am, right? Just to make sure, I'm going to create a repository CD with all packages I may have to use. Thanks in advance for your help and sorry for some english mistakes (I'm brazilian and it's been a while since I practised for the last time).

---

### Post by robertobech on 2007-07-01
> **alexmatos said:**
>  Thanks in advance for your help and sorry for some english mistakes (I'm brazilian and it's been a while since I practised for the last time).

Haha, eu sou brasileiro tambem :-)

But let`s keep the conversation in english, since english is the main language here. But you can always email me in portuguese if you will :-)

robertobech at gmail.com

---

### Post by alexmatos on 2007-07-01
> **robertobech said:**
> Haha, eu sou brasileiro tambem :-)

But let`s keep the conversation in english, since english is the main language here. But you can always email me in portuguese if you will :-)

robertobech at gmail.com

Thanks, man. I agree that we should speak english here, since this problem may be somebody else's problem some day. I'll try the procedure and come back here for the results (hopefully through the computer in question).

I thought about what you said before and I'm not sure if using your module would work. Only if I get the same 0966 result. Anyway, I'm preparing myself to do everything you have detailed.

I'll only have time to visit my girlfriend's computer on thursday, so until there you won't hear from me. Thank's again, and if this works, I'll email you.

---

### Post by sdg988 on 2007-07-03
> **robertobech said:**
> Ha! Found it! I knew I would end up forgetting how I had done it, so I sent myself an email with the procedures :-)

To compile the module, after having downloaded the source and doing all the stuff I have already mentioned, go to /usr/src/cd linux-source-2.6.17. Then:

```
sudo make menuconfig
```

Select Exit and Yes to save configuration. Then :

```

sudo make drivers/net/sis190.ko
sudo rmmod drivers/net/sis190.ko
sudo cp drivers/net/sis190.ko /lib/modules/`uname -r`/kernel/drivers/net/
sudo modprobe sis190
```

Line 1 compiles the driver. Line 3 will put the newly compiled module in it's proper place. Line 4 loads the new module. Now it should work.

...

Guess I'm being pretty stupid... maybe I could just send you my compiled module, and then all you would have to do is to copy it to the proper place and load it... 

Ok, let's try it. It's attached on this message. Once you get the file unload your current sis190.ko module with a "sudo rmmod sis190" command. I suggest you make a backup of the current module, just in case you screw up something:

cd /lib/modules/`uname -r`/kernel/drivers/net/
cp sis190.ko sis190.ko_bk

Unzip the file I sent you and place the sis190.ko file in /lib/modules/`uname -r`/kernel/drivers/net/

Now, sudo modprobe sis190 and cross your fingers!


This is good, but the module file you attached looks like an empty .gz file (69 bytes??)
Can you reattach with the proper file?
Also, I'm assuming the platform is i686?

Thanks!

---

### Post by robertobech on 2007-07-17
> **sdg988 said:**
> This is good, but the module file you attached looks like an empty .gz file (69 bytes??)
Can you reattach with the proper file?


The file is ok, it's just a single module, so it's really tiny. Hope it works for you.

---

### Post by _logic on 2007-10-25
> **robertobech said:**
> Well, I don't remember the exact steps, but it's not as hard as it seems. You won't even need to compile a kernel :-)

You'll need to compile a new sis190 module. This module comes packed in the kernel package, so you must get the kernel source that matches your current kernel version. To discover what kernel version you're running, type uname -r, and then apt-get install linux-source-2.6.20 or something like that. Once you get the source, go to /usr/src and you should see a tar.bz package of the source. Untar it. Now cd to linux-source-2.6.20/drivers/net - I guess thats the correct path. There you'll find this file called sis190.c, that is, the source code of the sis190 module.

I forgot to mention, you'll need build-essential to compile this module, so apt-get it. Then open sis190.c on your favorite text editor and look for these lines:

```

        isa_bridge = pci_get_device(PCI_VENDOR_ID_SI, 0x0965, NULL);
        if (!isa_bridge) {
                net_probe(tp, KERN_INFO "%s: Can not find ISA bridge.\n",
                          pci_name(pdev));
                return -EIO;
        }


```

This "0x0965" refers to the ISA bridge. That is the problem: it's looking in the wrong place!!! That's not 0965, at least on my PC. You can find out the correct number by issuing an "lspci | grep ISA" command. I got this result here:

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)

The important part here is "00:02.0" - it may be different on your PC, so check it. Now do an "lspci -n | grep 00:02.0". I got this:

00:02.0 0601: 1039:0966 (rev 59)

1039:0966 is the answer. To be more precise, 0966. So I substituted 0x0966 for 0x0965 on the sis190.c file.

Now you must compile the new module. And then... man, I forgot how I compiled it... I guess I have the instructions around here, I'll look for it. Now try to get to this point and post here, and then I'll keep telling you what to do.

just want to thank you for this post... its already been 4 days since I started to work on that d#$% NIC.... although the 2.6.23 kernel from kernel.org has 0966 besides its 0995 default, my board has 0968 address so a little twitching did the trick... again thanks man!

---

### Post by _sunshine_ on 2007-10-25
HelP!  I couldn't untar it.  It says no such file or directory. :confused:

---

### Post by _polarix_ on 2007-10-29
For robertobech:
Very Good Work !!
Thank you!

---

### Post by scantan on 2007-11-05
I encountered the same problem ("ISA bridge not found") while trying to install Ubuntu (first 7.04 then 7.10) on an AmazonPC ([www.amazonpc.com.br](www.amazonpc.com.br)) with the ECS 761GXM-M motherboard that has an onboard SIS 190 NIC.

I compiled the driver following the instructions, on another computer with Ubuntu 7.10 (same kernel version) and with internet access. But the "make menuconfig" command returned a cryptic error message. Since I wasn't going to setup a kernel config, I managed to bypass the error message by running "make oldconfig" (at some point a command error message suggested such command).

I then copied the driver module to the target PC, unloaded the module, renamed the original driver, copied the new one, reloaded it and restarted the system.

And it worked. Thanks a lot. I was quite frustrating at first. Specially when I was trying to compile the module on a system running a different kernel version.

I hope this message (with the aditional keywords) can help others find the same solution.

Cheers,

---

### Post by TimMc on 2007-11-11
Hi All,

This is my first time on the ubuntu forums ^_^

I just tried to copy+paste the module posted on this forum and load it in Feisty Fawn but it didn't work (probably because it was compiled with 0966 instead of 0968 ).

I'm installing Gusty Gibbon again and will attempt to compile the sis190.c module.

Here's a little info about my system:

uname -r
```
2.6.22-14-generic
```

lspci | grep ISA
```
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
```

lspci -n | grep 2.0
```
00:02.0 0601: 1039:0968 (rev 01)
```

Does the Ubuntu 7.10 CD come with the kernel source? Is it installed by default?

FYI: I'm posting this message on another computer as the PC in question doesn't have internet access (hence wanting to compile a module to enable onboard LAN). 

I've a 128k connection shared with 5 other computers at the moment so downloading is kind of not an option :-(

Tim.

EDIT: Problem Solved
I put a 12 year old Intel S82557 100MBit NIC in the machine and Ubuntu 7.10 recognised it.

I still can't assure anyone that hardware sold in the past 5 years will be supported by linux distributions out of the box :-/

---

### Post by maximal73 on 2008-01-23
I'm using Ubuntu Gusty 7.10 on an Acer Extensa E261 that have all-in-one motherboard With SIS chipset and sis191 Gigabit Ethernet Adapter

Ubuntu Gusty 7.10 with kernel 2.6.22.14 don't find sis191 Gigabit Ethernet Adapter for Isa bridge addres  in driver (i see that right address in my case is 0968)

I install USB 10/100 Ethernet with Realtek chip and it work.

then I decide to mod sis190.c driver and recompile kernel. I download surce of last stable kernel 2.6.23.14 form [www.kernel.org](www.kernel.org)

I mod  /usr/src/Linux/drivers/net/sis190.c like this:

```
isa_bridge = pci_get_device(PCI_VENDOR_ID_SI, 0x0965, NULL);
	if (!isa_bridge)
		isa_bridge = pci_get_device(PCI_VENDOR_ID_SI, 0x0966, NULL);

	if (!isa_bridge)
		isa_bridge = pci_get_device(PCI_VENDOR_ID_SI, 0x0968, NULL);

	if (!isa_bridge) {
		net_probe(tp, KERN_INFO "%s: Can not find ISA bridge.\n",
			  pci_name(pdev));
		return -EIO;
	}
```

and I follow istractions for compile kernel ([http://symbolik.wordpress.com/2007/11/10/vanilla-kernel-26231-on-gutsy-gibbon/](http://symbolik.wordpress.com/2007/11/10/vanilla-kernel-26231-on-gutsy-gibbon/))

At reboot new driver sis190 is load and eth1 is found, but it seen don't work.

```
sudo lspci -v
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
        Flags: bus master, medium devsel, latency 0
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
        Subsystem: Foxconn International, Inc. Unknown device 0c9e
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at fdffc000 (32-bit, non-prefetchable) [size=128]
        I/O ports at fe00 [size=128]

sudo lspci -n
00:02.0 0601: 1039:0968 (rev 01)
00:04.0 0200: 1039:0191 (rev 02)

dmesg | grep 00:04.0
[   31.546354] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
[   31.546368] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   31.551697] 0000:00:04.0: Read MAC address from APC.
[   31.575481] 0000:00:04.0: Unknown PHY transceiver at address 1.
[   31.831157] 0000:00:04.0: Using transceiver at address 1 as default.
[   31.843300] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at dc998000 (IRQ: 16), 00:1c:25:4f:6a:9e
```

I try to configure eth1 by roaming, DHPC and also static IP, but always seem don't work

Somebody can help me ?

---

### Post by gareth_005 on 2008-01-25
I have the same problem as maximal73 but on an Asus P5S-MX SE mobo.

Ubuntu gutsy installed, I upgraded the hardy kernel, 2.6.24-4 and applied the sis190 patch, using this method:
  [https://lists.ubuntu.com/archives/ubuntu-users/2008-January/134789.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-January/134789.html)
No luck.

I also tried some prebuilt sis190.ko drivrs from the mobo driver disk as well as an update from asus for edubuntu but none of those worked either.

eth1   Link encap:Ethernet  HWaddr 00:1D:60:66:CF:B5  
          inet6 addr: fe80::21d:60ff:fe66:cfb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:31532 (30.7 KB)
          Interrupt:18 Base address:0xdead 
eth1:avah Link encap:Ethernet  HWaddr 00:1D:60:66:CF:B5  
          inet addr:169.254.8.213  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xdead 

**sudo lspci -v**
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
        Flags: bus master, medium devsel, latency 0
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 825e
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at feafcc00 (32-bit, non-prefetchable) [size=128]
        I/O ports at dc00 [size=128]
        Capabilities: [40] Power Management version 2

**sudo lspci -n**
00:00.0 0600: 1039:0671
00:01.0 0604: 1039:0003
00:02.0 0601: 1039:0968 (rev 01)
00:02.5 0101: 1039:5513 (rev 01)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.3 0c03: 1039:7002
00:04.0 0200: 1039:0191 (rev 02)

**dmesg | grep 00:04.0**
[ 6288.469915] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 18
[ 6288.469936] PCI: Setting latency timer of device 0000:00:04.0 to 64
[ 6288.485590] 0000:00:04.0: Read MAC address from APC.
**_[COLOR="Magenta"][ 6288.537507] 0000:00:04.0: Unknown PHY transceiver at address 1.[/COLOR]_**
[ 6289.044671] 0000:00:04.0: Using transceiver at address 1 as default.
[ 6289.077302] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f888ac00 (IRQ: 18), 00:1d:60:66:cf:b5

I think the problem is the line "Unknown PHY transceiver at address 1" but I don't know what to do about it.

Any help appreciated.

---

### Post by Fintan on 2008-03-10
I am having a problem getting the sis190 netwotk card to work on HH alpha 6 install.
The network notifyer sees the card as sis 190 and says "connected" but I cannot do a sudo apt-get install xyz, ping outside. Nada.

Will this patch work on a HH alpha 6 install?

---

