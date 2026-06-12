---
title: "Wake on USB problems- Zotac IONITX-A-C"
date: 2011-06-24
forum: Hardware
---

### Post by Parrallax on 2011-06-24
Hi guys,

I'm having problems with waking on USB. The system runs ubuntu 11.04 off a USB drive. It's designed to be a media center computer.

When I suspend it with all the USB devices disabled in /proc/acpi/wakeup then it suspends correctly and wakes up fine when I press the power button. However if I enable ANY of the USB devices in /proc/acpi/wakeup it suspends and then wakes up straight away.

Here is all the lines not commented out in my /etc/default/grub:
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1 acpi_enforce_resources=lax"
GRUB_CMDLINE_LINUX=" vga=792 splash quiet"

So I've tried the usbcore.autosuspend=-1 and acpi_enforce_resources=lax changes that I've read recommended on [http://wiki.xbmc.org/?title=Enable_Wake-On-Device]("http://wiki.xbmc.org/?title=Enable_Wake-On-Device"). That didn't work.

I've read on another site [http://www.minimyth.org/forum/viewtopic.php?f=6&t=2524]("http://www.minimyth.org/forum/viewtopic.php?f=6&t=2524") that disabling USB2.0 support worked on a Zotac IONITX-B-E. I can't find anywhere within my BIOS however an option to turn off USB2.0. Of course I'm also loath to disable 2.0 support anyway because the operating system runs from USB.

Please guys, If anyone has any ideas on how to help me I'd appreciate it a lot. I've looked around for answers, but nothing I change makes any difference. Is the fact I'm running the OS from USB mucking me up?

Thanks

---

### Post by Parrallax on 2011-06-26
Hi again guys,

I hate to bump my own thread, but I really need a hand here. Any ideas what's causing this problem?

Could it be the fact that I'm running my OS from USB? Would the problem go away if I got a small SATA drive instead? I'd be happy to do that if it fixed the problem, but of course I'm a bit reluctant to go ahead and spend the money on no more than a guess.

---

