---
title: "Aspire 3680 Hibernate Under HH"
date: 2008-10-01
forum: Hardware
---

### Post by N00bB00b on 2008-10-01
I've seen some posts on fixing Hibernate and Suspend on the Acer Aspire 3680 in previous versions of U (FF, etc.).

What steps can I use to diagnose and fix Hibernate and Suspend on this laptop in 8.04?

---

### Post by quanumphaze on 2008-10-03
This is what worked for me.

Step 1: Install Ubuntu 8.04

Enjoy

But seriously my laptop is the Acer Aspire 3680 too, though Ubuntu 7.10 had terrible ACPI on this laptop 8.04 was perfect. Suspend works 100%, hibernate is about 80% (X is fine but tty shows complete white).

Try booting strait from the live CD first to see if it's just your particular install that's messed up.

To take a random stab at the problem it may be the acer_acpi module.

You should get this after typing "lsmod | grep acer"
```
you@ubuntu:~$ lsmod | grep acer
acer_acpi              18112  0 
led_class               6020  1 acer_acpi
wmi_acer                9644  1 acer_acpi

```

---

### Post by N00bB00b on 2008-10-03
> **quanumphaze said:**
> This is what worked for me.


You should get this after typing "lsmod | grep acer"
```
you@ubuntu:~$ lsmod | grep acer
acer_acpi              18112  0 
led_class               6020  1 acer_acpi
wmi_acer                9644  1 acer_acpi

```


I AM running 8.04.

Here's what I get:

```

acer_acpi              17216  0 
led_class               5124  1 acer_acpi
wmi_acer                8748  1 acer_acpi

```

As long as you're digging in to help, I haven't gotten the Atheros wireless to work yet.  I haven't done very much, but the directions seen a little convoluted at this point, and there seems to be a fair amount of dissent on that topic.

---

### Post by quanumphaze on 2008-10-04
Those numbers shouldn't be important, just that those lines are there to show that those modules are loaded.

Please try the live CD alone and see if suspend works.

Also give me the output of lspci so I can see any differences that may be causing problems for you.

About the Atheros card. This should work out of the box for everything but WPA-EAP (fine with the WPA-PSK for most consumer routers).

When you type in```
lshw -C network
``` and you see that the wireless entry has "unclaimed" next to it then you should press the wireless switch at boot just after Grub but before the Ubuntu slash screen appears (before Ubuntu's hardware detection).
The atheros card has problems being set up correctly if it's disabled at startup. Unfortunately if you take the battery out the card get's put in the off state and will not be detected at startup. Also there is a script that automaticaly compiles and installs the latest MadWifi (Atheros) driver if you are having problems still. [[link]]("http://ubuntuforums.org/showthread.php?t=798485")

---

### Post by N00bB00b on 2008-10-04
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

---

### Post by N00bB00b on 2008-10-04
As far as the wireless goes, just hitting the button to activate it after Grub didn't do it.  It's kind of annoying, but I see notes from others that on this model of lappie, the LED doesn't come on to indicate that the wireless radio is on in Linux.  Now onto the next idea...

---

### Post by quanumphaze on 2008-10-04
Well the only difference is the Atheros card and I have a fourth line of PCI bridge.

My lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
[COLOR="Red"]00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)[/COLOR]
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
[COLOR="Red"]0a:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)[/COLOR]
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

If it is the Atheros card that's killing your suspend I suggest you try removing it and seeing if suspend works. Be careful with this as you may break stuff, make sure you take anti-static precautions.

It also could also be the BIOS version. Type: [FONT="Courier New"]sudo lspci | less[/FONT] and look for something like [FONT="Courier New"]version: v1.3216 (10/27/06)[/FONT] under the *-firmware section.

First get check the BIOS version. If it's the same as mine (1.3216) then take out the wireless card and check suspend then.

I would also recommend you test newer live CDs to make sure it's not just Ubuntu.

---

### Post by quanumphaze on 2008-10-04
> **N00bB00b said:**
> As far as the wireless goes, just hitting the button to activate it after Grub didn't do it.  It's kind of annoying, but I see notes from others that on this model of lappie, the LED doesn't come on to indicate that the wireless radio is on in Linux.  Now onto the next idea...

Odd, my wireless indicator LED is always on, even when it's disabled. If you still have Windows installed, make sure the card is on before you shut down.

Well it's more evidence that the wireless is the source of all the world's problems.

---

### Post by N00bB00b on 2008-10-07
BTW, it's not that I have this working yet (either wireless or Hibernate).  I don't.  I have been really busy, though.

Wireless even with Mad doesn't work still.  Waiting for further suggestions.

I'm going to build a boot CD this afternoon and see if that makes hibernate work.

---

### Post by N00bB00b on 2008-10-08
OK, I finally built the live CD, so here's the results from the experiments, if anyone is still paying attention:

LIVE CD (8.04):
Suspend:  Works
Hibernate:Not listed as an option

Regular boot from the hard drive:
Suspend:  Works
Hiberhate: Apparently causes the machine to shutdown, because when I hit the power button, I get grub

---

### Post by quanumphaze on 2008-10-09
> **N00bB00b said:**
> ... if anyone is still paying attention

I'm still here. I have been busy too with lots of lab reports overdue and now 3 tests next week.

Anyway it's good to see that suspend is sorta working for the live CD. The hibernate feature is supposed to save the current session (RAM image) to disk then proceed to turn off the computer. Next time you boot (Grub should still work as normal) the kernel will detect the RAM image and load that.

As for the wireless there's not much I can do for you. All I can say is to either:
[LIST][*]Find a way to get Madwifi working (Just to clarify: Madwifi is the project that develops the drivers for Atheros cards)
[*]Wait for Ubuntu 8.10 (not long now or get the beta) or try out other live CDs
[*]Or try out the Ath5k drivers (made by the Madwifi guys but may not be as mature as the other ones)[/LIST]

I suspect that the Madwifi problems may be that it can't detect the type of chip, it says AR242x and according to the [Madwifi Chipsets page]("http://madwifi.org/wiki/Chipsets") it should be either a 2424 or 2425.

It may be best to make a new thread about this if 8.10 beta doesn't work. Be warned about the massive flood of threads that come out after a new release, you may never get your thread answered.

---

### Post by N00bB00b on 2008-10-09
Unfortunately, when coming back from "hibernate" it doesn't work as one would hope - previous session isn't restored.

---

