---
title: "Error -110 :USB device using ehci_hcd not accepting address"
date: 2012-02-28
forum: Hardware
---

### Post by kaleidovision on 2012-02-28
Hello,

I'm very very new to ubuntu. I have a history of 1 successful install (ubuntu 11.10) on an old machine where everything worked right out of the box. That was a happy time.

Now I'm trying to get 11.10 working on my 'new' machine:

Acer Aspire M3641 (91d1r77tcp)
Intel Core 2 Quad Q6600 @ 2.4GHz
4GB DDR2 (2 x 2GB)
640GB SATA-300
GeForce 8600 GT (256MB DDR3)
2x Firewire 400
9x USB 2.0
LAN 1Gbps
D-Sub (VGA)
DVI-I
HDMI
Multi-cardreader

the only things attached to the USB are a logitech wireless desktop (keyboard & mouse) and a USB Belkin Wi-Fi dongle, both work under liveCD & during install of ubuntu 11.10, connection to internet was flawless.

To get to the install I had to change the bootoptions in grub (nomodeset, drmraid and something with acpi) or I would get stuck on a blank screen with blinking cursor.

After fixing that I installed Ubuntu 11.10 on the formatted ext4 HD (I let the install do this for me) and everything went fine up until the first reboot...

nothing happens, just a blank screen.

After searching a bit I found my way to grub and edited the 'quiet splash' into 'nomodeset'.

I get a little bit further, but it hangs during startup (initramfs) on the USB-ports, for every USB-port (9 in total) I get something like:
"new high speed USB device number X using ehci_hcd"
"device not accepting address X, error -110"

it goes through all of them fairly quick, but hangs on the last one... left the computer on for 10 minutes on that screen and nothing happened.

After searching for a solution some people suggested pulling the power cord and reconnecting it after 5 minutes, but this has no effect whatsoever for me (apart from the machine refusing to reboot at all after my 3rd attempt, but luckily it restarted a couple of tries later).

I don't know if it's helpful but I'll attach the boot-info.

Any help at all would be greatly appreciated,

Thanks in advance!

---

### Post by kaleidovision on 2012-03-01
SOLVED!

Had to change the option in the bios where it says: "Boot to OS: windows" to "others"
And now everything works fine!

Hope it's helpful to others as well

---

### Post by demkpap on 2012-12-13
My problem was that USB flash drive was mounted and unmounted in quick succession, and one of the messages in syslog was the above stated. This drove me crazy for a few days. Kaleidovision's idea made me search the Bios settings and in Integrated peripherals-> OnChipEHCI Controller I changed it from enabled to disabled. After that the USB mounted OK.

---

