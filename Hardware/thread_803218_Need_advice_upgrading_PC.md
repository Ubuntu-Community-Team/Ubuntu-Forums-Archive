---
title: "Need advice upgrading PC"
date: 2008-05-22
forum: Hardware
---

### Post by Vexxon on 2008-05-22
So, a couple of years ago, I built my computer out of whatever spare parts I could find lying around, and have been slowly upgrading it to fix problems I run into. Currently, I'm having issues playing higher quality videos. Basically anything better than .avi skips frames, freezes, or just crashes vlc/mplayer/etc (okay, so .avi is a container... but whatever typically comes inside .avi seems to work).

I've come to the (perhaps faulty) conclusion that this is a hardware issue, and I need to know what exactly I need to upgrade to get reasonably decent video running smoothly.

Here's the output of lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
00:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)
```

Do I need to:
A) Upgrade my graphics card
B) Upgrade my RAM (I believe I have a gigabyte)
C) Upgrade my processor (not sure what I have, don't know how to get that info)
D) Upgrade some combination of the above
E) None of the above

I'm looking to spend somewhere in the ballpark of $100, unless this is a ridiculously low amount, or something. Any help would be appreciated.

---

### Post by Cap'n Skyler on 2008-05-22
well,what are the processor specs?
motherboard specs?
knee jerk reaction is, more memory cant hurt,but that is not totally true.a better vid card can be had  with not too much cash laid out.
you might can find a better version of your processor and if it has the same socket,you can gain a bit by doing that.
motherboard up grade ability is another ball of wax.how many memory slots available?
what kind of memory does it take?
pci vid card or vga?
pci express is the current way to go,the others are going obsolete.

see,you can get a new processor and board for under 100 with sufficient capability for an upgrade,and pirate off your old stuff and use it.

do you want to build/repair so you can do better upgrade later on?
i suggest browse around [www.tigerdirect.com](www.tigerdirect.com) and [www.newegg.com](www.newegg.com) and see what they have for motherboard/processor bundles.
 check your foundation and see if it meets your needs,if not start anew
and recycle what you can.lots of options,and hard to say what to do really.

post up what you are after

Moofs:popcorn:

---

### Post by Vexxon on 2008-05-22
Okay, after some digging around:
processor:```
Version: Intel(R) Celeron(R) CPU 2.66GHz                     
	Voltage: 1.4 V
	External Clock: 133 MHz
	Max Speed: 2660 MHz
	Current Speed: 2660 MHz

```

as much info as I could find about the mobo:```
description: Motherboard
       product: P4M800PRO-M
       vendor: ECS
       physical id: 0
       version: 1.0
       serial: 00000000

```

After taking a look inside, it looks like I have 2 slots for RAM (well... 2 for DDR and 2 for DDR2) And I'm only using one DDR2 slot.

[QUOTE=Cap'n Skyler]pci vid card or vga?[/quote]
I think it's agp. :confused:

I don't have any pci express slots, but I'd be happy just getting a better pci card, if that's what it takes. I'm not really interested in switching out my motherboard at the moment, but I will if that's the next step.

---

### Post by nicedude on 2008-05-22
If your motherboard is the one in the picture at the bottom of this post then you should just get a AGP graphics card and probably you should just reboot and look into your bios to see how much RAM you have as well, saying you have 1 chip doesn't really tell me anything about what the amount of RAM is. I have listed an AGP card below that is only $36 I chose it quickly but for a few reasons first it is cheap but had good customer feedback, second because it is a model that doesn't use a fan to cool it which means there is less to break or make more noise etc and since you just want to watch videos it will do that just fine.

Also a tip .avi means either Xvid or Divx encoded videos which is in my opinion ( and pirates as well ) the best current available video format for use with your PC. The quality of any video you obtain is directly related to how good the source they ripped it from was and there skill and or software used to convert it to .avi. I have seen .avi movies that look as good as a store bought DVD but usually they (if from good source) are a slight step below true DVD quality but at one fifth the size. You have to get real picky to list the difference between say TV and good Xvid. So stick with obtaining avi's and watching them and get that video card and install it and you should see an immediate improvement in your playback performance.

Link to newegg $36 graphics card
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150239](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150239)

---

### Post by Vexxon on 2008-05-22
Yep, that pic is what my mobo looks like.

I forgot I didn't mention it, but I have a gigabyte of RAM.

That card would be fine with me, as long as it's an upgrade from my current card. Don't want to pay for a downgrade. :-P

You might have already seen it in my first post, but this is the card I'm using at the moment:
```
 description: VGA compatible controller
                product: NV20 [GeForce3 Ti 200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 m
```

Would it be worth it to toss this card in favor of the one you showed me? (Sorry if you already took my old card into consideration... just want to double check before dropping $40. :3 )

Thanks for the feedback.

---

### Post by Cap'n Skyler on 2008-05-22
the good news is there are a LOT of mid range 3 d cards to buy,and certainly will be good for your computer.
memory and a better card will be good to help it all work better,without breaking your car's gas fund! :P
:guitar:

---

