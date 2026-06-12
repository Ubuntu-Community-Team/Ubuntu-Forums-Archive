---
title: "PCI unsupported PM CAP Regs ..."
date: 2008-11-09
forum: Hardware
---

### Post by wzhang on 2008-11-09
Hi,

I have successfully  installed Ubuntu 8.10 64 bit on my laptop (Toshiba Satellite L305-S5908).  My network (wired and wireless) is working.  MY CD/DVD drive is working too. The build-in video cam seems to be working as well when I tested Skype.

But I am getting the following message every time  my laptop restarts (reboot):

"[ 0.789298] PCI   unsupported PM CAP regs Version (7)"

My best guess is  8.10 does not support one of  the hardware components in this laptop.   But what does the message mean?  What hardware is not supported?

The specification of the laptop can be found here:
[http://www.circuitcity.com/ccd/productDetail.do?oid=225182&cc_fm=Personalized+HP+Module#prodspecs](http://www.circuitcity.com/ccd/productDetail.do?oid=225182&cc_fm=Personalized+HP+Module#prodspecs)

Thanks,
-Wayne

---

### Post by echovolutionx on 2008-11-09
:confused::confused:try using other cap

---

### Post by raztus on 2008-11-16
I am getting the same error on a Toshiba Satellite A305-S6872.  Like parent, all of my devices seem to work ok (issues with the CPU fan and screen brightness on battery), but I get the same error at boot-up: "unsupported PM cap regs version (7)".

I'm new to linux, so fairly clueless as to what this means thanks!

~raztus

---

### Post by tsja-tosh on 2008-11-18
Same for me regarding: 

"[ 0.789298] PCI unsupported PM CAP regs Version (7)"

Still searching...

Owner of a Toshiba L300-1be (just slightly lesser specs than the former two)

I welcome any ideas, thanks.

---

### Post by MORDOCtheGREAT on 2008-11-23
I just bought a Satellite L355D-S7825 and am receiving the same message but cannot seem to figure out what it is to.

---

### Post by MORDOCtheGREAT on 2008-11-24
I asked one of my instructors (who is my go to guy for Linux) at college what that error might mean and he had no idea but he suggested that I look at the log files in /var/log and see if any thing in there said.  There is a PM-suspend.log and that has to do with suspending the computer(duh), so I tried to do so and it failed to come back on after the suspend. So I can only assume that it has something to do with that.  Just my uneducated guess. If anyone knows if I am anywhere close or not please chime in.  Thanks.

---

### Post by MORDOCtheGREAT on 2008-11-25
OK.  My instructor and I spent an hour tracking down what that message is to.  
     pm  cap regs version (7) 
power management capabilities register version 7
some pci device in your computer uses version 7 which apparently is not supported by the kernel as of yet.  You can use ```
sudo lspci -v

``` and look to see which pci device uses version 7.  In my case it was the LAN card.  So I went into the BIOS and disabled it and did not get a message.
     So there is no danger to your system.  It just cannot fully manage all the power options available to one of your pci devices.  Probably the NIC.
     Its just too bad I still have to see that dang message every time.

---

### Post by IlSeniore on 2009-02-06
Hi, 

I have a Toshiba Satellite L305-S5921 and experience the same problem. I checked with "sudo lspci -v" and found that it is my Ethernet controller Realtek RTL8101E 
Strange is that my computer _sometimes_ fails to boot up. After the Ubuntu Logo during boot, it gets stuck with a blank screen and freezes.
Any tips on how to get this solved? When I disable the controller in the BIOS, the message disappears. But I can't disable the controller permanently, because I need the Ethernet. 
Thanks so much!

PS: I am totally new to Linux, so don't know much about it yet :(

---

### Post by mngsailing on 2009-05-17
I also have Toshiba L305, and get the same message.  
lspci says   !!! Unknown header type 7f

This was following an attempt to hibernate. 
The normal boot is trying to use the 8.10 kernel though I have installed 9.04. 
My wired network cannot reach the router, but the wireless is working.

---

### Post by mngsailing on 2009-05-17
This may give some clues, but I don;t now how to deal with it. 

Re: Weirdness with realtek 8169

To: [email]debian-user@lists.debian.org[/email]
Subject: Re: Weirdness with realtek 8169
From: Juhan Kundla <juku@juku.kicks-***.net>
Date: Wed, 20 Oct 2004 12:20:49 +0300
Message-id: <20041020092049.GB13040@pohjala.ee>
Mail-followup-to: [email]debian-user@lists.debian.org[/email]
In-reply-to: <20041014114617.GA12181@pohjala.ee>
References: <20041014114617.GA12181@pohjala.ee>
Hei!

Juhan Kundla kirjutas:

[...]

> I have weird problem with my NIC. It has the Realtek 8169 chip on it.
> The r8169 kernel module should drive it. The floppy, it came with, has
> the r8169.c source on it.
> 
> But when i compile the r8169 kernel module (either the one from kernel
> source tree or the one from the floppy) it just won't load. I tried
> different kernel versions and configurations, nothing. The r8169 module
> will not initialize the interface. I tried both 2.6.8 and 2.4.27
> kernels.
> 
> Now begins the weird stuff. lspci and /proc/pci shows, that this card
> says, that it is actually with realtek 8129 chip. This means, that
> 8139too module should actually drive this card. The 8129 is Fast
> Ethernet, but i bought a gigabit ethernet card and the chip has 8169
> written on it!

This problem is now sorted out. Here is the solution, if someone does
this kind of bookkeeping.

My NIC announces wrong device ID on PCI bus. It should be 8169, but it
actually is 8129. Operating system drivers expect certain device ID and
they'll load only when this device ID matches. That is why the r8169
module from kernel did not initialize this NIC.

Ironically, the device ID 8129 belongs to another realtek NIC, which is
drived by 8139too kernel module. This was a source to much of confusion.
This 8139too driver loaded, but gave lots of puzzling errors.

In the beginning i was thinking, that there is something wrong with my
NICs firmware, perhaps some terrible mixup had happened in the factory.
In my worst nightmares i was dreaming, that they are shipping 8169 NICs
with 8129 firmware and vice versa. Well, luckily this is not the
case. :-)

Actually seems, that my NIC hardware has one bit of information reversed
by accident.

1000 0001 0110 1001 = 8169
1000 0001 0010 1001 = 8129

As a workaround i changed the Realtek's r8169 driver source to match
this incorrect device ID. See the patch below, with my changes. This
worked only with driver from Realtek website, but not with the driver
from kernel (2.6.8) source tree.

Complete solution was to return this defective NIC and get a new one.


Juhan


diff -urN r8169/src/r8169_n.c r8169.new/src/r8169_n.c
--- r8169/src/r8169_n.c 2004-08-09 11:54:32.000000000 +0300
+++ r8169.new/src/r8169_n.c     2004-10-18 17:59:35.000000000 +0300
@@ -183,7 +183,7 @@


 static struct pci_device_id rtl8169_pci_tbl[] __devinitdata = {
-       { 0x10ec, 0x8169, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 },
+       { 0x10ec, 0x8129, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 },
        {0,},
 };

---

### Post by chammi on 2009-05-26
...So if you want to fix this without replacing your NIC, you need to:

1. download the driver from the Realtek site
2. edit the source code as shown
3. compile and install 

?

Too bad there is not an easier way around it.

---

### Post by ovidio.catrina on 2009-06-03
hy there

i new in linux soy i`m having a problem installing my wify card.

please someone can tell me how did they do it¿?

my email is [email]ovidio.catrina@masterd.es[/email]

thkx

---

