---
title: "Strange mouse behaviour in Ubuntu 8.10"
date: 2008-11-20
forum: General Help
---

### Post by stasheck on 2008-11-20
Hello fellow Ubunters!

I'm rather not a rookie, but recently I stumbled upon a problem for which I'm yet to find a solution.

Sometimes my mouse stops working in a very specific way: I can still see cursor, defaulted to standard Ubuntu 8.10 arrow, but I cannot click anywhere, nor the cursor ever changes it's shape.

Only thing that helps is X restart, although it helps for much shorter time (say, after a boot I can work a couple of our with mouse working, but after X restart it's only minutes).

I tried just swiching to terminal (Alt+Ctrl+Fn), but doing it first time doesn't work (works only for a second, and then I'm again in X), doing it second time freezes my system.

I can't see any errors in system log, dmesg nor in Xorg.0.log. I tried checking xev, but it doesn't see any mouse events. I tried reloading psmouse module, but that didn't work either.

Does anyone has any ideas? I'm ready to do any tests and support each and every log requested - but now I just need to do a reboot, working in X using keyboard only is pain...

---

### Post by stasheck on 2008-11-24
Does nobody has any idea, or did I post sth wrong?

---

### Post by stasheck on 2008-11-27
Thank you for your shockingly helpful support.

As to date, I eliminated following probable causes, but still to no avail:
- video driver (proprietary nVidia)
- flash player in Firefox (this one because mouse often stops working when opening flash sites, like last.fm)

Unfortunately, this problem is not easy replicable - there is no single action to which I can blame my problem.

Additional info:
- VirtualBox (with WinXP SP2), Firefox 3.0 and Konsole (KDE4) all seem to have sth to do with the problem - all problems happened when they were running; unfortunately it is my main work computer, so I cannot just turn off FF/VB/K for a couple of hours just to check which one may be the culprit
- I haven't mention that touchpad also stops working (as any other mouse I connect to computer) - I can control cursor position using all these devices, but no clicking and no context actions (like cursor's shape changing)

I'm starting to suspect hidden kernel problem - most of the apps I know should at least put some info to logs, and I can't find any.

I'd like to ask you to answer at least writing "Dude, strange problem, no idea" - because I feel like I'm invisible on this forum.

---

### Post by stasheck on 2008-12-01
Wow, I am truly invisible - noone can see me. My guess is that in the minute I'd start swearing some mod would decide to see me after all :(

Anyway, I think it's not the kernel - changed from 2.6.27-7 to 2.6.27-9 and still the same problem. Or maybe the same bug is in both compilations...

I forgot to add - I have the same problem when I boot to KDE4, only faster - mouse works for a couple of minutes, then stops. So it's not windows manager.

Am I posting in wrong forum?

---

### Post by stasheck on 2008-12-01
OK, now VirtualBox has been ruled out - changed from 1.6.6 to 2.0.6 (non-ose) and the problem persists.

Can someone point me where can I read about how the mouse events are processed?

---

### Post by happyhamster on 2008-12-01
> **stasheck said:**
> 
I'd like to ask you to answer at least writing "Dude, strange problem, no idea" - because I feel like I'm invisible on this forum.
Ok, I'm not sure if I can help, but I'll try. :) 

- Could you show the output of:

cat /proc/interrupts

- before and during the mouse-weirdness?

- Also what kind of system are you using? (the exact model of the motherboard would be useful).

- Are you using an usb mouse, or a regular one?

- Are you booting with special kernel-parameters? Try:

cat /boot/grub/menu.lst | grep quiet

- It will output the relevant lines from the /boot/grub/menu.lst file.

- Also, could you show the output of:

uname -a

dmesg | grep irq -i

(the last one will show any interrupt-related messages in your log).


- If you're not afraid of poking in the computer's BIOS settings, take a look if there's a "Plug and play OS" setting somewhere. If so, test with the setting reversed.

Good luck, and keep us informed.


[edit: typo]

---

### Post by AntonOlsen on 2008-12-01
You're not invisible, but there are a couple other threads out there.

I'm having a similar issue and have commented on a couple other threads about this problem.  Search for mouse click problem and you should find them.  I'd copy and paste a few urls, but my mouse isn't working at the moment.  

So far it appears people are blaming Xinerama.

I've been reluctant to test without Xinerama, but I'm about to take the plunge and live without one monitor for a few days to see if that is the problem.

---

### Post by AntonOlsen on 2008-12-01
Here's the bug report about this problem:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/296167](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/296167)

Still no mouse, but I got bored waiting for something to finish compiling before I ctrl-alt-bkspc out of here.

---

### Post by fragos on 2008-12-02
The only mouse strangeness I've seen with 8.10 only occurred once. In the Epiphany browser when I hovered over a toolbar icon it visualy indicated the hover but the cusor was gone. I could click the icon and when I moved off the toolbar the cursor reappeared. Only happened once. Applications don't handle cursor visablility in a consistant way unless they use the same libraries. Gnome for example provides libraries for a consistant look and centralized theme control. Aps like Firefox do their own thing.

---

### Post by stasheck on 2008-12-03
Fragos: I think it's not the same problem.

AntonOlsen: haven't write about it 'cause I didn't want to spoil someone's thinking process, but I'm using Xinerama too (only dual-monitor extension that suits my needs)

happyhamster:
> cat /proc/interrupts
           CPU0       CPU1
  0:     594923     563700   IO-APIC-edge      timer
  1:       1816       1710   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:          9         12   IO-APIC-fasteoi   acpi
 12:      85685      83638   IO-APIC-edge      i8042
 14:      19094      19164   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:     229607     223760   IO-APIC-fasteoi   nvidia
 17:          0          0   IO-APIC-fasteoi   eth1
 18:          6          6   IO-APIC-fasteoi   mmc0
 19:          0          2   IO-APIC-fasteoi   ohci1394
 20:      29706      29472   IO-APIC-fasteoi   uhci_hcd:usb1, uhci_hcd:usb4, ehci_hcd:usb7
 21:     316606     310487   IO-APIC-fasteoi   uhci_hcd:usb2, uhci_hcd:usb5, HDA Intel
 22:         15         13   IO-APIC-fasteoi   ehci_hcd:usb3, uhci_hcd:usb6
2297:      51628      51575   PCI-MSI-edge      eth0
2298:      77004      75635   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:     884257     905034   Local timer interrupts
RES:     840013     855366   Rescheduling interrupts
CAL:     419661     360667   function call interrupts
TLB:       2000       3077   TLB shootdowns
TRM:      25299      25299   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
SPU:          0          0   Spurious interrupts
ERR:          0

that's before - I put "after" as soon as I stumble upon it ;-)

> cat /boot/grub/menu.lst | grep quiet
# defoptions=quiet splash
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=408882C08882B3C6 loop=/ubuntu/disks/root.disk ro quiet splash
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=408882C08882B3C6 loop=/ubuntu/disks/root.disk ro quiet splash
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=408882C08882B3C6 loop=/ubuntu/disks/root.disk ro quiet splash

> uname -a
Linux ubuntu 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

> dmesg | grep irq -i                                                                                      
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                                                 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                                                                                                          
[    0.000000] ACPI: IRQ0 used by override.                                                                                                                                         
[    0.000000] ACPI: IRQ2 used by override.                                                                                                                                         
[    0.000000] ACPI: IRQ9 used by override.                                                                                                                                         
[    0.664734] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7                                                                                                                    
[    0.664734] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10                                                                                                                       
[    0.664734] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4                                                                                                                    
[    0.664734] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)                                                                                                                  
[    0.664778] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)                                                                                                   
[    0.664932] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)                                                                                                   
[    0.665085] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)                                                                                                   
[    0.665223] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.                                                                                      
[    0.720052] PCI: Using ACPI for IRQ routing                                                                                                                                      
[    0.740092] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0                                                                                                                              
[    0.757333] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                                                                         
[    0.757345] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.757360] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.757375] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.757389] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.699719] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.702023] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.705542] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.705548] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.725347] rtc0: alarms up to one month, y3k, hpet irqs
[    2.233133] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.233241] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    2.441302] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.441408] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    2.545408] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.549449] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    2.773751] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.773831] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    2.981901] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.981999] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    3.086140] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.086220] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    3.294469] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.298447] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    3.523161] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.523438] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.575164] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f1aff800-f1afffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.580809] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.582186] ata1: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffb900 irq 2298
[    3.582191] ata3: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffba00 irq 2298
[    4.308433] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.617692] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
[    4.623316] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.628707] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    4.628710] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[   15.049830] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   15.134477] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.133206] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.649772] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 2332.101347] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

I'm using Dell XPS M1330 laptop with Nvidia video card (GF8400GS). Mouse is attached via USB, I guess touchpad too - but I think that's not the problem, as USB detection works after "weirdness" (I can unplug mouse and plug it back, and still I can move cursor, but no clicking).

---

### Post by stasheck on 2008-12-03
OK, thanks to reading bug reports I've been able to deactivate Xinerama and switch TwinView on. I don't know if I was doing something wrong previously, or the nvidia driver matured, but now I am able to use TwinView.

Hint for anyone else with 2-monitor setup: you have to run nvidia-settings via sudo (which is not by default), set everything up, "Save to xconfig file". and restart X.

AntonOlsen: mthx!

---

### Post by karlwilbur on 2009-01-06
Posted workarounds here:
[http://ubuntuforums.org/showthread.php?p=6507427](http://ubuntuforums.org/showthread.php?p=6507427)

---

