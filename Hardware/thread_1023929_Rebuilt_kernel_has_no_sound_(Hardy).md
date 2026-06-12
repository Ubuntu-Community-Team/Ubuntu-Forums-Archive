---
title: "Rebuilt kernel has no sound (Hardy)"
date: 2008-12-28
forum: Hardware
---

### Post by Schuenemann on 2008-12-28
Hi,

I recompiled kernel 2.6.24 (my first) in Hardy with the default options and when I booted the new kernel I had no sound.
I ran alsaconf and this is the message I got:
> 
No supported PnP or PCI card found
Would you like to probe legacy ISA sound card/chips?

Output from lspci:
> 00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)


What should I do?

Thanks

---

### Post by igknighted on 2008-12-28
You probably forgot to compile the modules for your sound card in menuconfig.  Unfortunately, I'm not sure how to compile just modules, you might have to redo the whole thing.

---

### Post by linux_tech on 2008-12-28
I've found this to be helpful -
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Schuenemann on 2008-12-28
I tried that tutorial but it seems I don't have any snd-* module.


I think igknighted is right.
I went to menuconfig and it looks like there's no ALSA support:
[IMG]http://img246.imageshack.us/img246/9540/alsaconfigbo2.jpg[/IMG]

Is this right?
If so, is there a way to fix without recompiling again?

---

### Post by igknighted on 2008-12-28
> **Schuenemann said:**
> I tried that tutorial but it seems I don't have any snd-* module.


I think igknighted is right.
I went to menuconfig and it looks like there's no ALSA support:
[IMG]http://img246.imageshack.us/img246/9540/alsaconfigbo2.jpg[/IMG]

Is this right?
If so, is there a way to fix without recompiling again?

That listing for Alsa is just a menu to another screen.  You need to go in there and check that not only is alsa compiled (as a module <m> is OK), but that the driver that your card uses is being built as well (in that alsa menu)

---

### Post by Schuenemann on 2008-12-28
I did. There's nothing checked there too.
So I'll have to recompile it again :roll:

---

### Post by igknighted on 2008-12-28
> **Schuenemann said:**
> I did. There's nothing checked there too.
So I'll have to recompile it again :roll:

Yeah.  No damage done tho, just gotta recompile.  Most people will find that they need to try it a few times before they get one that works, so it's not unusual at all.

Try the kernelcheck app ([http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)) to help automate the process, or see the master kernel thread for more help.

Anything in particular you were trying to gain by recompiling?

---

### Post by Schuenemann on 2008-12-28
Just trying to learn something.

But I want to remove stuff I won't need (different processors, ISA, etc). I'll take a look at KernelCheck.

Thanks.

---

### Post by Schuenemann on 2009-01-02
Alright! After 3 more rebuilds, I finally got it working.
Thanks again.

---

