---
title: "Notebook doesn't not wake up after suspend to ram (pm-suspend)"
date: 2012-09-28
forum: Hardware
---

### Post by Speransky on 2012-09-28
Hello to all!
What I have: HP Pavilion dv6 2055er and Ubuntu 12.04
What I do:
1) run "sudo pm-suspend" or click in the menu
2) system suspends to ram;
3) push any key to resume.
What I get: watching turning on leds(even WLAN-led turns on, that manipulates by ath9k kernel module), fan, HDD(only 2 moves). No monitor power on, no react to switching CapsLock, or NumLock, no react to power button, ctrl+alt+F1, crtl+alt+del and overs combinations and HDD stays quiet...

In /var/log/pm-suspend there is no log of waking up, only suspendig.

I've tryed to add to /etc/pm/config.d/modules different kernel modules to unload it before suspending:
firewire_ohci, sdhci_pci, video, zram, ath9k, vboxpci, vboxnetadp, vboxnetflt, vboxdrv, fglrx and usbhid in different combinations and got messages about success or not unloading these modules in log, but useless.

 I've installed uswsusp and tryed to use s2ram, but result is exactly similar. 

I've tryed to remove fglrx, but useless. 

I've tryed to install mainlain kernel, but no difference.

In Windows everything is ok. Also on ArchLinux I've saw this mode warkable.

Any help would be useful.
Regards, Dennis.

---

### Post by Alexithymia on 2012-09-30
I have the same problem, even under arch. How did you manage to fix it under arch?

---

### Post by Speransky on 2012-10-02
:) I forgot it, because it was long ago ) I think the problem is kernel ((

---

