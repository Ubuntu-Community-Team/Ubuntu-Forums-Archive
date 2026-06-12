---
title: "HP Pavilion dv7, video card issues"
date: 2013-06-18
forum: Hardware
---

### Post by hondaprelude on 2013-06-18
Hello I am very new to ubuntu but jumped all in on it. I have a hp pavilion dv7 which was having some issues with windows 7 so I decided to put ubuntu 12.04 on here. I now cannot use my hdmi port on the pc and also if I try to make a video full screen it lags really bad on the video but you can hear the audio perfectly fine. I really need some help I read that I may need a proprietary driver but it has been so long since I have dealt with the video card in this laptop I have forgotten which one is in here. Is this something I can find out through the terminal? And once I find this out how do I install a proprietary driver?

---

### Post by papibe on 2013-06-18
Hi hondaprelude.

Could you post the output of this command?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by hondaprelude on 2013-06-18
Ok so I found the lspci command and this is the information I got:

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series] (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company Device 1641
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 4000 [size=256]
        Memory at f0400000 (32-bit, non-prefetchable) [size=64K]
        Memory at f0300000 (32-bit, non-prefetchable) [size=1M]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: radeon
        Kernel modules: radeon


02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Robson CE [AMD Radeon HD 6300 Series] (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company Device 1641
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f0200000 (64-bit, non-prefetchable) [size=128K]
        I/O ports at 3000 [size=256]
        [virtual] Expansion ROM at f0240000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: radeon
        Kernel modules: radeon


02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]
        Subsystem: Hewlett-Packard Company Device 1641
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f0220000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

I do have a switchable video card for when its plugged in or unplugged from power is this some of my issue any and all help will be much appreciated.

---

### Post by papibe on 2013-06-18
Thanks.

The result is a little odd to me, as you had 2 discrete graphic cards (may be one is the mobo's integrated graphics).

Any way, open the application 'Additional Drivers'. There it should be listed the proprietary AMD driver so you can install it. It may require restart the machine to take effect.

Let us know how it goes.
Regards.

---

### Post by hondaprelude on 2013-06-18
Ok so an update I found 3 proprietary drivers in the additional driver application but none of them helped they didn't make it worse but at the same time they didn't make it any different. here is a screen shot of the drivers I tried to install.
[IMG][[IMG]http://i1295.photobucket.com/albums/b622/hondapreludebb2/Screenshotfrom2013-06-18202309_zps851bd2a1.png[/IMG]]("http://s1295.photobucket.com/user/hondapreludebb2/media/Screenshotfrom2013-06-18202309_zps851bd2a1.png.html")[/IMG]

---

### Post by hondaprelude on 2013-06-20
Has anyone encountered this issue before. I still am unable to use my hdmi cord or watch a video full screen because of this.

---

### Post by SeijiSensei on 2013-06-20
You have a machine with hybrid video.  Go into the BIOS and switch to "fixed mode".  Afterwards, try installing the driver again.

---

### Post by hondaprelude on 2013-06-20
Ok thank you I will try that and let everyone know how it goes.

---

### Post by hondaprelude on 2013-06-20
There is no option in the BIOS for this laptop to change it to only use a single graphics card instead of the hybrid system.

---

### Post by papibe on 2013-06-20
Set that, and then run this command to know which one got selected (with luck it'll be the 6300):
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by SeijiSensei on 2013-06-21
The "fixed mode" option was added to the firmware in 2011.  I had to upgrade my dv6t to enable it.  You can check to see what the most recent firmware release is for your machine here: [http://forum.notebookreview.com/hp-pavilion-notebooks/595505-current-hp-pavilion-bios-releases.html](http://forum.notebookreview.com/hp-pavilion-notebooks/595505-current-hp-pavilion-bios-releases.html)

---

### Post by hondaprelude on 2013-06-22
there is no way for me to set that in the bios :(

---

### Post by SeijiSensei on 2013-06-22
Did you read my last post?  The firmware for your BIOS may not contain the option.  You need to see if there is a newer version that you can install.

---

