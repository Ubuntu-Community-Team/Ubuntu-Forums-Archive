---
title: "First PC Build - Motherboard Compatibility"
date: 2011-01-07
forum: Hardware
---

### Post by vttay03 on 2011-01-07
--I'm going to be doing my first system build in the next month and have been heavily researching motherboard compatibility with Ubuntu.  Ubuntu is the only OS I run at home so this is the number 1 priority for the system.  I've looked through the Hardware Compatibility/Incompatibility Threads but didn't find much information on the two particular models I've zeroed in on.  I was wondering if anyone has had experience/success/failure with either of the following two motherboards:

1) ASUS M4A78T-E
2) MSI 870A-G54

I've read a little bit about sound issues regarding the ASUS, but really can't find much information on the MSI model.  I'd almost prefer to go with the MSI model since it supports both USB 3.0 and SATA 3.0.  If anyone has a comparable GIGABYTE model they could suggest, I've heard they make solid motherboards as well.

---

### Post by Yellow Pasque on 2011-01-07
The Asus board has integrated video and the MSI board does not. Did you want onboard video? ATI/AMD 700/800-series chipsets are well-supported in the Linux kernel. Some things to look at are the audio chipset (VIA 1708 is one to avoid right now) and the sensor chip if you plan on monitoring temps/voltages (see [http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices) ).

My personal experience:
I used an Asus M3A78 and it had issues with recognizing multiple SATA drives. No BIOS setting or update fixed it either. I sent that thing back and got a Biostar TA770. That board worked great and now resides in my Mom's PC. My current board is a Biostar TA890FXE (I'm partial to Biostar T-series boards).

---

### Post by vttay03 on 2011-01-07
I don't need the onboard video because I've selected a separate, dual monitor, PCI-E card.  I appreciate the insight on the audio capability - I had read some other threads in the forum where certain people were having trouble with the audio output on the ASUS M4A78T-E.  

I monitor temps/voltages with my current system so that was another good suggestion.  I will look into the Biostar motherboards as I haven't yet looked at what they have to offer.  Appreciate your help.

---

### Post by vttay03 on 2011-01-07
I don't need the onboard video because I've selected a separate, dual monitor, PCI-E card.  I appreciate the insight on the audio capability - I had read some other threads in the forum where certain people were having trouble with the audio output on the ASUS M4A78T-E.  

I monitor temps/voltages with my current system so that was another good suggestion.  I will look into the Biostar motherboards as I haven't yet looked at what they have to offer.  Appreciate your help.

---

### Post by cascade9 on 2011-01-07
If you dont need onboard video, the AMD 770/790X/790FX and 870/890FX chipset motherboards are what you should be looking for. 

770, 870- basic model. Fine for almost anyone. 
790X- mid model, more PCIe sots (for crossfire)
790FX, 890FX - top end model. Nice chipset, but more than most people would need (popular with overclocking set due to better coolign a slightly better chips on the FX motherboards).

---

### Post by Yellow Pasque on 2011-01-07
You'll probably want to look at AMD 870 boards then: [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007625+600008296+600008421&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=22&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007625+600008296+600008421&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=22&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

EDIT: beaten to it

---

### Post by vttay03 on 2011-01-07
> **cascade9 said:**
> If you dont need onboard video, the AMD 770/790X/790FX and 870/890FX chipset motherboards are what you should be looking for. 

770, 870- basic model. Fine for almost anyone. 
790X- mid model, more PCIe sots (for crossfire)
790FX, 890FX - top end model. Nice chipset, but more than most people would need (popular with overclocking set due to better coolign a slightly better chips on the FX motherboards).

So based on this, one of the boards I originally selected would be a candidate (the MSI 870A-G54 is based on the 870 chipset)...is it a well known fact that Linux has good compatibility with these chipsets?  This is very useful, I'm glad I posted before buying.

---

### Post by Yellow Pasque on 2011-01-07
Note: The Fintek F71889ED sensor chip on that board is not supported (yet). [http://www.spinics.net/lists/lm-sensors/msg28628.html](http://www.spinics.net/lists/lm-sensors/msg28628.html)

---

### Post by Yellow Pasque on 2011-01-07
If you like Gigabyte: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128443](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128443)
The sensor chip (IT8720) is supported.

---

### Post by vttay03 on 2011-01-07
> **Temüjin said:**
> If you like Gigabyte: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128443](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128443)
The sensor chip (IT8720) is supported.

This is one of the ones I narrowed it down to after following your earlier link.  I searched through the Newegg reviews under "Linux" and "Ubuntu" and it appears to have a good success rate.  This is shaping up to be the one I go with...

I have just recently discovered the "lm-sensors" package and would definitely like to have a compatible chip.  I have written scripts to monitor the temperatures of each CPU core.

---

### Post by Yellow Pasque on 2011-01-07
Good luck with your build. Post back results after running the board for a bit.

---

### Post by vttay03 on 2011-01-07
> **Temüjin said:**
> Good luck with your build. Post back results after running the board for a bit.

Thanks, I definitely will.  Other than digging through hundreds of Newegg reviews, it was hard to find much information.  But this thread has been most helpful.

---

### Post by vttay03 on 2011-01-07
One other question regarding chipsets, I've found the Gigabyte version of the previous motherboard with an AMD 880 chipset at a local store...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128444]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128444")

Are the AMD 880 boards supported well in Linux?  I see that the Audio and LAN chipsets for the 870 board and 880 board are the same.  The major difference I see between the two is that the 880 board has onboard video.  I can't seem to find where you're pulling the information for the sensor chip on each board.

---

### Post by Yellow Pasque on 2011-01-07
It would be far better to get an 870 board + nvidia card for video decoding and any gaming you want to do. AMD may eventually catch up to or adopt nvidia's VDPAU, but it's currently not that way. What do you plan on doing with your build? You already said you have a PCI-e card picked out, so why are you looking at IGP boards?

May I ask what tasks you plan to do with this system?

---

### Post by vttay03 on 2011-01-08
> May I ask what tasks you plan to do with this system?

Sure, I'm not heavily into gaming or anything.  I plan on using it as my everyday computer - I'm into Linux because it runs so much more efficiently/faster than the other operating systems which will remain nameless.  In my current system, I just have a basic nvidia card (chipset is 8400 GS) that works wonderfully.  I have always been able to use nvidia's proprietary drivers without an issue.  When selecting parts for the build, I wanted to try and find a basic card that could drive two monitors because I'm going to purchase a second monitor as well.  The one I selected is:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130395]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130395")

However, the 9500 GT chipset isn't listed on:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia")

And I definitely don't need a $200 video card.  If I could find a card based on the 8400 GS chipset that could drive two monitors, I'd be happy since I've never had any trouble.

---

### Post by cascade9 on 2011-01-08
I'd agree with Temüjin, much better off with a 870 + video card. 

The 9500GT will work fine. The list you linked to is very imcomplete, and outdated. 

You can get dual monitor 8400GS card. If you want 2 x DVI connectors, they gets more difficult to find. You dont want a 8400GS (or 9500 GT) now anyway. Get a GT210 or GT220. Similar cost to the 8400GS, faster, less heat, less power consumption.

---

### Post by vttay03 on 2011-01-08
> **cascade9 said:**
> I'd agree with Temüjin, much better off with a 870 + video card. 

The 9500GT will work fine. The list you linked to is very imcomplete, and outdated. 

You can get dual monitor 8400GS card. If you want 2 x DVI connectors, they gets more difficult to find. You dont want a 8400GS (or 9500 GT) now anyway. Get a GT210 or GT220. Similar cost to the 8400GS, faster, less heat, less power consumption.

So something like this...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130522]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130522")

And I can drive both monitors (one using the DVI and the other using the D-sub or HDMI depending on what inputs the monitor has), right?  I was under the impression for some reason that using the D-sub connector wouldn't give a true digital output.

---

### Post by cascade9 on 2011-01-08
D-sub wont give you digital output. ;) 

Some people can notice the difference between analog D-sub and digital DVI, some people cant (I'd guess that a lot of that would depend on the monitor, but I'm guessing). If you want dual digital outputs from a GT220 with HDMI, DVI and D-sub, just use a HDMI-> DVI converter. ;)

---

### Post by vttay03 on 2011-01-08
Haha whoops, of course.  I'll take the plunge and tack on a $5 HDMI -> DVI converter.

---

### Post by vttay03 on 2011-01-14
Just got done with the build last night.  For the most part everything worked extremely well.  I ended up going with the Gigabyte motherboard (AMD 870 chipset) and the NVIDIA GT220 video card.  I was able to boot a USB flash key with 10.10 and everything seemed to be functional.  I have one minor message I need to research that comes up during boot - I get the message "Too many connections" right before it comes into the desktop.  Hopefully I can take care of that with a little research.  Once again, I appreciate everyone's help because I would have been devestated if I couldn't get the chipsets to work with Ubuntu.

---

### Post by cascade9 on 2011-01-14
Glad its working, I'd feel like  right %&#% if it failed. :lolflag: 

As for the 'too many connections' msg, that seems to be connected to the RL892 sound chip- 

[http://ubuntuforums.org/showthread.php?t=1635278](http://ubuntuforums.org/showthread.php?t=1635278)

I'm pretty sure you can ignore the problem without any issues. If its really bugging you, there are cheap sound cards with decent linux support.

---

### Post by vttay03 on 2011-01-14
Ok thanks for the info, looks like if I can find a way to disable the HD Audio the message may disappear.  Either way it doesn't seem to be causing any harm.  I'll poke around in the BIOS later.

---

### Post by vttay03 on 2011-01-17
After a few days, I've gotten everything stabilized for the most part.  One of the few remaining issues I finally solved last night was getting Suspend to work.  I often used this functionality with my old computer, but I couldn't get it to work with this particular motherboard.  I eventually tracked it down to the fact it provides USB3 capability and the particular module associated with this capability, xhci_hcd, doesn't allow the computer to suspend properly.  There's a fix floating around that involves the following script:

```

#!/bin/bash

# Unload USB3 module before sleep

case "$1" in
  suspend)
    /sbin/modprobe -r xhci_hcd
    ;;
  hibernate)
    /sbin/modprobe -r xhci_hcd
    ;;
  thaw)
    /sbin/modprobe xhci_hcd
    ;;
  resume)
    /sbin/modprobe xhci_hcd
    ;;
esac

```

If you place this script into '/etc/pm/sleep.d/' and name it something like 05_usb3_suspend_help (make sure it's executable), then it will allow the computer to suspend properly.  It will also make sure the module is reloaded when coming out of suspend.  Just thought I'd pass this along for anyone who may be interested in the motherboard in the future.

---

