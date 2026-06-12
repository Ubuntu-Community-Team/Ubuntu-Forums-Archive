---
title: "suspend still broken"
date: 2008-08-23
forum: General Help
---

### Post by Adahn on 2008-08-23
Running hardy A64, 2.6.24.21.23   ATI cats 8.6 via Envy NG, dual core A64 on nforce 550 chipset, ATI 3850 gpu

suspend log:
Sat Aug 16 12:58:55 EDT 2008: running suspend hooks.
===== Sat Aug 16 12:58:55 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Sat Aug 16 12:58:55 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Sat Aug 16 12:58:55 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Sat Aug 16 12:58:55 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Sat Aug 16 12:58:55 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Sat Aug 16 12:58:55 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Sat Aug 16 12:58:55 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Sat Aug 16 12:58:57 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Sat Aug 16 12:58:57 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/95anacron =====
===== Sat Aug 16 12:58:57 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Sat Aug 16 12:58:57 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Sat Aug 16 12:58:57 EDT 2008: done running suspend hooks.


Swap is on, set to roughly 2x ram.

Suspend and hibernate both end with a blinking cursor on a black screen.  USB mouse turns off and cpu/case fans stay on.

I may be upgrading to an Intel cpu/chipset rig in the near future.  Is there any hope in that fixing it, or is the ATI card at fault?

---

### Post by Adahn on 2008-08-23
went to this site and made the following changes; still no joy.
[http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/](http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/)

: sudo gedit /etc/default/acpi-support and ensure the following:

    ACPI_SLEEP=true

    ACPI_HIBERNATE=true

    SAVE_VBE_STATE=false

    POST_VIDEO=false

    SAVE_VIDEO_PCI_STATE=true

---

### Post by Adahn on 2008-08-23
also:

sudo gedit /etc/modprobe.d/blacklist on a terminal)

blacklist intel_agp
blacklist agpgart

---

### Post by carolinason on 2008-08-23
make sure the acpi deamon is running and is enabled in the bios. 

also see this
[http://forums.hexus.net/operating-systems-applications/143871-foxconn-linux.html](http://forums.hexus.net/operating-systems-applications/143871-foxconn-linux.html)

---

### Post by Adahn on 2008-08-23
also made these changes to acpi-support from this site:
[http://www.lunders-and.no/wp/?p=99](http://www.lunders-and.no/wp/?p=99)

DOUBLE_CONSOLE_SWITCH=true
MODULES_WHITELIST="fglrx"

no joy.


acpi is on in bios.  I'm running a biostar mobo.
how do I confirm the daemon is running?


edit: suspend has worked on this mobo before, back when I had an nvidia card and in Edgy IIRC (stopped even with that card around Feisty or Gutsy).

also: compiz on/off, no difference

---

### Post by Adahn on 2008-09-01
Is it likely that suspend may work with the 32 bit versions of Hardy/ATI drivers?

---

### Post by Adahn on 2008-09-13
update:
I reverted to 32bit Hardy.
Suspend is still broken using regular, ubuntu restricted, or envyng versions of ATI drivers.

---

