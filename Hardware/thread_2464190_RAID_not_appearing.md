---
title: "RAID not appearing"
date: 2021-06-26
forum: Hardware
---

### Post by heatopher2 on 2021-06-26
Hello, I've got a new setup with a RAID 1 array for data and other bits and pieces, using [this card]("https://www.ebay.com/itm/IBM-M1015-9220-8I-6GB-SAS2-SATA3-PCI-e-RAID-Controller-Card-8087-to-sata-9211-8/192928587871"). I've been fiddling with the system for a week or so now, and the RAID is OK with Windows, showing up in two separate installs, but I've just put Ubuntu 20 on, and unfortunately none of the partitions in the RAID array are appearing automatically. Just to clarify - Windows isn't controlling this array in any way as far as I know. What do I do about this? I haven't found a great deal of information from searching so far.

Thanks in advance :~)

---

### Post by TheFu on 2021-06-27
Linux prefers to use SW-RAID for non-business situations.  That is controlled via mdadm or LVM.

With HW-RAID, the HBA needs to have Linux drivers. It is likely either 
the wrong drivers are found 
or 
no drivers are found, so you'll need to manually find some and compile/link the kernel module (and update the module with each new kernel)
or
Windows has made parts (or all) of the storage Windows-only in a way that doesn't allow Linux to have access.

BTW, "Ubuntu 20" isn't a release.  There is a YY.MM aspect to all Ubuntu releases.  And with kernel stuff, the exact kernel used will matter.  Exactly which release do you have?  Is it the Server or on of the Desktop releases?  If it is a desktop, which DE?

Have you checked the log files for any messages related to that HBA?  Anything in there?  If there is something, then there is some sort of driver. If there is nothing, then you'll need to hunt down a driver for the exact card.  You can google the specific card and model to see the Linux support just as well as we can.  Ok - I did the google thing. [https://www.ibm.com/support/pages/support-matrix-sassata-ii-serveraid-8i-8k-8k-l-8s](https://www.ibm.com/support/pages/support-matrix-sassata-ii-serveraid-8i-8k-8k-l-8s)  No mention of debian or ubuntu support. Just RHEL and SuSE.  I didn't read the users guide.

In general, LSI makes the most trouble-free HW-RAID cards for Linux.  Generally, I look for BSD support in any HBA - that will almost guarantee Linux support too.

Over a decade ago, I bought a cheap Promise HBA because it claimed "Supports Linux" on the box.  Turned out for any RAID functions, I had to run a 3 yr old kernel. No newer drivers were available.  Fortunately, that HBA was recognized as JBOD and I've been using it for SW-RAID all these years. I'm glad of this, because in 3 hardware upgrades, I've never had any issues migrating the array to the new system. None. Zero. Nada.

---

### Post by heatopher2 on 2021-06-27
Hi, and thanks very much for replying.

> **TheFu said:**
> Linux prefers to use SW-RAID for non-business situations.  That is controlled via mdadm or LVM.

With HW-RAID, the HBA needs to have Linux drivers. 

Please be patient with me, as I'm pretty much a novice with all this RAID stuff, so most of this terminology is completely new to me. HBA, JBOD, LVM... SW/HW RAID - no idea about that distinction - going to have a look after the football...

Also, sorry for the imprecision:

> **TheFu said:**
> BTW, "Ubuntu 20" isn't a release.  There is a YY.MM aspect to all Ubuntu releases.  And with kernel stuff, the exact kernel used will matter.  Exactly which release do you have?  Is it the Server or on of the Desktop releases?  If it is a desktop, which DE?

It's  Ubuntu 20.04.2 LTS, and I think it must be the desktop version, as  there's no  reason I'd have downloaded anything else. Not sure right now where I put  the iso file that I downloaded, but I can double-check at some point. 

Here's the main thing - is it going to be worth fiddling around  forever trying to make this thing work? This card was very cheap, and I  bought it on some forum advice that I guess I should have  double-checked. I don't mind just shelling out for a card that is going  to be reliable as long as it doesn't cost an exorbittant amount. But OK, before I do  that, I'll try checking stuff, if only just to see what I can do with  this card at some later date. 

> **TheFu said:**
> Have you checked the log files for any messages related to that HBA?  Anything in there?  If there is something, then there is some sort of driver.  

I'm not a total novice with Ubuntu, but  never had to look for the log files, and therefore not sure where I  should be looking. I've just googled about that, and the result I'm  getting is /var/log/syslog. Is that right? And if so, what kind of  string do I need to be searching for to find the appropriate info?

> **TheFu said:**
> If there is nothing, then you'll need to hunt down a driver for the  exact card.  You can google the specific card and model to see the Linux  support just as well as we can. Ok - I did the google thing. [https://www.ibm.com/support/pages/support-matrix-sassata-ii-serveraid-8i-8k-8k-l-8s](https://www.ibm.com/support/pages/support-matrix-sassata-ii-serveraid-8i-8k-8k-l-8s)  No mention of debian or ubuntu support. Just RHEL and SuSE.  I didn't read the users guide.

And as for this, same again - I don't really have any idea where to start. Not really experienced with this firmware stuff.

Anyway, I'll leave it there. Thanks very much for the reply. Hope to hear back again :)

---

### Post by SeijiSensei on 2021-06-27
I'd ditch the card, connect the drives' SATA cables to the motherboard, and use software RAID via mdadm. This is a pretty good guide for RAID1.  [https://linuxconfig.org/linux-software-raid-1-setup](https://linuxconfig.org/linux-software-raid-1-setup)

Even if you're not all that comfortable using the terminal, just follow the steps in the guide and you should be fine.

---

### Post by heatopher2 on 2021-06-27
Yes, but that's no good if I'm dual booting, is it?

---

### Post by heatopher2 on 2021-06-27
> **SeijiSensei said:**
> I'd ditch the card, connect the drives' SATA cables to the motherboard, and use software RAID via mdadm. This is a pretty good guide for RAID1.  [https://linuxconfig.org/linux-software-raid-1-setup](https://linuxconfig.org/linux-software-raid-1-setup)

Even if you're not all that comfortable using the terminal, just follow the steps in the guide and you should be fine.[INDENT]                     Yes, but that's no good if I'm dual booting, is it?                 
(sorry for the duplication, by the way - I can't see how to delete posts)
And of course the penny dropped a while later that HW/SW is just hardware/software. Of course I need HW if I'm dual-booting, don't I?
[/INDENT]

---

### Post by TheFu on 2021-06-27
No, you don't need HW if you are dual booting.  OTOH, I haven't dual booted in over a decade.  Virtual machines do all that I need well enough. For about 9 yrs, I ran MS-Win7 Media Center in a VM under a Linux host on SW-RAID managed by Linux.

I suspect the HW-RAID drivers are incompatible between the Windows implementation and the Linux implementation. That's fairly common, unless it is a Fake-RAID (which is what most cheap RAID cards and motherboard on-board RAID provides).  Fake-RAID has all the downsides of HW-RAID with all the downsides of SW-RAID too.

In advanced Linux storage management, JBOD is preferred.  Actually, HW-RAID devices just get in the way for ZFS.

OTOH, you will certainly learn a bunch of things as you work through trying to get this card to work, but I fear the lack of payoff in the end will make the learning uncertain and frustrating.  Who ever recommended that specific card is probably the person to get advice for setting it up.

But make RAID cards can be used in a JBOD mode and make fine, fast, controllers, provided the drivers "just work."

As for what you should look for in the logs ... I can only say that you should look through all of them for anything related to PCI cards, storage controllers, LSI or IBM.

The following probably won't be all that useful unless some driver is working. It shows how to gather some information using multiple methods. If a command is not found, install it. You'll eventually want them and having the option is better before you need it than if you need it and cannot install for some reason.

For my RAID controller, I did an 
```
$ lshw -C storage
```
and got a bunch of HDDs listed along with some disk controllers.

```
  *-ide
       description: IDE interface
       product: JMB368 IDE controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: ide pm pciexpress pci_native_mode-only_controller__supports_bus_mastering bus_master cap_list
       configuration: driver=pata_jmicron latency=0
       resources: irq:17 ioport:bc00(size=8) ioport:b880(size=4) ioport:b800(size=8) ioport:b480(size=4) ioport:b400(size=16)
  *-storage
       description: SATA controller
       product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       version: 05
       width: 32 bits
       clock: 66MHz
       capabilities: storage msi pm ahci_1.0 bus_master cap_list
       configuration: driver=ahci latency=0
       resources: irq:36 ioport:9c00(size=8) ioport:9880(size=4) ioport:9800(size=8) ioport:9480(size=4) ioport:9400(size=32) memory:f9ff4000-f9ff47ff
  *-scsi:0
       physical id: 1
       logical name: scsi0
       capabilities: emulated
```
The Intel controller is part of the motherboard.  The JMicron IDE is the RAID card. The system is from 2010-ish.

These commands can be used too:
```
lspci -vk |perl -lne 'print if /IDE/ .. /^[\w]*$/'
```
or 
```
lspci -vk |perl -lne 'print if /SATA/ .. /^[\w]*$/'
```
But they will only show stuff that has drivers.

**inxi** will provide all sorts of summary information based on different subsystems. There are options for most common needs. Fully documented in the manpage for that command.

Logs can be searched using **journalctl**.  There are too many options to list all the possible techniques. Or you can use egrep  with some regex patterns for all the logs in /var/log/.  Up to you for which.  There are 500 ways to look.

---

### Post by heatopher2 on 2021-06-28
> **TheFu said:**
> No, you don't need HW if you are dual booting.  OTOH, I haven't dual booted in over a decade.  Virtual machines do all that I need well enough. For about 9 yrs, I ran MS-Win7 Media Center in a VM under a Linux host on SW-RAID managed by Linux.

I suspect the HW-RAID drivers are incompatible between the Windows implementation and the Linux implementation. That's fairly common, unless it is a Fake-RAID (which is what most cheap RAID cards and motherboard on-board RAID provides).  Fake-RAID has all the downsides of HW-RAID with all the downsides of SW-RAID too.

This just makes me sigh. I naively assumed that it would be "simple". Silly me. I would be happy to do exactly what you're doing with the virtual machines, at some point in the future when I'm more confident with Linux, but I'm not ready yet. So in the meantime I want to have both.

By the way, one annoying thing about this RAID card is that I can't get into the settings/WebBIOS/whatever. It's supposed to be <Ctrl H> to get on there, and it worked at first when I was setting it up, but now it doesn't :~/

> **TheFu said:**
> For my RAID controller, I did an 
```
$ lshw -C storage
```
and got a bunch of HDDs listed along with some disk controllers.

OK, I've got this output. Is it at least a good sign that that has turned up?

```
  *-raid UNCLAIMED
       description: RAID bus controller
       product: MegaRAID SAS 2008 [Falcon]
       vendor: Broadcom / LSI
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: raid cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:a0260000-a0263fff memory:a0200000-a023ffff memory:a0240000-a025ffff


```

By the way, this is what the RAID controller's boot process looks like. <Ctrl Y> works, but I don't understand what that's about, and <Ctrl H> doesn't do anything. 

[https://www.dropbox.com/s/xf2aqbutjz2zzwh/2021-06-28%2010.19.56.jpg?dl=0](https://www.dropbox.com/s/xf2aqbutjz2zzwh/2021-06-28%2010.19.56.jpg?dl=0)

(I couldn't load the photo, so had to do it as a link, which is not quite ideal of course)

---

