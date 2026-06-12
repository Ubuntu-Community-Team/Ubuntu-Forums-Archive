---
title: "ENE Card Reader Issues in Dapper"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by rfdeshon on 2006-11-12
I have been searching off and on for months for a way to get my built in card reader in my laptop working in Dapper with no luck ](*,) . I have a Lenovo 3000 C100 (hey, it was cheap and I'm a college student) and the card reader (or at least the SD portion) will not work. I really need this to work since I have a digital camera that uses SD and, although I can pull photos off it using USB, I have not been able to find software that lets me put photos back on through the camera (I would like to make some prints of a few of my photos). Here is the pertinent output from lspci:

```
0000:01:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Lenovo: Unknown device 2075
        Flags: bus master, medium devsel, latency 168, IRQ 169
        Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 90000000-91fff000 (prefetchable)
        Memory window 1: c2000000-c3fff000
        I/O window 0: 0000c400-0000c4ff
        I/O window 1: 0000c800-0000c8ff
        16-bit legacy interface ports at 0001

0000:01:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Lenovo: Unknown device 2079
        Flags: bus master, medium devsel, latency 128, IRQ 5
        Memory at c0000000 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

0000:01:04.2 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Lenovo: Unknown device 2077
        Flags: bus master, medium devsel, latency 128, IRQ 209
        Memory at c0000100 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0000:01:04.4 FLASH memory: ENE Technology Inc: Unknown device 0551 (rev 01)
        Subsystem: Lenovo: Unknown device 2078
        Flags: bus master, medium devsel, latency 128, IRQ 5
        Memory at c0000200 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

```

---

### Post by Ereza on 2006-11-15
Same problem here:

lspci -v output:

```
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at dc000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 52000000-53fff000
        I/O window 0: 00005400-000054ff
        I/O window 1: 00005800-000058ff
        16-bit legacy interface ports at 0001

06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at dc001800 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, medium devsel, latency 32, IRQ 169
        Memory at dc001c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at dc002000 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: medium devsel, IRQ 255
        Memory at dc001900 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: [80] Power Management version 2

```

I have a Toshiba Satellite A110-180, with this built-in card reader. As I have been investigating, I can tell you that ENE hasn't given any information about this device. Also, I have found that version 710 works (although with some problems), but 712 doesn't (at least for me).

Does anyone have a solution for this?

---

### Post by Flak Magnet on 2006-11-22
Sorry folks, I don't have a solution to this issue yet either.  I have a Toshiba M115-S3154 with the same card reader, the ENE CB712/4.

I'll watch this space and hopefully remember to post if I find a way to enable at least the SD part of it.


--Tim

---

### Post by lgambett on 2006-11-25
Same as here, Acer Aspire 3102WLMi, memory card reader not working.

---

### Post by rfdeshon on 2007-01-04
Has anyone found anything on this? I still have not been able to find a solution. I would think an SD card reader would be pretty standard equipment and easy to get working, I guess I am too idealistic :(

---

### Post by eth on 2007-01-08
Very same problem here, on Acer Aspire 5502. 
The only thing that I noticed it's that the card reader works under ubuntu if it's USB bus based, but it won't if it's PCI.

---

### Post by rfdeshon on 2007-01-08
Is it a card reader using the EXACT same chipset? I know there are plenty of card readers that DO work under ubuntu but this specific one does not.

---

### Post by HellRat on 2007-01-21
My card reader doesnt seem to work either. I have a toshiba portege m100. Works in MS tho =(. Anyone know anything?

lspci -v:

```
0000:01:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, slow devsel, latency 168, IRQ 11
        Memory at cff05000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=06, subordinate=09, sec-latency=0
        Memory window 0: 4a000000-4bfff000 (prefetchable)
        Memory window 1: 50000000-51fff000
        I/O window 0: 0000c800-0000c8ff
        I/O window 1: 0000cc00-0000ccff
        16-bit legacy interface ports at 0001

0000:01:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: medium devsel, IRQ 255
        Memory at cff06800 (32-bit, non-prefetchable) [disabled] [size=512]
        Capabilities: [80] Power Management version 2

```

---

### Post by weissed on 2007-02-07
If it's SD the format you are interested in, you might want to take a look at [http://mmc.drzeus.cx/wiki/Welcome](http://mmc.drzeus.cx/wiki/Welcome)

The link above doesn't help me and my ENE 710 card reader, because the formats supported are SD and MMC - and I am having a Memory Stick card.

I did not try the drivers above, so proceed with caution. Check if your ENE controller is supported first [http://mmc.drzeus.cx/wiki/LaptopMatrix](http://mmc.drzeus.cx/wiki/LaptopMatrix). Seems from that page that ENE 712 is supported.

---

### Post by rfdeshon on 2007-02-22
Has anyone gotten this set up and working? I looked at the site posted above but there does not seem to be any information on actually getting anything working nor can I find any downloads of any sort (patching things and installing drivers generally requires a download, don't you think?)

---

### Post by macozz on 2007-02-23
Hi,
I am having the same problem described here with the ENE 712/4 chipset.
I have a Clevo M540V, sold here in Brazil as Positivo V21. It comes with Mandriva 2006. In ti all worked fine (Wireless, screen and, more important, card reader (4in1, MS, MS-Pro, SD and MMC). In the Mandriva installation, when I insert the MS card, pops-up a window with the card content. I guess that this indicates that there is support for that in Linux (ate least in some distros). In Edgy I cannot get this (OK, I have no MMC or SD cards...).
In some posts I see that a module called mmc_block is needed, but this module does not exist in my modules for the 2.6.17-50 kernel.
Any one out here have some idea, or point to same post that seems to solve that?
Thanks!

---

### Post by macozz on 2007-02-24
Just an adendum. In checking the Mandriva orginal installation in an identical notebook I found that 3 modules are loaded: esm7skl, esd7skl and ems7skl. By names it is obvious that they are related to the cards. However I cannot find anything abouth this modules in Google, Forums or otehr places and, of course, they are not present in my kernel modules installation. Anyone out there knows something about they?

---

### Post by elmerfud on 2007-02-25
I've got the same ENE device in an HP zd7280 laptop.  I've subscribed to the mailing list and Linux support for this device is almost non existent because they can't get the interface spec.  They have part of it working, but not all of it. 

I'm hoping that these sorts of issues go away when Dell and others start putting Linux on laptops from the factory.  At that point the manufacturer cannot overlook the Linux market, especially if a driver is needed for a Dell device. 

Does anyone know of a Dell laptop that uses an ENE device ?  I guess I could google it...

---

### Post by claudex on 2007-03-04
I've got a ENE cardreader in a Toshiba Satellite A110-178 and I can't use it too. Is there any news about a ENE driver.

---

### Post by Goliash on 2007-03-06
I also have this card reader: ENE Technology Inc CB-712/4 Cardbus Controller
Unfortunately with no driver, I didn't found any.

---

### Post by dptxp on 2007-03-17
I am just waiting to solve same problem in ACER 5101.

---

### Post by Tweepy on 2007-03-19
Same probleme here for a toshiba Satellite m60-103 :
```
uname -r
2.6.17-11-generic

```
```
lspci -v | grep ENE
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

```
Also prevent me to go in Hibernate mode:
```
dmesg | grep mmc0
[17233006.828000] mmc0: Got command interrupt even though no command operation was in progress.
[17233006.828000] mmc0: Please report this to <sdhci-devel@list.drzeus.cx>.
[17233006.828000] mmc0: Card is consuming too much power!
[17233006.828000] mmc0: Unexpected interrupt 0x00800000. Please report this to <sdhci-devel@list.drzeus.cx>.

```
So needed to disable the  mmc_core: sdhci module
```
sudo rmmod sdhci
sudo sh -c 'echo blacklist sdhci >> /etc/modprobe.d/blacklist'

```


A Trackball is opened here:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/62995]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/62995")

---

### Post by froyd on 2007-03-20
So still no sollutions for our problem ?
Got the same here on an ACER 5630

lspci | grep ENE

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

---

### Post by Goliash on 2007-04-08
The only solution is to upgrade to Feisty. Support for the card reader is in new kernel 2.6.20. Now I can read my SD cards, but only in slow mode (usb 1.1)
```
[41252.700000] mmc0: Problem switching card into high-speed mode!
[41253.108000] mmcblk0: mmc0:b368 SDC   999936KiB
[41253.108000]  mmcblk0: p1
```
I don't know why, but at least this.

---

### Post by Thingymebob on 2007-04-23
No joy on my aspire 5103wlmi:
```

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

```

On feisty :- Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

---

### Post by rfdeshon on 2007-05-02
I'm on feisty now and still no dice. This would be more of an annoyance if I had not given up and bought a USB adapter.

---

### Post by nab on 2007-05-10
Hi all,

I'm also having problems with my sd card reader. 

I'm working on an Toshiba satellite m30x with feisty. The ubuntu-kernel is version 2.6.20-15.

with "lspci -v | grep ENE" I get:
```
 02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
02:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (prog-if 01)
02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:
```

with "dmesg" I get:
```
[   23.448000] sdhci: Secure Digital Host Controller Interface driver
[   23.448000] sdhci: Copyright(c) Pierre Ossman
[   23.448000] sdhci: SDHCI controller found at 0000:02:04.2 [1524:0550] (rev 0)
[   23.448000] ACPI: PCI Interrupt 0000:02:04.2[B] -> GSI 17 (level, low) -> IRQ 17
[   23.448000] mmc0: SDHCI at 0xd0202000 irq 17 DMA 
```

As I understand this output my sd-card reader should now be working.
Inserting an SD-Card (which works on this reader with windows) nothing happens. :confused: 

well, i googled and didn't find any solutions, so please point me in the right direction.

TIA,
Niko

---

### Post by macozz on 2007-05-10
Goliash, do you get the card reader working slow or you use the USB cable to read it from the device in which the card is? I am running Feisty since the Beta version, fully updated, but no joy with SD, Memry Stick ot MMC cards... What modules handle your card reader?

---

### Post by Goliash on 2007-05-28
Part of my dmesg log:```

[   17.100000] sdhci: Secure Digital Host Controller Interface driver
[   17.100000] sdhci: Copyright(c) Pierre Ossman
[   17.116000] ieee80211_crypt: registered algorithm 'NULL'
[   17.116000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.116000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.c
om>
[   17.192000] Bluetooth: HCI USB driver ver 2.9
[   17.196000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   17.196000] Socket status: 30000006
[   17.196000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   17.196000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   17.196000] cs: IO port probe 0x3000-0x3fff: clean.
[   17.196000] pcmcia: parent PCI bridge Memory window: 0xd6100000 - 0xd61fffff
[   17.196000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   17.196000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.196000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   17.196000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10
PST 2006
[   17.196000] sdhci: SDHCI controller found at 0000:0a:06.2 [1524:0550] (rev 1)
[   17.196000] ACPI: PCI Interrupt 0000:0a:06.2[B] -> GSI 20 (level, low) -> IRQ 22
[   17.196000] mmc0: SDHCI at 0xd6101400 irq 22 DMA

```
Part of lspci:
```

0a:06.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10d7
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at d6100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003400-000034ff
        16-bit legacy interface ports at 0001

0a:06.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10d7
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at d6101400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

```

So I think module sdhci can use this card reader. But still with slow mode. (unfortunately also after today's upgrade to Linux version 2.6.20-16-generic)

```
[18934.272000] mmc0: Problem switching card into high-speed mode!
[18934.680000] mmcblk0: mmc0:b368 SDC   999936KiB
[18934.684000]  mmcblk0: p1
```

---

### Post by jaggerlink on 2007-06-08
Same problem here.  I have a Toshiba Satellite A-75 S231.  Here is my lspci output:
```
lspci | grep ENE
02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
02:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller
02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:

```I remember this working on another linux distro, so it should be possible.  Any help is appreciated.

---

### Post by rfdeshon on 2007-06-08
I get the same messages from the sdhci module Goliash but still it does not work. Not in high speed mode, not in low speed mode. It sees that the reader is there but never recognizes that media is inserted. Ubuntu recognizes the same media just fine when using a USB adapter, thus it is not a problem with the media (it had better not be, it is Kingston, I've always found their memory products to be of high quality IMHO). Is this just such an obscure chipset that no one has bothered to code modules for it? I wish I was a stronger programmer, I would attempt to do it, but I really would not know where to start when it came to programming device modules.

---

### Post by macozz on 2007-06-09
Hi rfdeshon, I buy my laptop with Mandriva installed, and the seller provided a pre-compiled module that worked just fine. They (the reseller) promise me to look for the module for Ubuntu, but no reply until now. So, this chipset do work in Linux, but the module is not freely available. At least as far I know! May be we can ask for a binary module?
Cheers!

---

### Post by oscarmeyer51 on 2007-06-14
I have emailed ENE Inc asking them to release info to the development community so that drivers can be built for this. Perhaps if enough others did the same, it would aid the development of these (and other) drivers.

Just a thought.

I am confident that the dev community will get this addressed soon, there seems to be significant amount of pages referencing this cardbus contoller and the absence of linux drivers.

Have patience (if possible!)

---

### Post by lsde on 2007-07-10
Resolved, patch available : [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/62995](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/62995)

---

### Post by macozz on 2007-07-10
Great!
There is a way to compile the patch ONLY for the proper modules? Or we need to compile and install the whole kernel? The problem with that is that you get "prisioner" of a personalized kernel. On the other hand, you can just complie the modules.... but, as I said, I do not know if it is possible.
Thanks again!!!
Cheers

---

### Post by rfdeshon on 2007-07-12
Great, too bad that patch breaks my wireless card (IPW2200, the patch alters the power management which makes it so the card cannot be activated)

---

### Post by tama on 2007-07-20
If you mean the same patch as the one [here]("http://list.drzeus.cx/pipermail/sdhci-devel/2007-May/001735.html") you should notify the [sdhci-devel ml]("mailto:sdhci-devel@list.drzeus.cx").

Anyway, are you sure is that patch that messes up with ipw2200?? Weird...

---

### Post by rfdeshon on 2007-07-22
The only change I made was applying that patch to my kernel. I didn't change anything else on my system, I didn't change any options from the Ubuntu default when I recompiled my kernel. When I booted into the patched kernel, it said it could not load the firmware on my wireless card. I checked some of the forums and found out that was a problem with some sort of power management function in the kernel. Looked at the patch and what it did (supposedly) to make the card reader work was roll back some power management alteration that was made in the current kernel.  From there, I put two and two together.

---

### Post by tama on 2007-07-23
I think we were talking about different patches.
What's got into the mainline kernel is [this patch]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=7de064ebc67d9baf6c933d3a7046feb9b4eced05;hp=98ccf14909ba02a41c5925b0b2c92aeeef23d3b9#patch1"), and the original patch (against 2.6.20) is [this one]("http://list.drzeus.cx/pipermail/sdhci-devel/2007-May/001735.html").

You should try the second one if you are on feisty kernel. Neither of these has anything to do with power management anyway.

---

### Post by rfdeshon on 2007-07-23
I just took a look at that patch. It is identical to the one I tried that was from the Ubuntu Bug Tracker. I may be misguided with the power management statement however, it most assuredly does break my IPW2200 wireless card. When I modprobe the ipw2200 module with a kernel with that patch, it tells me it could not update the firmware and it failed to bring the interface up. When I reboot with the unpatched kernel, it works just fine.

---

### Post by tama on 2007-07-24
There are two different patches in the Ubuntu bug tracker, but if you are sure the patch that breaks your wireless is the same I linked in the previous post, you should definitely write to [email]sdhci-devel@list.drzeus.cx[/email].

This patch has already got into the mainline kernel and the gutsy kernel, so we'd better report any problems now :)

---

### Post by rfdeshon on 2007-07-24
I'm sorry, it may be that I am overlooking something obvious, but the two patch links that you posted earlier, tama, look exactly the same to me. [This]("http://launchpadlibrarian.net/8359982/linux-source-2.6.20_ene_cb712.patch") is the patch that I tried and that seemed to break my wireless card. When you say that patch is in the mainline kernel, which one are you talking about specifically? I'm using the latest one (for feisty) from the repos and have not seen an updated kernel in quite a while. I will try compiling again tonight with the patch and grab the exact errors my wireless card gave me.

---

### Post by tama on 2007-07-24
Yeah, you've got the good patch.
And that patch is in the mainline kernel, that is, in the development version for the next release which will be 2.6.23. Now it has landed in the Gutsy kernel too (for next release).

Anyways, now that I read again, I believe your problems have more to do with the restricted modules than with the patch.
When you use a custom kernel, there're some non-GPL parts that you most probably have not compiled. I'm pretty sure the ipw2200 firmware lies down there.

You have instructions on how to build a custom kernel and its restricted modules [here]("https://wiki.ubuntu.com/KernelCustomBuild") .

Have luck :p

---

### Post by rfdeshon on 2007-07-24
Thanks, I'll try that out. Hopefully it is just some stupid mistake on my part. Now I have something to do while the rice for my dinner cooks tonight! Compile a kernel (again).

---

### Post by HarshReality on 2007-07-30
So am I to understand that if I get a current Gutsy beta that my card reader will work?

---

### Post by tama on 2007-08-02
> **HarshReality said:**
> So am I to understand that if I get a current Gutsy beta that my card reader will work?

The patch is already included in 2.6.22-9 kernel, so... yep, it should work now.

---

### Post by HarshReality on 2007-08-03
Kewl, wonder if/when this wil reach a fiesty kernel update
l

---

### Post by HarshReality on 2007-08-04
hmmm, negative. Updated to the generic kernel and got butkus:
lspci:
```

02:01.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
        Subsystem: Hewlett-Packard Company NX9500
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at e2004000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 58000000-5bfff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

02:01.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
        Subsystem: Hewlett-Packard Company NX9500
        Flags: medium devsel, IRQ 10
        I/O ports at 3c00 [size=128]
        Capabilities: <access denied>

```

access denied? Help me out guys, am I to manually add this to fstab or something and if so how am I to determin what I am to add (yep Im green here). I updated to the gutsy generic kernel.... nuts

incidentally it didnt even show up in dmesg at all :/

---

### Post by HarshReality on 2007-08-05
Is there truely that large of a diff. between the 710 and the 712... It would appear so...

---

### Post by rfdeshon on 2008-02-28
Just thought I would post in here to say that my SD card reader FINALLY works now that Gutsy is out. I'm quite thrilled about that fact. One less piece of hardware to put in my laptop bag when I head out on the road. I tried a memory stick, but that doesn't work. I'm assuming it's probably because of the MagicGate crap so I'm not worried, I don't really use them anyway.

---

### Post by oscarmeyer51 on 2008-03-31
FYI - Glad to hear that some (many?) have their memory card reader working under Gutsy. I am still one of those stuck with it not working, but have been informed by those on Launchpad that Hardy Heron has a full fix for this. I have not had the opportunity as yet to pull the alpha (now beta) down to attempt that, and as there are but a scant number of days until the Heron takes flight as a full release (yes, pun intended), I am just going to wait for that.

Other good news was that with the Gutsy release, my PC Card reader started working OK. I will take any positive movement and be happy!

Will update this thread after moving up to Heron and seeing what effect that has on all the hardware. Happy Ubuntuning to all !!!

---

