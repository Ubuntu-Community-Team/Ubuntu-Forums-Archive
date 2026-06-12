---
title: "gdm works; gnome does not on fresh install to HP tx1000z"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by guttersnipe on 2007-07-29
I just installed a ubuntu 7.04 amd64 onto my new HP tx1000z laptop.  Unfortunatly, I am expierencing many problems.

Firstly, (just so I can boot into ubuntu without it freezing at the loading screen) I have to add "noacpi acpi=off" to the kernel line of grub.

After grub, I recieve this message at the bottom of the screen right before the ubuntu loading screen appears:
```
kernel alive
kernel direct mapping tables up to 100000000 @ 8000-d000
```
..no idea what that is, but the computer continues to boot until I get to gdm; gdm load beautifully.  I can move my mouse, type, and even login.  However, once I DO login gdm goes away and gnome does NOT load.  It sits forever at the plain "ubuntu orange" screen.  I can still move my mouse and all, but it's futile without a desktop manager loading.

So, I press ctrl+alt+f1 to see what the hell's going on in the terminal and I am given this:
```
Loading, please wait...
kinit: name_to_dev_t(/dev/sda5) = sda5(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot...

Ubuntu 7.04 guttersnipe tty1

trinity login: [  174.231128] bcm43xx: Error: Microcode "bcm43xx+microcode5.fw" not available or load failed.
[  298.964215] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```
also, the
```
kernel alive
kernel direct mapping tables up to 100000000 @ 8000-d000
```
...is still sitting at the bottom of the screen.

The ```
bcm43xx: Error: Microcode "bcm43xx+microcode5.fw" not available or load failed.
``` messages seem to spawn indefenitvly with a different number inside the [ ]'s every time.

I think the bcm43xx error has something to do with WIFI.  Frankly, getting gnome to load is much more important to me than WIFI, but for the sake of information, I did an dmesg | grep -i bcm43xx and found tons of errors:
```
[  186.764528] bcm43xx driver
[  186.771393] bcm43xx: Unsupported 80211 core revision 13
[  186.773652] bcm43xx: Invalid PHY Revision 9
[  194.576193] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  197.809115] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  221.042012] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  244.249670] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  269.051880] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  292.255133] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  315.462498] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  440.192837] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  563.324446] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  686.508056] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  809.638316] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```
the errors would run into infinity if I left my machine on long enough, but you get the general idea...

I went back to tty7 (ctrl+alt+f7), restarted X (ctrl+alt+backspace), and re-logged into gdm.  This time, I got a white square on the uppper left corner of the screen, but still no windows.  All I have is that white block ontop of the "ubuntu orange" screen.  Nothing else.  If I mouse over the white box, the mouse changes to a cursor (as if there were text inside the box).  Nothing happened after five minutes or so, so I went back to tty1, stopped gdm (/etc/init.d/gdm stop) and copied Xorg.0.log (see attached)

As I said, the most important thing to me is to get X with gnome working.
Any help will be appreciated.

---

### Post by guttersnipe on 2007-07-29
I did some more searching, and found [a thread on the fedora forums]("http://forums.fedoraforum.org/archive/index.php/t-154482.html") regarding the HP tx1000z.  Firstly, I noticed that the option I was using for my grub line was incorrect

> Firstly, (just so I can boot into ubuntu without it freezing at the loading screen) I have to add "noacpi acpi=off" to the kernel line of grub.

Instead of "noacpi" I was supposed to use "noapic".  Once I made that change, the computer booted to gdm and logged into gnome beautifully.

The thread listed above also suggested the use of the "irqpoll" option as well as the "noapic" option to the /boot/grub/menu.lst file.  I AM getting spat out irq errors while in the terminal, so I went ahead and did a:
```

$dmesg | grep -i irq
[   12.110975] spurious 8259A interrupt: IRQ7.
[   13.251894] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.252262] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
[   13.252622] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.252982] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.253343] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.253705] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.254066] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 *10 11 14 15)
[   13.254451] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.254814] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   13.255174] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 *11 14 15)
[   13.255534] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[   13.255895] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[   13.256257] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[   13.256618] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.256978] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.257342] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.257701] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.258073] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[   13.258458] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.289597] PCI: Using ACPI for IRQ routing
[   13.289601] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.289714] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   14.089248] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.091053] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   14.106338] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.106346] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.884948] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[   15.884951] PCI: setting IRQ 5 as level-triggered
[   15.884956] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[   15.885038] ata1: SATA max UDMA/133 cmd 0x00000000000130b0 ctl 0x00000000000130a6 bmdma 0x0000000000013090 irq 5
[   15.885068] ata2: SATA max UDMA/133 cmd 0x00000000000130a8 ctl 0x00000000000130a2 bmdma 0x0000000000013098 irq 5
[   16.692155] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[   16.692160] PCI: setting IRQ 7 as level-triggered
[   16.692164] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[   16.692520] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xc0005000
[   16.798259] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 11
[   16.798265] PCI: setting IRQ 11 as level-triggered
[   16.798269] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 11 (level, low) -> IRQ 11
[   17.316815] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[   17.316819] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[   17.316890] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xc0004000
[   17.476115] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   18.548419] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.275095] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 10
[   30.275099] PCI: setting IRQ 10 as level-triggered
[   30.275103] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 10 (level, low) -> IRQ 10
[   30.656292] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
[   30.656297] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
[  241.804758] irq 7: nobody cared (try booting with the "irqpoll" option)
[  241.804767]  <IRQ>  [<ffffffff802bd285>] __report_bad_irq+0x35/0x90
[  241.804826]  [<ffffffff88093465>] :usbcore:usb_hcd_irq+0x25/0x60
[  241.804836]  [<ffffffff802be243>] handle_level_irq+0xe3/0x140
[  241.804841]  [<ffffffff8026223c>] call_softirq+0x1c/0x28
[  241.804850]  [<ffffffff80270189>] do_IRQ+0x89/0x100
[  241.804908] [<ffffffff88093440>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  241.804923] Disabling IRQ #7

```

not quite sure what these errors mean, but I went ahead and followed the directions by adding the irqpoll option to the grub line and did another
```

#dmesg | grep -i irq
[    0.000000] Command line: root=UUID=1f041846-bd33-4411-9c4b-5f3af19c5b66 ro quiet splash noapic irqpoll
[    0.000000] Kernel command line: root=UUID=1f041846-bd33-4411-9c4b-5f3af19c5b66 ro quiet splash noapic irqpoll
[    0.000000] Misrouted IRQ fixup and polling support enabled
[   11.502102] spurious 8259A interrupt: IRQ7.
[   11.859101] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   11.859462] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
[   11.859818] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   11.860175] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   11.860530] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   11.860887] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   11.861243] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 *10 11 14 15)
[   11.861685] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   11.862045] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   11.862399] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 *11 14 15)
[   11.862754] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[   11.863108] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[   11.863463] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[   11.863817] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   11.864175] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   11.864536] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   11.864891] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   11.865258] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[   11.865683] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   11.896900] PCI: Using ACPI for IRQ routing
[   11.896903] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.897019] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   12.699833] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.701585] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   12.716909] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.716916] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.429987] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[   14.429990] PCI: setting IRQ 11 as level-triggered
[   14.429995] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[   14.430159] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xc0004000
[   14.622098] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[   14.622101] PCI: setting IRQ 5 as level-triggered
[   14.622106] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[   14.622186] ata1: SATA max UDMA/133 cmd 0x00000000000130b0 ctl 0x00000000000130a6 bmdma 0x0000000000013090 irq 5
[   14.622215] ata2: SATA max UDMA/133 cmd 0x00000000000130a8 ctl 0x00000000000130a2 bmdma 0x0000000000013098 irq 5
[   15.432057] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   16.506632] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   16.510239] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 11
[   16.510243] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 11 (level, low) -> IRQ 11
[   17.033879] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[   17.033883] PCI: setting IRQ 7 as level-triggered
[   17.033887] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[   17.033983] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xc0005000
[   33.775960] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 10
[   33.775964] PCI: setting IRQ 10 as level-triggered
[   33.775968] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 10 (level, low) -> IRQ 10
[   34.230959] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
[   34.230964] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10

```

All I know is that the latter produced less output, so I'm guessing it fixed something.  I'm following this guide blindly, and I'd prefer to know WHAT I'm doing and WHY it's working.  If anyone can provide the slightest bit of input, please do.  Thanks.

Now I've just got to tackle the network, 3d acceleration, sound, and the whole tablet-pc thing ;)

---

### Post by guttersnipe on 2007-07-29
Now that I got gnome up and running, I naturally grabbed my updates.  Now the laptop crashes during the ubuntu loading screen every time I boot up.  Further investigation lead me to discover that when ubuntu updated the kernel, it not only added it to the /boot/grub/menu.lst file, but it also OVERWROTE my "noapic irqpoll" options.

Is there anyway to make these options permanent such that a kernel upgrade will not delete them from the grub kernel line??

---

### Post by mangal on 2007-08-23
> **guttersnipe said:**
> Now that I got gnome up and running, I naturally grabbed my updates.  Now the laptop crashes during the ubuntu loading screen every time I boot up.  Further investigation lead me to discover that when ubuntu updated the kernel, it not only added it to the /boot/grub/menu.lst file, but it also OVERWROTE my "noapic irqpoll" options.

Is there anyway to make these options permanent such that a kernel upgrade will not delete them from the grub kernel line??

find the line like following in /boor/grub/menu.lst
# kopt=root=UUID=667a803a-3b2a-4315-b2f8-24a2f7b30a57 ro

add at the end noapic and irqpoll 

now try ubdate-grub the noapic and irqpoll options will come by default

for solving wireless problem i used latest ubuntu kernel 2.6.22-10-generic and restricted-modules-2.6.22-10-generic using gutsy distribution and i downloaded bcm43xx firmware at the following link
[http://www.maxxer.it/visite/phpmyvisites.php?url=http://www.maxxer.it/linux/bcm43xx_firmware_wl_apsta.tar.bz2&id=1&pagename=FILE:bcm43xx%20wl_apsta.o](http://www.maxxer.it/visite/phpmyvisites.php?url=http://www.maxxer.it/linux/bcm43xx_firmware_wl_apsta.tar.bz2&id=1&pagename=FILE:bcm43xx%20wl_apsta.o)
and extracted to /lib/firmware/<kernel-version>/ 

Now after the  reboot wireless is working fine.

---

### Post by kthxbai2u on 2008-01-20
For the record, when I had the problem with the white box in the top left, I immediatley tried "apt-get remove gnome" and it said the package wasn't installed. I believe it is possible that the update deselected the packages for some reason... When I did "apt-get install gnome" it did say "selecting previously deselected package ______" for gnome and all of its dependancies,  but I swear I didnt remove them.

Usually when I stumble accross a problem I just use apt-get to remove and reinstall the package containing the error. Sometimes that doesnt fix it though :-/

[EDIT] that didnt work either :-O I think this white box thing needs its own thread. This isnt the same problem as the one in that screenshot and it isn't getting enough exposure here hidden in a differently titled thread.[/EDIT]

---

