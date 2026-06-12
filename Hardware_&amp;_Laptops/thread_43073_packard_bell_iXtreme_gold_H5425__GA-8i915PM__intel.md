---
title: "packard bell iXtreme gold H5425 / GA-8i915PM / intel 915P"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by ubuntu_demon on 2005-06-20
Hi,

A friend of mine tried the livecd :

When the livecd is booted Ubuntu can't get into gnome. Somewhere during starting up gnome it stops starting up (the mouse doesn't respond anymore as well).

So we decided to install Ubuntu (dualboot). The issue still remains. I don't know whether the kernel crashes or it's xorx. But the pc doesn't respond to anything anymore
(ctrl-alt-delete,ctrl-alt-backspace,ctrl-alt-f1 .. nothing works)

This pc is a :

packerd bell iXtreme gold H5425

motherboard : GIGABYTE GA-8I915PM version 1.1 
(sunshine micro-ATX)
chipset : intel 915P

videocard :
ATI: x600 PRO 256 mb CRT/TV

cordless mouse and keyboard connected using USB

I've tried a lot.Ive also tried xfce4. It crashes right after I click on an application.(the system also freezes entirely and I have to do a hard-reset)

Also sound doesn't work. But that's a minor issue compared to the freezing :). I've tried disabling the on board sound. It had no effect on the freezing problem.

I've modprobed snd_intel8x0 in an attempt to get sound working. Didn't help.

cat /dev/asound/cards didn't show any cards

this is /cat/proc/interrupts :

```

           CPU0       CPU1       
  0:     606802          0    IO-APIC-edge  timer
  1:          9          0    IO-APIC-edge  i8042
  7:          0          0    IO-APIC-edge  parport0
  8:          1          0    IO-APIC-edge  rtc
  9:          1          0   IO-APIC-level  acpi
 12:         67          0    IO-APIC-edge  i8042
 14:       6663          0    IO-APIC-edge  libata
 15:       8808          0    IO-APIC-edge  libata
 16:          0          0   IO-APIC-level  uhci_hcd
 18:       7544          0   IO-APIC-level  uhci_hcd
 19:          0          0   IO-APIC-level  uhci_hcd, saa7133[0]
 21:       1536          0   IO-APIC-level  eth0
 23:      33466          0   IO-APIC-level  uhci_hcd, ehci_hcd, ohci1394
NMI:          0          0 
LOC:     606456     606455 
ERR:          0
MIS:          0

```

I suspect that the freezing problem is related to the mainboard. To narrow it down a bit..... it could be that this is related to the 82801 chip since usb and(mouse) audio go over this chip.

---

### Post by ubuntu_demon on 2005-06-20
(please delete this post)

---

### Post by ubuntu_demon on 2005-06-20
Here's dmesg and xorg log. This is a rar file (I can't get into Ubuntu remember ;))

---

### Post by ubuntu_demon on 2005-06-21
I changed DRI lines (using dpkg-reconfigure xserver-xorg).The screen went black. Can't remember if this xorg.conf is the "original" or the one with the black screen.

---

### Post by XDevHald on 2005-06-21
Might not be much help even though I work for Dell, I am not familiar with this type of computer myself. Don't use a cordless mouse due to the drive not being recognized. Also, you need to check on what kernel you're using of course in this case it would be the 2.6.10-5-386. See if you can get the boot to go into safe mode when doing the boot up by hitting "ESC"

I could be wrong on some areas of ths post, but again, I am not familiar with this unit :( but try it out. I'll research it more in a bit.

---

### Post by ubuntu_demon on 2005-06-21
[QUOTE=BB]Might not be much help even though I work for Dell, I am not familiar with this type of computer myself. 
[/QUOTE]

it's a "packard bell" not a dell :)

[QUOTE=BB]
Don't use a cordless mouse due to the drive not being recognized. 
[/QUOTE]

I've tried a cordless mouse and a mouse with a cord (both USB). On my advice he's going to try ps2 mouse and keyboard.

[QUOTE=BB]
Also, you need to check on what kernel you're using of course in this case it would be the 2.6.10-5-386. 
[/QUOTE]

I've tried the latest 386 kernel and the latest 686-smp kernel.

[QUOTE=BB]
See if you can get the boot to go into safe mode when doing the boot up by hitting "ESC"
[/QUOTE]

gnome doesn't boot in safe mode. gnome doesn't even boot into xterm.

[QUOTE=BB]
I could be wrong on some areas of ths post, but again, I am not familiar with this unit :( but try it out. I'll research it more in a bit.[/QUOTE]

thnx

---

### Post by XDevHald on 2005-06-21
well then, shut me down why don't you ;) sorry about the dell thing, my head is in a lot of paper work at the moment. Also, gnome goes into recovery mode :p not safe, my fault again.

---

### Post by ubuntu_demon on 2005-06-21
[QUOTE=BB]well then, shut me down why don't you ;) sorry about the dell thing, my head is in a lot of paper work at the moment. Also, gnome goes into recovery mode :p not safe, my fault again.[/QUOTE]
 :-P

---

