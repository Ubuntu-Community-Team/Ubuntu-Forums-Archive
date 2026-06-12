---
title: "Fujitsu Siemens Amilo A1650G"
date: 2006-01-11
forum: Hardware &amp; Laptops
---

### Post by targz on 2006-01-11
I have an Amilo A1650G laptop. My problem is the wireless network card (Atheros chipset). The result of lspci is:
"0000:02:05.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)".
Could anyone help me to install this cad. Thank you in advance.

---

### Post by wickwire on 2006-02-11
I've got the exact same problem.

I'm using a Fujitsu Siemens Amilo L3710, 16:9 screen, I ran a SUSE live dvd and it detected the atheros chip properly, but I'd like to use Ubuntu instead. I'll keep searching, will post anything here if I find it.


EDIT:

Tried a lot of things, still stuck. I'm trying to avoid compiling sources because I'd rather have binary packages installed, better yet, through apt-get/Synaptic, tried solving things alternating between the "linux-restricted-modules" package and the "madwifi-restricted-module" package. Using both at the same time generated lots of errors from dmesg output.

Using either package, I managed to run the "ath_pci" module, and then when running dmesg, I got an IRQ related error... I checked to see if my laptop was controlling IRQs from the BIOS and not the OS (suggested somewhere on the web), there are no options to choose from. I also tried booting with "acpi=off". None of these solved the issue.

So, I got as far as modprobing the ath_pci module and getting an IRQ error. The ath* device will not be created, so I'm stuck.

this guy --> [http://rik.no-ip.com/~rik/?q=node/10]("http://rik.no-ip.com/~rik/?q=node/10") has the same atheros chip as we do, same lspci message and managed to get it to work. So apparently it is possible to do it.

---

### Post by wickwire on 2006-02-13
Ok, managed to get it working.

In your case, even though it shows as unknown device (as does here), try the linux-restricted-modules package for the kernel you have installed (search in Synaptic, it should be installed by default), then run

sudo ath_pci

and then run "dmesg" and check to see what happened with ath_pci.

My specific error was the one [on this thread]("http://ubuntuforums.org/showthread.php?t=128816"), I figured it out - good luck.

---

