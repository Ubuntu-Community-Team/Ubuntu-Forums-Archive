---
title: "Touchpad: strange behaviour"
date: 2008-09-25
forum: Hardware
---

### Post by 10o on 2008-09-25
From time to time (at random) the touchpad of my **Acer Aspire 5310** starts acting very jumpy. On itself it moves around the place and even clicks here and there, often with unexpected/unwanted results. Just now it shut down the system, sometimes a folder is created on the desktop, sometimes unwanted menus are opened.

Of course this makes the laptop hard(l)y usable. So I hope someone here can help me out. On the Dutch forum I've had no results so far. The hint I got there was to enable every checkbox in the Touchpad settings. So I did, but the problem keeps coming back now and then.

The other thing is that vertical scrolling functionality (using the button underneath the touchpad) is turned around. Up scrolls down and vice versa. With this issue I could live though... ;-)

---

### Post by purct on 2009-01-09
> **10o said:**
> From time to time (at random) the touchpad of my **Acer Aspire 5310** starts acting very jumpy. On itself it moves around the place and even clicks here and there, often with unexpected/unwanted results. Just now it shut down the system, sometimes a folder is created on the desktop, sometimes unwanted menus are opened.

Of course this makes the laptop hard(l)y usable. So I hope someone here can help me out. On the Dutch forum I've had no results so far. The hint I got there was to enable every checkbox in the Touchpad settings. So I did, but the problem keeps coming back now and then.

The other thing is that vertical scrolling functionality (using the button underneath the touchpad) is turned around. Up scrolls down and vice versa. With this issue I could live though... ;-)

I have the same issue, however I noticed that if I switch on my laptop and what for selftest to finish(before the ubuntu boots up) press control+alt+delete (laptop reboots) and then my Touchpad works fine.....so I guess its a problem with BIOS rather than ubuntu.

Hope this helps!

---

### Post by 10o on 2009-01-19
> **purct said:**
> I have the same issue, however I noticed that if I switch on my laptop and what for selftest to finish(before the ubuntu boots up) press control+alt+delete (laptop reboots) and then my Touchpad works fine.....so I guess its a problem with BIOS rather than ubuntu.
Hope this helps!
Thanks, it helps! When the touchpad behaves badly, I restart the system, press ctrl-alt-del when Bios is starting up and wait for the system to boot up once again. The problem then does not seem to occur. The Bios version is V1.50 by the way. It´s a bit of a hassle, but it works...

---

### Post by 10o on 2009-01-28
I have set a longer pause for the GRUB, so I have time to reboot there. When I start Ubuntu from the GRUB after this reboot the touchpad always works fine.

When I go for it first time, 90% of the time it doesn't.

---

### Post by tpurch on 2009-02-11
I was able to fix this by editing my /boot/grub/menu.lst entry for my installation by tagging i8042.reset i8042.nomux to the end of the kernel entry. 

My main boot entry in my menu.lst file now looks like this:

title linux
kernel (hd0,0)/vmlinuz BOOT_IMAGE=linux root=/dev/sda1 acpi=on splash=silent vga=788 i8042.reset i8042.nomux
initrd (hd0,0)/initrd.img

---

### Post by 10o on 2009-02-11
I've tested it a few times now and it works every time. Beautiful. Thanks very much!

---

