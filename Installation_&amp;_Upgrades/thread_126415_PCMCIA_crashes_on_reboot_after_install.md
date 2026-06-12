---
title: "PCMCIA crashes on reboot after install"
date: 2006-02-06
forum: Installation &amp; Upgrades
---

### Post by UK31337 on 2006-02-06
Hi, I'm having a problem with Breezy Badger on my laptop (Fujitsu Siemens Amilo M3438G).

It installs fine, the CD ejects, and it reboots.  The problem is, when it restarts and goes into the final installation procedure, it gets as far as pcmcia-*something* (too fast to read), and it crashes - I see a grey screen with black text, some kind of debug output, not sure what it is or what it means.  

The machine locks up, and I have to do a hard reboot.  But when I hold down the power button, it says the usual Sending TERM signal etc, so that's fine.

To get the machine to boot at all, I have to hold down Alt-SysRq-E to kill the hotplug subsystem at boot up (if I don't, the whole system hangs).  It then advances into the final installation phase.  Does this skipping the hotplug business have anything to do with my problem?

Hope you guys can help, I have no idea.

---

