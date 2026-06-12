---
title: "PCI-Express interrupt woes"
date: 2009-04-28
forum: Hardware
---

### Post by AMESSIER on 2009-04-28
I'm having trouble getting interrupts to work with my PCI-express device. The PCI-express device is a custom FPGA, but known to work under windows etc. In other words, there may be something funny with the hardware, but I don't really think there should be. I'm running Ubuntu 8.04 on a pretty new Dell Precision Laptop

MY first attempt was to use MSI interrupts since they seem to be enabled on this device (at least as far as a can tell be peering into the config registers using "lspci". Here's some code from my char driver (under probe):

--- code snippets from my driver ------------------------------------------
 pci_enable_device(dev);
 pci_enable_msi(dev);
 status = request_irq(dev->irq, swcr_interrupt, 0 , "swcr_pci", NULL);
---------------------------------------------------------------------------

When I run this I do get a message popup in /var/log/messages:

--- /var/log/massages -----------------------------------------------------
 ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 19 (level, low) -> IRQ 17
---------------------------------------------------------------------------

However, once I enable MSI the IRQ changes from 17 to 218 (in this case). here's a snippet from "lspci -vvv" for my device:

--- "lspci -vvv" snippet ---------------------------------------------------------------
	Interrupt: pin A routed to IRQ 218
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
		Address: 00000000fee0300c  Data: 414a
----------------------------------------------------------------------------------------

This seems to tell me that indeed the device has been given an MSI vector and it has been given an IRQ of 218, which can be confirmed by looking at /proc/interrupts

--- clip from /proc/interrupts --------------------------------------------
218:          0          0   PCI-MSI-edge      swcr_pci
---------------------------------------------------------------------------

Things look promising, however when I expect my device to interrupt I don't see them. The "ERR:" count in /proc/interrupts increments each time though. This tells me my device is doing something, but perhaps the MSI message is not correct, or perhaps the APIC is not configured properly? 

Anyway, my next step was to try INTx emulation mode. To do this I simple removed the "pci_enable_msi" call in my driver. (I reboot often to clear out the hardware etc.) Now /proc/interrupts looks like this:

---------------------------------------------------------------------------
17:          1          1   IO-APIC-fasteoi   swcr_pci
---------------------------------------------------------------------------

I'm a little ignorant when it comes to figuring out where it was decided that IRQ17 should be used. In fact, on my system IRQ17 is normally used by a firewire card and when I load my driver there is a conflict (which I can tell by error reporting from my driver). At this point I bootup, rmmod the firewire device and then insmod my device. Every time I boot it seems to want IRQ17. At any rate, in this mode when I expect an interrupt things go crazy. The interrupt count in /proc/interrupts just keeps running (like I have a level triggered interrupt that is stuck high).

--- clip from /proc/interrupts -----------------------------------
17:     486927     486968   IO-APIC-fasteoi   swcr_pci
------------------------------------------------------------------

One thing I tried was to play around with the arguments passed to "request_irq" in my driver. For example I tried: "IRQF_TRIGGER_RISING", but got this in /var/log/messages:

----/var/log/massages ---------------------------------------------
ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 19 (level, low) -> IRQ 17
Apr 28 16:27:10 swcr-laptop1 kernel: [   57.521481] No IRQF_TRIGGER set_type function for IRQ 17 (IO-APIC)
------------------------------------------------------------------

I guess this is telling me I can't change the trigger type for IRQ17? I tried hard-coding the IRQ to a free one that seems to be "IO-APIC-edge", like IRQ5 and IRQ7. No luck, I didn't see the interrupt at all, not even an "ERR:" in /proc/interrupts. 

Well, that's where I am now. If you're still with me here I really appreciate you giving some consideration to my problem. I'm not sure where to go from here. It seems that when I was in the state where I got interrupts like crazy I was really close, I just needed a way to tell the APIC to use edge-triggered interrupts on IRQ17. If there is something special about IRQ17 I guess I really should be able to switch, but like I said this didn't work either. Hmmm...

---

