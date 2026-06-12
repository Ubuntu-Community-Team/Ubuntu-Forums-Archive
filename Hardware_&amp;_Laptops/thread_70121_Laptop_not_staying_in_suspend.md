---
title: "Laptop not staying in suspend"
date: 2005-09-28
forum: Hardware &amp; Laptops
---

### Post by droric on 2005-09-28
Hello, I have my Ubuntu 5.04 laptop setup to suspend via S3_Bios, but the laptop seems to suspend okay.  But the problem is as soon as the laptop sleeps it resumes immediatly after suspend. Any ideas?

---

### Post by warpforge on 2005-09-29
Does the first suspend after boot work and not subsequent ones? That's what happened to me. Anyway, it's not happening in Breezy for me anymore.

---

### Post by droric on 2005-09-29
Every suspend, reguardless of order results in the laptop waking up immediatly, btw is there a way I can try out breezy without loosing hoary?

---

### Post by Manny C on 2005-09-29
I have this problem when enabling "suspend after closing the laptop" in klaptop.

I have no problems with suspend to ram (ie. s3)  though.

Am using Breezy.

---

### Post by droric on 2005-09-29
My laptop is setup to use s3, at least i think so...
in /boot/grub/menu.lst i have # kopt=root=/dev/hda2 ro acpi_sleep=s3_bios resume=/dev/hda5 vga=0x318.  And at ACPI_SLEEP_MODE=mem in /etc/default/apic-default

---

### Post by pnunn on 2005-09-29
OK.. followed this and managed to get the notebook to suspend with the lid shut.. but how the hell do I get it to start again?

Tried all the buttons and nothing.. pressed the power button and it re-booted.

HELP...
:)

Peter.

---

