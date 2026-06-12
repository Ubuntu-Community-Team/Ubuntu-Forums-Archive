---
title: "Blank screen after installing xen server"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by bharat.bvrit on 2008-12-21
hi,
  
i have installed **vmlinuz-2.6.24-22-xen**  xen kernel on the ubuntu 8.04 OS. Whenever i try to boot into xen, i 'm getting a blank screen and nothing else

For installing xen i have followed the tutorial on the link,
[http://www.howtoforge.com/high-performance-xen-on-ubuntu-8.04-amd64](http://www.howtoforge.com/high-performance-xen-on-ubuntu-8.04-amd64)

please help me out from this....

---

### Post by pspinler on 2009-02-18
No answer for you, sorry, but for what it's worth, I'm experiencing the same issue.  That is, booting into a Xen kernel, xwindows startup hangs.  Booting into a generic kernel, and all is good, I get gdm and X, can log in, and in fact, create this forum post. :-)

I've just now installed the ubuntu-xen-server on an up to date ubuntu 8.04 AMD x86_64:

pjs11@patslinux01:~$ dpkg-query --list | grep -i xen
(...trimmed for brevity...)

ii  libxen3                                    3.3.0-1ubuntu7~hardy1  
ii  linux-image-2.6.24-23-xen                  2.6.24-23.48
ii  linux-restricted-modules-2.6.24-23-xen     2.6.24.16-23.56
ii  linux-ubuntu-modules-2.6.24-23-xen         2.6.24-23.36
ii  python-xen-3.3                             3.3.0-1ubuntu7~hardy1
ii  xen-hypervisor-3.3                         3.3.0-1ubuntu7~hardy1 
ii  xen-utils-3.3                              3.3.0-1ubuntu7~hardy1

When I boot with Xen, I get to the point of gdm startup, whereupon the startup hangs,  (Fortunately, it's already started ssh by then, so I can log in)  My /var/log/gdm/:0.log reads thusly:

pjs11@patslinux01:~$ more /var/log/gdm/\:0.log.1 

(...snip copyright notices...)

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux patslinux01.mayo.edu 2.6.24-23-xen #1 SMP Mon Jan 26 03:09:12 UTC 2009 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 17 14:45:06 2009
(==) Using config file: "/etc/X11/xorg.conf"
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) Module "ramdac" already built-in
(WW) intel(0): Failed to set up write-combining range (0xd0000000,0x10000000)

And that's it, no more output.  I should note I see the same message "Failed to set up write-combining range (0xd0000000,0x10000000)" when booting into a generic kernal and getting a successful gdm and x session. 

And my machine hardware is a Dell Optiplex 755, with an Intel(R) Core(TM)2 Duo CPU and 8GB of ram.  lspci on this box looks like this:

pjs11@patslinux01:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
	Subsystem: Dell OptiPlex 755
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Dell OptiPlex 755
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fea00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec90 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at feb00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
	Subsystem: Dell OptiPlex 755
	Flags: bus master, fast devsel, latency 0
	Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
	Subsystem: Dell OptiPlex 755
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fedad000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Dell OptiPlex 755
	Flags: 66MHz, fast devsel, IRQ 18
	I/O ports at fe80 [size=8]
	I/O ports at fe90 [size=4]
	I/O ports at fea0 [size=8]
	I/O ports at feb0 [size=4]
	I/O ports at fef0 [size=16]
	Capabilities: <access denied>

00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02) (prog-if 02 [16550])
	Subsystem: Dell OptiPlex 755
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	I/O ports at ec98 [size=8]
	Memory at fe9da000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
	Subsystem: Dell OptiPlex 755
	Flags: bus master, fast devsel, latency 0, IRQ 509
	Memory at fe9e0000 (32-bit, non-prefetchable) [size=128K]
	Memory at fe9db000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ecc0 [size=32]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff20 [size=32]
	Capabilities: <access denied>

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff00 [size=32]
	Capabilities: <access denied>

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at fe9d9c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Optiplex 755
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fe9dc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: fe800000-fe8fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at ff80 [size=32]
	Capabilities: <access denied>

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff60 [size=32]
	Capabilities: <access denied>

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]
	Capabilities: <access denied>

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Optiplex 755
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe600000-fe7fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Unknown device 0211
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 510
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fec0 [size=32]
	Memory at ff970000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: Dell Optiplex 755
	Flags: medium devsel, IRQ 9
	Memory at fe9d9b00 (64-bit, non-prefetchable) [size=256]
	I/O ports at ece0 [size=32]

02:00.0 SCSI storage controller: LSI Logic / Symbios Logic 53c895 (rev 02)
	Subsystem: LSI Logic / Symbios Logic LSI8952U PCI to Ultra2 SCSI host adapter
	Flags: bus master, medium devsel, latency 72, IRQ 16
	I/O ports at dc00 [size=256]
	Memory at fe6fef00 (32-bit, non-prefetchable) [size=256]
	Memory at fe6ff000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at fe600000 [disabled] [size=128K]

Can anyone offer advice, please?

Thanks,
-- Pat

---

### Post by pspinler on 2009-02-26
Any hints?  Anyone?

Not hearing any answers, perhaps I'll go try KVM...

-- Pat

---

