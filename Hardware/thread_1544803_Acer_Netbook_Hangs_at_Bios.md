---
title: "Acer Netbook Hangs at Bios"
date: 2010-08-03
forum: Hardware
---

### Post by Pqqu on 2010-08-03
Acer Aspire One
Dual boot Windows 7 and Ubuntu 10.04 (lucid) (netbook remix)
Kernel Linux 2.6.32-21-generic
GNOME 3.30.0
991.9 MiB of memory
Processor 1 and 2: Intel(R) Atom(TM) CPU N450  @ 1.66 Ghz 

Besides a few hiccups (mouse freaking out in ubuntu, hibernating not working in windows), I've had a very easy time with the dual-booted solution until recently. I left it on for a day and a half on the Windows 7 partition, syncing music from an external HDD to an mp3 player, and then shut down. When I tried to turn it back on, the computer started the Acer bios and got ready to open grub, paused, and returned to the Acer screen, ad infinitum. I read that this might have something to do with the usb settings in the bios, but for the life of me I couldn't find an option to change it.

Today I inserted an Ubuntu 10.04 USB stick and booted it fine, although a few things were strange. The startup screen for the disk drive was far more pixelated than usual, a "Ubuntu 10.04" text box over 4 flashing periods, not that pretty vector graphic. In addition, after a while ([72.~] and [90.~] the few times I tried it) this would print:

>> acer-[something] unable to detect available WMID devices

To be quickly replaced by the normal "Try or Install" window. Upon clicking try:

>> speech-dispatcher configured for user sessionsle WMID devices

And then it goes to the desktop fine. What on earth is going on here? Any help at all would be appreciated.

---

### Post by Pqqu on 2010-08-09
In a way, I fixed the problem. I made a little extra space and installed a clean Ubuntu install, imported some settings, and rebooted. That new install appears at the top of the list of grub when I don't even use it, but...at least grub shows up.

---

