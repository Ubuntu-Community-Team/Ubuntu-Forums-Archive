---
title: "Poweroff after resume from sleep"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by caspian on 2005-04-27
I've just started using Ubuntu and I love it!

Suspend to RAM (echo 3 > /proc/acpi/sleep) works fine -- until after I played around with "powernowd" (I don't know whether powernowd was an unrelated coincidence), it suspended and resumed just fine. But for some reason, it now dies whenever it resumes from suspend. It resumes, then after a couple seconds, it powers off. Is there a way I can work around this?

I check in my kernel logs, and here's what it says when coming out of suspend:

> Warning: CPU frequency is 1600000, cpufreq assumed 600000 kHz.
ehci_hcd 0000:00:1d.7: USB 2.0 restarted, EHCI 1.00, driver 26 Oct 2004
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 11 (level, low) -> IRQ 11
eth0: Coming out of suspend...
ACPI: PCI interrupt 0000:02:05.0[A] -> GSI 11 (level, low) -> IRQ 11
Restarting tasks... done

It looks to me that the main problem is that the CPU freqnency is on the wrong setting. Is there something I can do to correct this? Or, is this related to a different problem?

Thanks.

---

### Post by caspian on 2005-04-28
Hmm... CPU frequency doesn't seem to be the problem. I tried suspending/resuming again and this time, the kernel logs don't say anything about CPU speed. Here's what I get:

> kernel: eth0: Going into suspend...
kernel: ehci_hcd 0000:00:1d.7: USB 2.0 restarted, EHCI 1.00, driver 26 Oct 2004
kernel: ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 11 (level, low) -> IRQ 11
kernel: ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 11 (level, low) -> IRQ 11
kernel: eth0: Coming out of suspend...
kernel: ACPI: PCI interrupt 0000:02:05.0[A] -> GSI 11 (level, low) -> IRQ 11
kernel: Restarting tasks...<6>usb 1-1: USB disconnect, address 3
kernel:  done
kernel: usb 1-1: new low speed USB device using uhci_hcd and address 4
kernel: input: USB HID v1.10 Mouse [Fellowes, Inc. Web Pro Optical] on usb-0000:00:1d.0-1
input.agent[7805]:      tsdev: already loaded
input.agent[7805]:      mousedev: already loaded
input.agent[7805]:      evdev: already loaded
input.agent[7805]:      evbug: blacklisted
usb.agent[7882]:      usbmouse: blacklisted
usb.agent[7882]:      usbhid: already loaded
input.agent[7936]:      evdev: already loaded
input.agent[7936]:      evbug: blacklisted
input.agent[7994]:      evdev: already loaded
input.agent[7994]:      evbug: blacklisted
input.agent[7972]:      evdev: already loaded
input.agent[7972]:      evbug: blacklisted
shutdown[8085]: shutting down for system halt
gconfd (caspian-7603): Received signal 15, shutting down cleanly
gconfd (caspian-7603): Exiting

It just seems to shut down without a reason... as it some app just sent the shutdown command! Is there something I need to configure to stop this?

---

### Post by jbrnd on 2005-05-02
[QUOTE=caspian]I've just started using Ubuntu and I love it!

But for some reason, it now dies whenever it resumes from suspend. It resumes, then after a couple seconds, it powers off. Is there a way I can work around this?
[/QUOTE]

What do you do to wake up your machine? If you press the power button, it could be that that triggers the shutdown sequence. If you type "cat /proc/acpi/wakeup" from a command prompt, that should in a somewhat cryptic way tell you what can trigger a wakeup. Type "sudo echo ABCD >/proc/acpi/wakeup" to toggle enabled/disabled status for event ABCD, where ABCD is one of the four-letter codes in the output from the cat command.

For instance, PBTN is a power button event and LAN0 is network activity.

---

### Post by florizs on 2006-03-02
I have the same problem with my amilo-pro M1425 laptop, I resume from suspend with the powerbutton and I belive it sends a shutdown signal at the same time.

how can I disable the feature to shutdown my laptop on the event of an acpi powerbutton event?

---

