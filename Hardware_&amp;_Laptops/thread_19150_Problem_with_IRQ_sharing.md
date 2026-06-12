---
title: "Problem with IRQ sharing"
date: 2005-03-10
forum: Hardware &amp; Laptops
---

### Post by tommie-lie on 2005-03-10
Hi,

I know there are plenty of posts out in the net about this problem, but nothing helped me, so I try it once again ;-)
I'm Using Ubuntu 5.04 daily from 7 March on a EP8KHA-Board (VIA KT266) with a Hercules Gamesurround Firtissimo II (CS46xx DSP).
After the installation, the network (DEC 21041) worked fine, but I had no sound. While booting, ALSA complained about not having found an appropriate soundcard. Then I found [this](http://www.ubuntuusers.de/viewtopic.php?t=2356) topic over at the German board (a rough translation: "Add snd-cs46xx to /etc/modules and everything will work"). I added the module and rebooted, but now, neither the network nor the soundcard is working. When the boot sequence comes to the point where it configures my network card, it says (excerpt from dmesg):
> irq 11: nobody cared (try booting with the "irqpoll" option.
 [<c012e40b>] __report_bad_irq+0x31/0x77
 [<c012e4de>] note_interrupt+0x75/0x9b
 [<c012dec2>] __do_IRQ+0xd3/0x111
*[... some other lines of the same kind ...]*
handlers:
[<e0a6f362>] (snd_cs46xx_interrupt+0x0/0x19e [snd_cs46xx])
Disabling IRQ #11
eth0: link up, media 10baseT auto
lspci says:
> 0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:0a.0 Ethernet controller: Digital Equipment Corporation DECchip 21041 [Tulip Pass 3] (rev 21)
0000:00:0c.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 18)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 18)
0000:00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 18)
0000:01:00.0 VGA compatible controller: STMicroelectronics STG4000 [3D Prophet Kyro Series] (rev 0f)

When I comment out the module in /etc/modules, the network is working again (but of course not the sound).
I'm pretty sure that the problem has something to do with the IRQ sharing between the network card and the soundcard, but I don't know how to resolve it.
The installer added "pci=noacpi" to the boot parameters, I already tried disabling ACPI in the BIOS, booting with noapic, nolapic, pci=irqbios, irqpoll and noirqdebug, but nothing solved the problem.

Any hints about this?

Bye
Thomas

---

### Post by tommie-lie on 2005-03-11
Today, I fiddled around with the kernel parameters and stumbled over a combination I must have missed yesterday.
When adding "pci=biosirq" and "irqpoll" to the kernel's parameter list (via grub's command line), both, the network and the sound works and both cards get an IRQ assigned (11 for both).
However, the problem has not gone away, as there is still the complaint about an unhandled IRQ.
Now, dmesg looks as follows:
> 
irq 11: nobody cared (try booting with the "irqpoll" option.
 [<c012e40b>] __report_bad_irq+0x31/0x77
 [<c012e4de>] note_interrupt+0x75/0x9b
 [<c012dec2>] __do_IRQ+0xd3/0x111
[...some more lines...]
handlers:
[<e0ab1362>] (snd_cs46xx_interrupt+0x0/0x19e [snd_cs46xx])
Disabling IRQ #11

But now the network works, I have no idea why.
When I get the message "Setting up network configuration" (or something like this), the network card is not activated immediately (the LED on the router does not blink) but some seconds later, i.e. when the booting process comes to the point where it tries to synchronize the clock with ntp.ubuntulinux.org.

So, the problem itself is still there, but I managed to work around it. But still I'd like to get a real solution, if anybody has one ;-)

---

### Post by alastair on 2005-03-11
This type of thing has been popping up on the kernel list for a while - every now and then. You might want to do some research and see what's said there e.g.

[http://marc.theaimsgroup.com/?l=linux-kernel](http://marc.theaimsgroup.com/?l=linux-kernel)

and do some searches (it isn't the best search interface though - perhaps google).

---

### Post by tommie-lie on 2005-03-13
[QUOTE=alastair]This type of thing has been popping up on the kernel list for a while - every now and then.[/quote]Yeah, I know and I'll keep playing with the parameters, but the ones I've tried so far did not resolve the problem. I thought there might be someone with the same machine who solved this already ;-)

---

### Post by tommie-lie on 2005-08-10
Finally, the problem was solved by a new kernel. Other than the two parameters mentioned above, I did not find any other working solution for neither the original Hoary kernel nor my custom kernel (built from some oldish Breezy sources, 2.6.12-3.something, I think).
However, today I updated to the current Breezy kernel (2.12.6-6.8) for some other reasons and it worked out of the box without any kernel parameters and without any IRQ issues in the kernel log.

---

