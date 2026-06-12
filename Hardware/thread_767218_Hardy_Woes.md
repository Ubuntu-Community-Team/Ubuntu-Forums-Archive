---
title: "Hardy Woes"
date: 2008-04-25
forum: Hardware
---

### Post by bodgetastic on 2008-04-25
Hi all,

I've not had much luck with recent Ubuntu releases!  My main PC is an Athlon 64, with an NForce3 mobo,a Geforce 7600GT gfx card and mostly using onboard peripherals (soundcard, net, etc.).  I'm still running Edgy which I installed ages ago!

I tried Gutsy a while back but it kept crashing when I tried to load the LiveCD.  I've downloaded Hardy and it seems to be doing the same kinda thing.

Specifically:
I boot up the LiveCD and press CTRL-ALT-F1 to see the daemons loading.  Everything loads OK and it fires up X, at which point one of my two displays switches itself off, the other stays on but blank, and the system locks (no numlock/capslock/scroll-lock activity when I press the buttons).  Also no CTRL-ALT-DEL.

Rebooting, I edited the commandline for Grub to show the entire boot and disable APIC (I think - sorry I keep getting confused between APIC and ACPI!).
Boot took a little longer, and hung when trying to load the Bluetooth daemon (I don't have bluetooth installed btw.)  Pressing CTRL-ALT-F2 to get to a prompt and manually killing the initscript allowed boot to progress and Gnome came up.

Unfortunately, it wouldn't recognise my network.  Manually loading forcedeth didn't work, ifconfig shows the eth0 interface as existing but down.  Manually setting the interface to DHCP showed repeated 'sendto: Network is Down' errors.

I haven't tested any other hardware, but noticed when booting again with ACPI enabled and boot splash disabled (hence crashing on X load) that it had detected my multimedia drive, which I hadn't noticed before.

Anybody got any clues?  It's a Foxconn mobo but I don't have the exact model number to hand.  I'm currently running 64-bit but the LiveCD is 32-bit.

Thanks everyone in advance

---

### Post by bodgetastic on 2008-04-26
Had some progress!

Remembered that I'd had some issues with powernowd before, so I booted the LiveCD to single-user by customising the Grub prompt.

Then I simply deleted the two powernow scripts from /etc/init.d, and ran telinit 5 - success, and working network!

Still had some issues when I tried to install the proprietory nvidia driver to see if Compiz would work correctly, the xconfig wasn't written properly and I got dumped out to a terminal, and when I tried manually loading it couldn't load the nvidia.ko module.  I'm hoping this will go away if I install it.  Not going to install till I get a coupla new hard drives which are in the post, so I can kill off my partitions and install anew.  Thinking of using Reiser4 if I can get hold of it...

---

