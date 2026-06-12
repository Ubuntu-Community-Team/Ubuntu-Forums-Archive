---
title: "First time Linux/Ubuntu user with PCMCIA woes."
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by Turbo Donkey on 2006-02-13
Hi everyone!

For my first post I would like to get stuck right in!

I have sucessfully dual booted my Toshiba A60 laptop with Ubuntu/XP, everything seems to be working ok... so far!

I have been trying for a couple of days to get my Linksys WPC54G v1.2 (PCMCIA) card working with ndiswrapper, I have tried EVERY damn driver I can get my hands on and I cant get ndiswrapper to acknowledge the hardware, I get "Driver Present" but no more.

I got the output from lspci, which I am assuming will show me details of the card, but it doesn't seem to see beyond the cardbus controller:

---snip---
root@ubuntu:/home/turbodonkey# lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device cab3 (rev 05)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4345 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 434d (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4437
0000:02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
root@ubuntu:/home/turbodonkey#
---snip---

Can anyone point me in the right direction? the card works fine in my XP installation!

Bear in mind that I am a 2 day old linux noob!


Added: cardctl output:

---snip---
root@ubuntu:/home/turbodonkey# cardctl ident
Socket 0:
  no product info available
---snip---

---

### Post by K.Mandla on 2006-02-14
Hi. The fact that the hardware isn't even acknowledged is a little scary. Depending on how old your laptop is, you might be having [this problem]("http://ubuntuforums.org/showthread.php?t=125334"). However, there are still a couple of things you can try.

If you add *acpi=off* to the GRUB boot command, it might free up the card. Also, you might add *pci=assign-busses* to the boot command, and that might free up a [problem with subordination]("http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html#knownproblems"). However, if you're going with the straight Ubuntu 5.10 install, you might find that command to be useless; I believe it's not implemented until later kernels (but again, I could be wrong). If you can wait a month or two, Dapper might support it.

However, it doesn't mean you're stuck. In my experience, different distributions of Linux have better support of PCMCIA ports. Try [DSL]("http://www.damnsmalllinux.org"), which is built only as a Live CD, and is intended for older machines and uses earlier kernels (which might have different PCMCIA routines). It's built on Knoppix, by the way, which I haven't tried, but I have been told has better hardware support (is that possible? :p )

Good luck.

---

### Post by Turbo Donkey on 2006-02-14
OK, excellent, thaks for that!

I had the problem with subordination, adding the line pci=assign-busses into the menu.lst file sorted that out...

Now...

I have got the wpa supplicant working when I run the command:

wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd

But this only works after boot, and I have to type the command into the root console...

This is causing a very long boot time waiting for the networking to time out during boot and fail...

How can I incorperate my setup into the boot process so that wlan0 comes up during boot instead of timing out and failing?

Many, many, many thanks for getting me this far!

---

### Post by K.Mandla on 2006-02-14
Great! I'm glad to hear it. It's good to know that the *assign-busses* option works on a straight install.

I might have to dodge the wpa question, though. I haven't any experience with that. I'm sure someone else will have an idea for you, though. 

Cheers!

---

### Post by macdo on 2006-02-19
Can't help with the wpa question either, I'm afraid - but if you press ctrl-c during the "hang" time when your pc is trying to find a network, it will go straight on to the next step... Not a fix, but at least it's a workround :) 

-- 
macdo

---

