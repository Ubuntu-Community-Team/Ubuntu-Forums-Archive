---
title: "APIC errors on dmesg"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by xpan on 2007-01-10
I have the following problem. Sometimes when I shutdown Ubuntu edgy freezes while displaying some garbage on screen. Only solution is to hold the power-off button.

I ran dmesg and noticed there are many APIC error on CPU0: 40(40) messages.

I don't know if this is the cause for this malfunction but these problems appeared some days after I had installed the binary drivers for my ati mobility radeon X700 (various distro updates had occured in the meantime).

It seems that many laptop (and some desktop) users face the same situation and it seems to be connected with the SiS chipsets. 

I was wandering if the only solution is to recompile the Kernel ([http://saintaardvarkthecarpeted.com/blog/?p=184#comment-11917](http://saintaardvarkthecarpeted.com/blog/?p=184#comment-11917)) or downgrade to a another kernel version.

Is there any howto in order to *safely* recompile the kernel?

APIC is needed for dual core processor. I don't have such a processor. Do I need APIC?

How can I see what is the cause of the shutdown malfunction? and how can I "cure" this APIC errors?

I use Acer 3023 WLMi.

(part of dmseg output follows) 
> [17179591.296000] EXT3 FS on hda2, internal journal
[17179591.480000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179591.480000] NTFS-fs warning (device hda1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17179591.516000] r8169: eth0: link up
[17179591.532000] NTFS volume version 3.1.
[17179592.244000] NET: Registered protocol family 10
[17179592.244000] lo: Disabled Privacy Extensions
[17179592.244000] IPv6 over IPv4 tunneling driver
[17179592.824000] NET: Registered protocol family 17
[17179594.100000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179596.068000] ACPI: AC Adapter [ADP1] (on-line)
[17179596.284000] ACPI: Battery Slot [BAT0] (battery present)
[17179596.308000] ACPI: Power Button (FF) [PWRF]
[17179596.308000] ACPI: Lid Switch [LID0]
[17179596.308000] ACPI: Sleep Button (CM) [SLPB]
[17179596.368000] ACPI: ACPI Dock Station Driver 
[17179596.440000] ibm_acpi: ec object not found
[17179596.468000] pcc_acpi: loading...
[17179596.576000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179596.576000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179596.796000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179596.796000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[17179596.796000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc (1250 mV)
[17179596.796000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13 (1075 mV)
[17179596.796000] cpu_init done, current fid 0xa, vid 0xa
[17179598.692000] [fglrx] Maximum main memory to use for locked dma buffers: 1171 MBytes.
[17179598.692000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179598.856000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 66
[17179600.748000] apm: BIOS not found.
[17179600.864000] [fglrx] total      GART = 134217728
[17179600.864000] [fglrx] free       GART = 118226944
[17179600.864000] [fglrx] max single GART = 118226944
[17179600.864000] [fglrx] total      LFB  = 127889408
[17179600.864000] [fglrx] free       LFB  = 119697408
[17179600.864000] [fglrx] max single LFB  = 119697408
[17179600.864000] [fglrx] total      Inv  = 0
[17179600.864000] [fglrx] free       Inv  = 0
[17179600.864000] [fglrx] max single Inv  = 0
[17179600.864000] [fglrx] total      TIM  = 0
[17179602.512000] eth0: no IPv6 routers present
[17179604.864000] ttyS1: LSR safety check engaged!
[17179606.812000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179608.048000] Bluetooth: Core ver 2.8
[17179608.048000] NET: Registered protocol family 31
[17179608.048000] Bluetooth: HCI device and connection manager initialized
[17179608.048000] Bluetooth: HCI socket layer initialized
[17179608.084000] Bluetooth: L2CAP ver 2.8
[17179608.084000] Bluetooth: L2CAP socket layer initialized
[17179608.112000] Bluetooth: RFCOMM socket layer initialized
[17179608.112000] Bluetooth: RFCOMM TTY layer initialized
[17179608.112000] Bluetooth: RFCOMM ver 1.7
[17181004.596000] APIC error on CPU0: 00(40)
[17181367.424000] APIC error on CPU0: 40(40)
[17181511.744000] APIC error on CPU0: 40(40)
[17182840.252000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17182840.312000] input: AT Translated Set 2 keyboard as /class/input/input3
[17182853.920000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17183413.656000] APIC error on CPU0: 40(40)
[17183731.400000] APIC error on CPU0: 40(40)
[17184147.976000] APIC error on CPU0: 40(40)
[17184737.700000] APIC error on CPU0: 40(40)
[17185214.916000] APIC error on CPU0: 40(40)
[17187318.976000] APIC error on CPU0: 40(40)



fglrxinfo output follows

> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6011 (8.28.8 ) 

---

### Post by play0r on 2007-01-10
you could try adding the following kernel option to your /boot/grub/menu.lst

```
acpi=noirq
```

dunno if that'll work, but you may as well try it. :-# 
could need a bios update (very unlikely, but i thought i'd throw it out there) or if you can track it down to a specific module, you could blacklist it.

ez,
play0r

---

### Post by xpan on 2007-01-10
> **play0r said:**
> you could try adding the following kernel option to your /boot/grub/menu.lst

```
acpi=noirq
```

dunno if that'll work, but you may as well try it. :-# 
could need a bios update (very unlikely, but i thought i'd throw it out there) or if you can track it down to a specific module, you could blacklist it.

ez,
play0r

will try to modify the menu.lst file and report back.

The problem is that it doesn't happen always, but most of the times. It rarely happens when I start ubuntu in recovery mode. Does this mean anything to you?

I just had a Bios update few days ago (jumped from v1.12 to v1.20 Phoenix Bios)

---

### Post by xpan on 2007-01-11
adding acpi=noirq in the boot options, resulted in a no-boot situation where I could hear the short drum roll sound of the login screen but couldn't see anything (black screen).

Please tell me if there is any way I could track down the problem (it might not be the APIC errors) so I can blacklist the module. 

I also noticed that while in recovery mode I don't see the APIC errors and the machine shuts down normally... why is that?

---

### Post by hollerith on 2007-01-11
I've got the same problem except I'm on a different distro (gentoo).  What else we do have in common is fglrx and probably loads of ATI hardware - Radion Mobility X200?  AMD Sempron +3100.  APIC error on CPU(0) 40 (40) - 60 is cpu specific allegedly.  I have seen acpi=noapic except that I would be VERY careful following advice about power management options - you don't really want to fry your board - bet that acpi=noirq was a bit scary too.  I don't know if these acpi tables persist after reboot in gentoo or ubuntu for that matter.  When I do append="apm=on acpi=off" my machine goes a lot faster, even though it is an ACPI capable board.  I haven't installed any tools to watch frequency scaling and the like, just doing cat /proc/whatever for now.  I'm considering a switch to ubuntu but can't seem to find out whether Xgl works out-of-the-box from ubuntu CD.

---

### Post by jasin on 2007-01-12
Seems like you're not the only one with acpi problems, the forums here are plagued with posts about acpi problems. There are work arounds for nearly every acpi problem, but their just that, work arounds.

I guess we need to post more of our acpi problems on launchpad.net in hopes the developers at ubuntu will get off their lazy asses and fix acpi.

---

### Post by gh0st on 2007-01-13
> **jasin said:**
> Seems like you're not the only one with acpi problems, the forums here are plagued with posts about acpi problems. There are work arounds for nearly every acpi problem, but their just that, work arounds.

I guess we need to post more of our acpi problems on launchpad.net in hopes the developers at ubuntu will get off their lazy asses and fix acpi.

I think you've got ACPI confused with APIC, they aren't the same thing. ACPI is to do with power management and you do see a lot about it on the forums, I haven't seen much about APIC on here though.

I also seem to have an APIC error, I get a msg when I boot that says "Kernel Panic: sync error APIC failed. Try booting with noapic option or running apic=debug" I don't know what this means and I haven't seen an error like this before. Does anyone have any ideas? It just started doing this the last couple of days.

---

