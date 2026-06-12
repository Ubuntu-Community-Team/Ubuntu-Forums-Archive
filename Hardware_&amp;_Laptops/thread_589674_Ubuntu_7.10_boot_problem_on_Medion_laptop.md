---
title: "Ubuntu 7.10 boot problem on Medion laptop"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by LUFC72 on 2007-10-24
Hi

I am a complete newbie to ubuntu! Just installed 7.10 on my Medion laptop and cannot get it to boot up. Loads to dual boot screen and then when I select ubuntu screen goes black and nothing happens? 

I had problems with the live cd working at first but found something on a forum that solved that. Had to add  in the boot option "live acpi=off noapic".No idea what that means but it solved it.  Installation onto to hard drive was fine but just cannot get it to boot from hard disk?

My laptop details are;

Intel Celeron 2.6
512 mb ram
ATI mobility radeon 9000 igp


If more info is needed to help solve the problem post it and let me know.

Thanks in advance.

---

### Post by alex77 on 2007-10-25
have you added those boot options to your kernel for when you try to boot from hard drive?

if not try this:

when you boot up, press escape to enter the GRUB menu


press e
select the kernel line and press e again to edit it.
remove the words quiet and splash from the line
add acpi=off to the end of the line
add no apic to the end of the line
press ENTER
press b to boot

this will boot without the splash screen so that you can see what problems you are having when booting.
It also uses the same arguments you added to get the live cd to work, so hopefully you should be able to boot up.

---

### Post by alex77 on 2007-10-25
You may also wnat to look at this thread. sounds similar? 

> **insulae said:**
> ok i solved everything:

the acpi problem i solved passing to the kernel in the grub the next parameters:

```

pci=assign-busses apicmaintimer idle=poll reboot=cold,hard

```

the wifi i solved with this information:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

the battery work perfect with the klaptop package (run klaptop_check)

Grettings
insulae

> **insulae said:**
> (first sorry, my english is bad :))

ok i have a:

Compaq Presario V3415LA (V3000), this model is only in Latin America i think, so the notebook have the next hardware:
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

```

my compaq don't want to work with Linux, when i boot with the LiveCD of Ubuntu the notebook  is crashes every time, i try booting with the options:

```
acpi=off pnpbios=off
``` and with this options i can install and use Linux, but if i remove one of this 2 parameters the notebook crash again.

this is incompatibily of my mother with the kernel linux? anybody can tell me where i can find information about this, and if somebody is working with this problem.

Grettings
insulae

---

### Post by mnewell on 2007-10-25
I see there's a lot of problems with Radeon cards having problems.  In my case I have an old Dell 600m with a Radeon card in it.  Boots up, gives the Ubuntu splash, then blanks and freezes.  I ended up booting in single user mode (press "esc" at grub, then select recovery mode) and going through the "/etc/rc*x*.d" files (where "*x*=2 though 5) and removing the "S13gdm" links.  That allowed me to boot without the X desktop GUI running so at least I could get the system back up.  Now all I have to do is figure out how to get around the X problems... :-)

Mike

---

### Post by LUFC72 on 2007-10-26
Thanks for the replies. Managed to get it to boot now by adding the acpi=off and no apic. I tried this the other day but it would not work? but today it did. 

Cannot get my wlan to work now though? my laptop has a prism 54 built in wlan. I noticed the other day when it was booting and going through all the blurb on screen that it always stopped at the prism54 bit.Stated something like maybe a fault or irq problem?

Also when I shutdown information on the screen states system halted and it just hangs. Something to do with network manager bus connection failed?

will search the forum for more info

---

