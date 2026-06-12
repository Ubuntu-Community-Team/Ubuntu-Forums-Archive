---
title: "Freeze on startup: ata timeout, /sbin/modprobe abnormal exit"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by keflavich on 2007-01-26
I've been running Edgy for about a week on my Compaq V6000 with no serious problems up until today.  

Problem:
Ubuntu freezes on load (both in regular and recovery mode) for kernel version 2.6.17-10.  Putting the load into verbose with F2 gives me this output (using the regular kernel):

(sometimes it gives this, sometimes not) udevd-event[3065]: run_program: '/sbin/modprobe' abnormal exit

[17179978.156000] ata1: command 0xc8 timeout, stat 0x50 host_stat 0x4
irq 7: nobody cared (try booting with the "irqpoll" option)
handlers:
[<f8904830>] (usb_hcd_irq+0x0/0x60 [usbcore])
Disabling IRQ 7

(there's more of the [#####.###] stuff, which I assume is just time stamping)

When I use recovery mode, the final output is:
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (0000:00)
ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
(sometimes this line too) PCI: Ignoring BAR0-3 of IDE controller 0000:00:0d.0

The "magic SysRq" keys do nothing, and while I apparently can switch consoles with ctrl-alt-fn, they're all dead, as I figure I should expect.

I know the hard drive itself is fine; it's a dual boot system and FC6 boots alright and can access anything.  

Before the freeze, I installed a few things, include Sun's JRE.  Somewhere in that installation, Firefox and other web browsers started crashing whenever I loaded a page that wasn't pure html (i.e. gmail, java download page).  I successfully installed ndiswrapper, and as far as I know alsamixer, both from source before the reboot.  I also installed a lot of other stuff from synaptic/apt-get, mostly fortran compilers and web browsers.

I'm new enough that I don't know what buttons I can press on startup to try to fix things/enter a different run level.  For example, assuming I got far enough, is there any way to start at runlevel 3 if the default is runlevel 5?

Also, all of my log files in /var/log end at 5:28 PM today, which is when I rebooted the computer.  None of the stuff I typed above showed up in the logs, which I accessed through FC6.

Thanks,
Adam

---

### Post by keflavich on 2007-01-27
Problem solved, at least in part.  I added "pci=noacpi" to the kernel line in GRUB (/boot/grub/menu.lst).  I'm still curious as to why I had to do this the, let's say, 15th time I booted up Ubuntu, as opposed to the first 14 times.  I already had the "noapic" option on, and I knew that was necessary from a previous linux install.

---

### Post by keflavich on 2007-01-28
New development: after restarting again, I got the same failure, but this time if I removed "noapic" and kept "pci=noacpi", it worked.  Clearly, I don't  understand what's going on, but I guess I'll go see if it's repeatable.

my current kernel line in grub:
**kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro pci=noacpi**
sometimes works, sometimes freezes at
** PCI: Ignoring BAR0-3 of IDE controller 0000:00:0d.0**
also, at
[b]ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=-1 pin1=-1 apic2=0 pin2=0
...trying to set up timer (IRQ0) through the 8259A ...
.....(found pin 0) ...works.
checking TSC synchronization across 2 CPUs:[\b]
but it usually gets past that, and instead gets stuck at
[b]ACPI: Assume root bridge [\_SB_.PCI0] bus is 0[\b]

So my crashes/recoveries are no longer repeatable.  Any ideas?


More info on kernel options for Edgy on the Compaq v6000:
**kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro **
I freeze at either:
**Kernel panic: Attempted to kill the idle task!**
or, after some ACPI functions,
** PCI: Ignoring BAR0-3 of IDE controller 0000:00:0d.0**

I get more errors with noapic:
**kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro noapic**
gives:
**run_program: '/sbin/modprobe' abnormal exit**
ALSA switches to polling mode
ata1 command timeout....
(i.e. old error repeats itself)

**kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro pci=noacpi noapic**
dies at
[b]ACPI: Assume root bridge [\_SB_.PCI0] bus is 0[\b]

---

### Post by ofir_k on 2007-01-28
Hey, I also got the same message after installing some ALSA drivers...

I will try your solution just for backing up files and then I will format the disc and install it from the beginning.

---

### Post by ofir_k on 2007-01-28
Ok, so I simply booted from the kernel-generic listed in the GRUB menu and Ubuntu is fine again.

However, I still going to format the computer and install Ubuntu from the beginning because right now I have a lot of hardware problems (I upgraded the sound card and the graphic card...).

I really hope that everything will work fine in the end of this long long journey... :D

---

### Post by keflavich on 2007-02-01
Ubuntu still freezes on at least 50% of startups at the "TSC synchronization" point, but other than that works fine.  It's annoying and worrisome that I have to hard reboot on half of startups.  Can anyone help?

Thanks,
Adam

---

### Post by clayt0nk2 on 2007-02-02
I also have the exact same problem with  TSC synchronization on 6.1.0 edgy and a Compaq Presario 6110us

---

### Post by keflavich on 2007-02-12
Update:  I have better luck starting up the computer without any USB devices plugged in.  The startup crashes at " PCI: Ignoring BAR0-3 of IDE controller 0000:00:0d.0" seem to happen less often (maybe not at all, but I'm not sure of that yet) when I make sure my USB mouse not plugged in.  Hopefully that helps solve someone's problem.

Adam

---

