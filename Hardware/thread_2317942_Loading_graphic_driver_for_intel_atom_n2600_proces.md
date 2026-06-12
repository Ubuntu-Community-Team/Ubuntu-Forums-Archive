---
title: "Loading graphic driver for intel atom n2600 processor"
date: 2016-03-21
forum: Hardware
---

### Post by adam191 on 2016-03-21
[COLOR=#000000][FONT=IntelClear-Light]Hi there,[/FONT][/COLOR]

[COLOR=#000000][FONT=IntelClear-Light]I got a question for a brand-new Ubuntu 12.04.03 LTS graphic installation, this embedded  system running on top of Intel Atom N2600 CPU, and Intel NM10 intel chipset, also **GMA 500 **[/FONT][/COLOR]
[COLOR=#000000][FONT=IntelClear-Light]After a brand-new OS installation, I found the system is slow, and realized  only the basic graphic  driver installed, the currently resolution  is only (800*600).[/FONT][/COLOR]
[COLOR=#000000][FONT=IntelClear-Light]Below steps is what I tried so far but has no luck to get it work.[/FONT][/COLOR]

[COLOR=#000000][FONT=IntelClear-Light]1. I downloaded the Intel graphic installer for LINUX from 01.org, it installed successfully, but tells me that "You don't seem to have an Intel i915 chipset so no update are needed".[/FONT][/COLOR]
[COLOR=#000000][FONT=IntelClear-Light]2. Type command ""Sudo lshw -c video | grep 'configuration' " in term, I got below[/FONT][/COLOR]
[COLOR=#000000][FONT=IntelClear-Light]    configuration: driver=gma500 latency=0[/FONT][/COLOR]
[COLOR=#000000][FONT=IntelClear-Light]3. Try find gma500 linux driver but I got nothing.[/FONT][/COLOR]

[COLOR=#000000][FONT=IntelClear-Light]Does anyone know how to install this driver?[/FONT][/COLOR]
[COLOR=#000000][FONT=IntelClear-Light]Thanks.[/FONT][/COLOR]

[COLOR=#000000][FONT=IntelClear-Light]Adam[/FONT][/COLOR]

---

### Post by ajgreeny on 2016-03-21
You already have that driver so there is nothing you can do to change, I'm afraid.  Or not in a simple way with 12.04, but see below.

Intel has excellent drivers for its graphic chips and as long as it is not one of the very newest skylake cpus, it should be working as well as it can.  It is likely that a newer version of Ubuntu will work better and I suggest you try an upgrade, or better a clean install of 14.04.4, which I am pretty certain has much better support for that Poulsbo graphic chip.

Try it live for a start to see if it gives you the required resolution; I think it will, and you can then take the final step and install that version.

---

### Post by adam191 on 2016-03-22
Thanks for the quick respond ajgreeny.
I actually downgraded from 14.04, it seems like a effect that causing the system even slower under 14.04 or 15.04.
I think its the graphic driver, cuz it only shows mesa driver installed which its the basic driver. I don't know if anyone else have such problem, maybe is there a way to fine tune this OS?.

---

### Post by PippoFranco on 2016-04-03
I have the same problem. Performance under 14.04.4 or 15.10 of my old Aspire One A0751h are just impossible. The system was working with reasonable  performance with 11.04 or 12.04.
Hope some user is able to suggest how to find a reasonable driver for GMA500 chip set

---

### Post by mörgæs on 2016-04-04
I think an Atom would be better off with a lighter desktop environment like X/Lubuntu.

---

### Post by 1clue on 2016-04-04
What motherboard?

My SuperMicro c2758-based board has an aspeed graphic chip, maybe you have something like that hardwired in.

mörgæs,

I found out a year or so back that we have to stop assuming atoms are feeble.  My c2758 beats my i7 920 on about half of the tests I tried. The i7 is faster at compilation, but just about everything else that I actually use a computer for, the c2758 beats the i7.

---

### Post by mörgæs on 2016-04-04
Atom is a big family and yes, some of them can be quite powerful. Yours and original poster's are far from similar:

[http://ark.intel.com/products/58916/Intel-Atom-Processor-N2600-1M-Cache-1_6-GHz](http://ark.intel.com/products/58916/Intel-Atom-Processor-N2600-1M-Cache-1_6-GHz)
[http://ark.intel.com/products/77988/Intel-Atom-Processor-C2758-4M-Cache-2_40-GHz](http://ark.intel.com/products/77988/Intel-Atom-Processor-C2758-4M-Cache-2_40-GHz)

---

### Post by 1clue on 2016-04-04
Yeah, maybe I should have looked before posting.  I guess somehow I thought all Atom processors were taking a huge step up.

Sorry for injecting irrelevant info.

---

### Post by Yellow Pasque on 2016-04-04
I'm pretty sure the OP's Atom N2600 is a Cedarview chip with GMA3600 (not a Poulsbo chip with GMA500). If that's the case, this bug report explains why it works better with 12.04:
[https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584](https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584)

---

### Post by mörgæs on 2016-04-05
> **1clue said:**
> Yeah, maybe I should have looked before posting.  I guess somehow I thought all Atom processors were taking a huge step up.

Sorry for injecting irrelevant info.

You don't have to be sorry. I like it when a thread widens out a little to give a more complete picture, not only question -> answer.

---

### Post by mastablasta on 2016-04-05
I think this could be one of those chips which were actually not made by Intel. so Linux drivers are problematic. for more info see here: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
here: [https://wiki.archlinux.org/index.php/poulsbo](https://wiki.archlinux.org/index.php/poulsbo)

and here: [http://www.notebookcheck.net/Intel-Atom-N2600-Notebook-Processor.54661.0.html](http://www.notebookcheck.net/Intel-Atom-N2600-Notebook-Processor.54661.0.html)

> The N2600 features a** PowerVR SGX545 **based graphics card (at 400MHz) named Graphics Media Accelerator 3600 and a video decoding engine for MPEG4 Part2, VC-1, WMV9, and H.264. Furthermore, the chip now also supports DisplayPort 1.1 and HDMI 1.3a outputs.
The processor core is still similar to the old Atom processors. Therefore the performance of the N2600 is comparable to an older Atom N570.


---

### Post by Yellow Pasque on 2016-04-05
> **mastablasta said:**
> I think this could be one of those chips which were actually not made by Intel. so Linux drivers are problematic.
Yep.

> for more info see here: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) here: [https://wiki.archlinux.org/index.php/poulsbo](https://wiki.archlinux.org/index.php/poulsbo)
No, I think those links are what's confusing the OP. It's not a Poulsbo (GMA500/600) chip, but rather a Cedarview (GMA3600) chip.
Or, to get around Intel's naming scheme, it's a PowerVR SGX545 as you said, rather than a PowerVR SGX535/540 that the Poulsbo chips used. From what I've seen, the drivers are different for the two.

So, what's the solution? Unless you want to live with Ubuntu 12.04, the other option is to not use the Unity desktop as mörgæs suggested, since it's not kind to GPU's without 3D hardware acceleration. If Unity doesn't have GPU acceleration, it will use the CPU to do graphics tasks, which the older Atom chips simply cannot handle.

---

