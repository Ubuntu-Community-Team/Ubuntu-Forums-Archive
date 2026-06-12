---
title: "acx100 wlan problems"
date: 2004-11-03
forum: Hardware &amp; Laptops
---

### Post by elempoimen on 2004-11-03
I have a PCMCIA card based on the TI ACX100 chipset (I know, I know...).

Looking at dmesg, all is well during initialization until here:

> acx100_issue_cmd failed: Invalid parameter [1200 uSec] Cmd: Ah, Result: Eh
cb =0x1AE

Then all hell breaks loose.  Any ideas on what I can do to fix this?

---

### Post by elempoimen on 2004-11-03
[QUOTE=elempoimen]I have a PCMCIA card based on the TI ACX100 chipset (I know, I know...).

Looking at dmesg, all is well during initialization until here:



Then all hell breaks loose.  Any ideas on what I can do to fix this?[/QUOTE]
 I don't know if it will help any, but the only other distro I was able to get this card working in was MEPIS.  There, I used this slick KDE wireless config app to manually assign the 2.4 GHz frequency to the card, then it worked like a charm.  There is no such thing in Ubuntu.

The card is detected.  The light is on, but Linux won't see it as a network interface.  I tried the ndiswrapper, I tried modprobe, I tried everything I can think of.

---

### Post by Magneto on 2004-11-03
Have you tried the sourceforge drivers and instructions?

---

### Post by Fred_og_ro on 2004-11-04
I got it working!!

It all came with Ubuntu Warty 4.10.
My setup:
Toshiba Satellite 4000CDT
PCMCIA: D-Link AirPlus DWL-650+ (with the acx100)

What I did:
1. In bios.
 - Disable parallel port ("Not used" in my bios)
 - Set the PC Card Controller Mode to "CardBus/16-bit"
btw. I have "Device Config. = All Devices" and not "Device Config. = Setup by OS"

2. Moved the existing firmware in /lib/hotplug/firmware that applied to the acx_pci card (RADIO0d.BIN-2.6-8.1-3-386, RADIO11.BIN-2.6.8.1-3-386, RADIO15.BIN-2.6.8.1-3-386, TIACX111.BIN-2.6.8.1-3-386, WLANGEN.BIN-2.6.8.1-3-386)

3. Downloaded the latest drivers from [ftp://ftp.dlink.co.uk/wireless/dwl-650+/](ftp://ftp.dlink.co.uk/wireless/dwl-650+/) (I choose the dwl_650+_b_drv_v3.07.zip)

4. unzipped this and copied the firmware files from the Win2000 folder to /lib/hotplug/firmware. Do not add "-2.6.8.1-3-386" ending to these files like ubuntu does. I did like this from the Drivers/Win2000 folder
$: sudo cp RADIO0d.BIN /lib/hotplug/firmware/
$: sudo cp RADIO11.BIN /lib/hotplug/firmware/
$: sudo cp RADIO15.BIN /lib/hotplug/firmware/
$: sudo cp WLANGEN.bin /lib/hotplug/firmware/WLANGEN.BIN

(note the last file needs to be converted to uppercase letters)

5. rebooted (i know, i know)

And that was it...no messing with any gui tools, no messing with any config files. 

hope this helps for you.

---

### Post by elempoimen on 2004-11-04
Fred_og_ro,

Thank you!  This looks good, and I'm willing to give it a shot.  This is one of the things that keeps me from dumping XP (that and power management issues).  A question: why disable the parallel port?  In my case, I need it for compatibiliy with a non-USB printer at one of my remote offices.  Can this be done without disabling that port?  I'm not sure I can even do this in my BIOS...IBM Thinkpad T23.

Thanks,
I'll be waiting for your reply!
elem

---

### Post by Fred_og_ro on 2004-11-05
[QUOTE=elempoimen]
A question: why disable the parallel port?  In my case, I need it for compatibiliy with a non-USB printer at one of my remote offices.  Can this be done without disabling that port?  I'm not sure I can even do this in my BIOS...IBM Thinkpad T23.[/QUOTE]

I did it since there was an IRQ conflict....but I also had trouble getting my sound card working (Yamaha OPL3-SA2)...and since I tried to fix both things at the same time (i know, i know) I can't say which item it fixed (sound-card or acx_pci card) ](*,)

I plan to enable the parallel port to see what that does....maybe it will work itself out. 

Good luck with getting your acx_pci card up and running.

---

### Post by jchstevens on 2004-11-05
Fred_og_ro,

I am also having trouble getting my Yamaha OPL3-SA2 sound card to work with Ubuntu, although my computer is a tower rather than a laptop.  I am also using the Ubuntu 4.10 Live CD at the moment.  The card works fine with XP, but also remains silent with my currently installed linux (Debian Unstable, SID).
Do you have any suggestions for getting the card working with Ubuntu/Debian?

Thanks,

Julian

---

### Post by Fred_og_ro on 2004-11-05
Julian,

Absolutely. I followed the instructions given here:
[http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html)

I did point 1 + 2 and then rebooted (i know, i know...)

Good luck

---

