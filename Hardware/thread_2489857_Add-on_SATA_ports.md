---
title: "Add-on SATA ports"
date: 2023-08-12
forum: Hardware
---

### Post by RogerDavis on 2023-08-12
My older motherboard had a problem with a SATA port, So I'm looking to add an add-in SATA card with 6 ports (like the motherboard - Intel DZ77BH-55K).  The particular one I'm looking at is 10Gtek PCIe SATA Card 6 Port with 6 SATA Cables and Low Profile Bracket, 6Gbps SATA3.0 Controller PCI Express Expansion Card, X2, Support 6 SATA 3.0 Devices.

Is this, or any, SATA card plug-n-play, or do I need drivers, or ???

---

### Post by TheFu on 2023-08-12
> **RogerDavis said:**
> My older motherboard had a problem with a SATA port, So I'm looking to add an add-in SATA card with 6 ports (like the motherboard - Intel DZ77BH-55K).  The particular one I'm looking at is 10Gtek PCIe SATA Card 6 Port with 6 SATA Cables and Low Profile Bracket, 6Gbps SATA3.0 Controller PCI Express Expansion Card, X2, Support 6 SATA 3.0 Devices.

Is this, or any, SATA card plug-n-play, or do I need drivers, or ???

I searched for this HBA and see it isn't too expensive on Amazon.  Lots of people buying it for their storage servers. People use it with FreeNAS/TrueNAS, Proxmox, UnRAID, etc.  The biggest complaint was the lack of documentation for the jumpers, but that it came configured for all the internal ports to be enabled.  Because it is cheap and has related reviews, I'd probably get this if I were in the market and didn't want a SAS controller.  Looks like the risk for disappointment is low.

I have a 4-port PCIe SATA controller.  Let me check the hardware.  Looks to be JMicron. Meh.
You can get a quality LSI SAS controller that should be well supported by Linux.  The FreeNAS/TrueNAS guys used to maintain a list.  Each SAS port can connect to 4 SATA drives using $15 SAS-to-SATA cables.  

If you want to be 100% certgain, get the major chip used in the HBA and look up that to ensure drivers for it are included in the kernel drivers. Then it should be plug-in-play, but you never know until you try.  I've been burned by HBAs before.  Got one that claimed Linux support all over the box ... got it home to discover they shipped with a proprietary driver that had to be compiled into a 2.x kernel.  Great, except I was on a 3.x kernel by that point and no new drivers were created by the vendor for the new kernels and none for any kernel since.  To be far, the HBA did have generic kernel support - purely as JBOD, nothing more advanced.  Jumping forward with years of use behind me, I can say that this controller was slow. USB2 speeds compared with it.  Also, it came with a name brand, but not one known for quality. The company is long out of business.  $150 wasted.  Because it worked well enough, but not great, I used it. Should have returned it. 

When it comes to addon cards, I look for FreeBSD support. If a device claims to support FreeBSD, they will almost certainly have good-to-great Linux drivers too.

---

### Post by RogerDavis on 2023-08-12
I was hoping for a simple "no additional drivers ever needed", but I see now I need to be more specific.  

What I was wanting, but appears not likely is a 6 port SATA to replace the 6 on my motherboard with no software magic or support of any kind, completely plug and play.  One of the original ports is now dead, making others physically nearby suspect in the future, at least to me. Of course, the motherboard SATA ports don't require separate drivers or other support that I'm aware of.  I currently have 4 hard drives in the system, two for ******* and two for Ubuntu.  These are in manually switched drive trays, so normally only one is active and the other 3 are manually switched off.  I can have two on and clone any one drive to any other.

Reliability and consistency is very important, I don't want to have to rebuild drive connections and drivers or anything else every time an electron farts. 

Relevant system info:
- Motherboard Part / Model Number - DZ77BH-55K
- Which two Motherboard SATA drive cable connectors are for faster speeds 
- Do add-on SATA cards need drivers in Ubuntu or Windows ?

Total # of SATA Ports - 7   ???
Max # of SATA 6.0 Gb/s Ports - 4   ???
# of eSATA Ports - 1   ??

Since I've forgotten probably half of what I used to think I knew, simple details are appreciated.
Relevant system info:
- Motherboard Part / Model Number - DZ77BH-55K
- Which two Motherboard SATA drive cable connectors are for faster speeds 
- Do add-on SATA cards need drivers in Ubuntu or Windows ?

Total # of SATA Ports - 7   ???
Max # of SATA 6.0 Gb/s Ports - 4   ???
# of eSATA Ports - 1   ??

Back panel eSATA ports support IDE and RAID (no 
AHCI) mode in BIOS.  Once booted to an OS with drivers 
loaded, all SATA controller support depends on the OS 
driver. 
 
Note: A RAID array cannot be shared across SATA driver 
controllers (x6 ICH10 Gen-2 black ports, x2 Discrete 
Gen-3 blue ports and x2 eSATA Gen-2 red ports). 

Thanks !!!

---

