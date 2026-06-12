---
title: "Disaster with 10.4"
date: 2011-04-03
forum: Hardware
---

### Post by hbrednek on 2011-04-03
Sigh --

I just installed Ubuntu 10.4 on my daughter's Dell netbook.  Everything that I expected could possibly go wrong went wrong.

Note, until I destroyed it with a new install of Ubuntu 10.4 (netbook), this netbook (a Dell mini) worked flawlessly with an Ubuntu 8.04 factory installation.

The problems:

1) No wireless access.

Of course not.  How foolish of me to expect that wireless would actually work! 

expected pointless Bot response: RTFM

Me - I DID!  It said to sudo apt-get install b43-fwcutter.  That went off without a hitch.  But nothing.  Then, I went into the hardware manager and enabled the driver.  NOTHING!

But I got this on looking at the end of dmesg:

[lots of stuff elided]

```
[    5.948324] phy0: Selected rate control algorithm 'minstrel'
[    5.950365] Registered led device: b43-phy0::tx
[    5.950420] Registered led device: b43-phy0::rx
[    5.950477] Registered led device: b43-phy0::radio
[    5.950651] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[    6.043463] [drm] initialized overlay support
[    6.113294] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[    6.292306] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[    6.298485] type=1505 audit(1301882066.098:5):  operation="profile_replace" pid=759 name="/sbin/dhclient3"
[    6.299926] type=1505 audit(1301882066.105:6):  operation="profile_replace" pid=759 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    6.300376] type=1505 audit(1301882066.106:7):  operation="profile_replace" pid=759 name="/usr/lib/connman/scripts/dhclient-script"
[    6.305456] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[    6.311201] type=1505 audit(1301882066.114:8):  operation="profile_load" pid=763 name="/usr/bin/evince"
[    6.319755] type=1505 audit(1301882066.122:9):  operation="profile_load" pid=763 name="/usr/bin/evince-previewer"
[    6.329159] type=1505 audit(1301882066.134:10):  operation="profile_load" pid=763 name="/usr/bin/evince-thumbnailer"
[    6.405768] type=1505 audit(1301882066.210:11):  operation="profile_load" pid=769 name="/usr/lib/cups/backend/cups-pdf"
[    6.406763] type=1505 audit(1301882066.210:12):  operation="profile_load" pid=769 name="/usr/sbin/cupsd"
[    6.413952] type=1505 audit(1301882066.218:13):  operation="profile_load" pid=770 name="/usr/sbin/tcpdump"
[    6.449823] fb0: inteldrmfb frame buffer device
[    6.449831] registered panic notifier
[    6.449851] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    6.449954]   alloc irq_desc for 22 on node -1
[    6.449962]   alloc kstat_irqs on node -1
[    6.449980] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.450067] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.456445] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[    6.465998] vga16fb: initializing
[    6.466012] vga16fb: mapped to 0xc00a0000
[    6.466024] vga16fb: not registering due to another framebuffer present
[    6.588622] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[    6.794396] Console: switching to colour frame buffer device 128x37
[    7.063894] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000
[    7.196225] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   12.237365] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   12.237383] b43-phy0: Controller RESET (DMA error) ...
[   12.452405] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   17.993313] b43-phy0: Controller restarted
[   17.993422] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   17.993438] b43-phy0: Controller RESET (DMA error) ...
[   18.208419] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10
```
The last four lines are repeated about 50 times.

2) The machine can no longer suspend

Ohfergawdsake!  A netbook is supposed to suspend!  And use wireless!  It's like the two most crucial items were the first two eliminated!

3) Password mania.  It now defaults to locking the screen after maybe a minute's inactivity and insisting on a password to unlock the screen!  Yes, I understand that in some circumstances leaving a netbook inactive for more than 30 seconds might well invite a security threat, but this (even if both the previous problems are addressed) makes it unusable for an 18 year old.

Any ideas?  After this experience I would gladly return to the previous (usable, if a bit out of date) configuration!

---

### Post by rvchari on 2011-04-03
instead of trying to find out what went wrong and solve the problem, can u just revert back to your more stable 8.04 ? if you can then you should re-check if all the hardware / software is working perfect.
after this you can use the apt-get dist-upgrade command from terminal and notice the upgrade of distro taking place.
i am no lilux geek but my logic says that when you go for upgrade, the files needed for your lappy will be held back and not erased...

your problem can be solved trying this option... i have upgraded from 9.04 to 10.04 and now 10.10 like this...
after i feel the stability, i download the iso to create a live cd.

---

### Post by Rasa1111 on 2011-04-04
Try a 10.10 CD and see if everything works from it first.
I had some wireless problems on a couple peoples laptops with 10.04.
10.10 I havent had any.

To stop it from locking when the screen blanks, and to change the length of time it takes to go blank, Just go into "screensaver" and "power manager"
You can get to power manager from within screensaver.

---

