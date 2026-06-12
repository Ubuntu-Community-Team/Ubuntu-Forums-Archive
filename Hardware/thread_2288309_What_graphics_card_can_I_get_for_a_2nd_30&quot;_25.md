---
title: "What graphics card can I get for a 2nd 30&quot; 2560x1600 monitor?"
date: 2015-07-26
forum: Hardware
---

### Post by watchpocket on 2015-07-26
I recently got a [30-inch Nixeus monitor]("http://www.amazon.com/Nixeus-Vue-2560x1600-WQXGA-Monitor/dp/B00CHDHE0W/ref=sr_1_1?s=pc&ie=UTF8&qid=1437885199&sr=1-1&keywords=nixeus+vue+30") that I'm really happy with and highly recommend -- 16:10 aspect ratio, 2560x1600 resolution.  

Now I want to get a second one.

[COLOR=#ff0000]***Problem:***[/COLOR] the monitor uses a dual-link DVI cable but my graphics card has only one DVI port***.***  (EDIT: A dual-link DVI cable and connection (or DisplayPort) is specifically needed to render the 2560x1600 resolution.)  

My first thought was "Simple, just get another graphics card identical to the one I have."

Not so simple.  The card I have is five years old and isn't made anymore.  Three times I thought I'd found a vendor that would sell me that card and three times I was refunded. I scoured ebay for one but couldn't find.

**So I need to find the right graphics card with either one or two DVI ports, one that my computer can accommodate.** (And if it only has one DVI port, one that can play nice with my current card.) It can't be longer that eight-and-a-quarter inches or it won't fit inside the computer case. I have four PCI slots available, so that's not a problem.  I probably don't want anything higher than PCIe 2.1.

I'm not a gamer but do photo-editing & archiving, watch movies and videos, with at the very least web browser (FF), terminal, & music players (Cantata, mpv) always up. 60Hz refresh rate is fine.

My computer is a Wild Dog Performance 64-bit desktop unit from System76 (model wilp6, bought in early 2010).  I'm running Ubuntu-MATE 14.04.2 Trusty on one drive (with nouveau driver) and Ubuntu 12.04.5 Precise on a 2nd drive (with nVidia driver).

My power supply is 230 watts.[COLOR=#0000ff]*** [EDIT: that's wrong.  It's 500 watts maximum power.]***[/COLOR]   

My current graphics card, the one that came with the computer, is a [COLOR=#800000]*Gigiabyte GTS 250*[/COLOR], 1GB 256-Bit GDDR3, PCIe 2.0.  You can see it [here]("http://www.amazon.com/exec/obidos/ASIN/B005640FSW/ref=pe_301860_26203570_tex_id").

In any event, I'm hoping someone mgiht have an idea what card would work in this situation, either as a standalone with 2 DVI ports, or a card with one DVI port running alongside my old card.  

Thanks for any suggestions, meanwhile here is some[COLOR=#ff0000]** other data about my system:  **[/COLOR]

CPU: Intel(R) Core(TM)2 Quad CPU Q9650  @ 3.00GHz; L2 cache: 6144 KB; 8 GB ram.  ```
--> [COLOR=#0000ff]lspci -nnk | grep -iA3 vga[/COLOR] 
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G92 [GeForce GTS 250] [10de:0615] (rev a2)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:34c7]
    Kernel driver in use: nouveau
02:00.0 FireWire (IEEE 1394) [0c00]: LSI Corporation FW322/323 [TrueFire] 1394a Controller [11c1:5811] (rev 70)
```

Motherboard: ```
-->[COLOR=#0000ff] lspci [/COLOR]
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
[COLOR=#8b4513]*[ snip ]*[/COLOR]
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller 
```

```
--> [COLOR=#0000ff]sudo lshw -C display[/COLOR] 
  *-display               
       description: VGA compatible controller
       product: G92 [GeForce GTS 250]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:43 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:e000(size=128) memory:e3000000-e301ffff
```

```
--> [COLOR=#0000ff]xrandr[/COLOR]
Screen 0: minimum 320 x 200, current 4480 x 1600, maximum 8192 x 8192
DVI-I-1 connected 2560x1600+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1600      60.0*+
   1920x1080      60.0  
   1680x1050      60.0  
[COLOR=#8b4513]*[ snip ]*[/COLOR]
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1920x1200+2560+400 (normal left inverted right x axis y axis) 593mm x 371mm
   1920x1200      60.0*+
   1920x1080      60.0     50.0     59.9  
   1920x1080i     60.1     50.0     60.0  
   1680x1050      59.9

```

---

### Post by dino99 on 2015-07-26
there are several recent cards which  are able to deal with such screen: you need to watch their technical specs
but the other problem is the too low psu power

[http://www.extreme.outervision.com/psucalculatorlite.jsp](http://www.extreme.outervision.com/psucalculatorlite.jsp)

---

### Post by watchpocket on 2015-07-26
> **dino99 said:**
> 
but the other problem is the too low psu power

I had that wrong earlier above.  My PSU is actually 500 watts maximum power.  (I edited to correct that in the original post.)

---

### Post by Yellow Pasque on 2015-07-26
Can't you just use the HDMI connector on your card?

EDIT: Also, the card originally came with an HDMI to DVI adapter, so if you don't have an extra HDMI cable, you can use that.

---

### Post by watchpocket on 2015-07-26
Using my current card's HDMI port absolutely will not deliver the 2560x1600 resolution. HDMI only supports that resolution if it's the HDMI 1.3 specification (mine isn't). Otherwise DVI is necessary, and it must be dual-link DVI. (Original post edited to clarify this point.)

The same goes for using an HDMI-to-DVI connector. HDMI's maximum resolution is 1900x1200, putting a DVI connector behind it isn't going to change that.

---

### Post by sandyd on 2015-07-26
Get a card with 1 DisplayPort and 1 Dual link DVI.

Might be much easier than two DVI ports.

---

### Post by Yellow Pasque on 2015-07-27
> if it's the HDMI 1.3 specification (mine isn't)
Are you sure about that? [http://solidlystated.com/hardware/evga-gts-250-512mb/2/](http://solidlystated.com/hardware/evga-gts-250-512mb/2/)
```
There are also 3 newer SKUs that have HDMI ports in addition to DVI. These cards drop the older HDTV 7 pin round connector in favor of HDMI 1.3 and it&#8217;s digital connnection.
```

Anyway, if you have an appropriate HDMI cable or the aforementioned HDMI->DVI adapter and a dual-link DVI cable, then it would be worth a try ($0)

---

### Post by watchpocket on 2015-07-27
I did run a 9-foot [Honeywell HDMI cable]("http://www.amazon.com/Honeywell-High-Speed-Supports-Ethernet-Standard/dp/B00TDIJRCC%3Fpsc%3D1%26SubscriptionId%3DAKIAILSHYYTFIVPWUY6Q%26tag%3Dduckduckgo-d-20%26linkCode%3Dxm2%26camp%3D2025%26creative%3D165953%26creativeASIN%3DB00TDIJRCC") (which claims to support the HDMI 1.4 standard) from the card's HDMI port to the monitor's HDMI port but got only 1900x1200 resolution.

And since I haven't yet, I will try plugging the HDMI->DVI adapter into the card's HDMI port and running the DL-DVI cable from that to the monitor's DVI port to see how that works.  You're correct in that I do need to at least try it before definitively ruling out that possibility.  For that matter I suppose I could try a DVI splitter on the DVI port, though that seems iffy and like something that might cause mirroring between two monitors.

---

### Post by watchpocket on 2015-07-28
I wrote:
>  *I will try plugging the HDMI->DVI adapter into the card's HDMI port  and running the DL-DVI cable from that to the monitor's DVI port to see  how that works.  *

This gave me a completely black screen, as if the monitor were off.  Connections were tight, I expected at least to get a lower resolution.  Back to square one.

---

