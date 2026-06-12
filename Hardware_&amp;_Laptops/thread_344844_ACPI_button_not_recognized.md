---
title: "ACPI button not recognized"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by abrahamsmith on 2007-01-23
My fujitsu laptop does not seem to register ACPI button events.    
It's running an up-to-date Edgy amd64 kubuntu install.

Here are the symptoms:

0) System logs and acpi_listen register **nothing** when the power button is pressed or the lid is closed.  Yes, /etc/init.d/acpid is running.

1) On boot, dmesg indicates that ACPI is detected and active. It **does** see the power and lib buttons when the button module is loaded.  (I'll post dmesg tonight if you don't believe me.)

2) Other ACPI modules (e.g., processor, thermal, ac, battery) seem to be okay, as detected by  kpowersave, et cetera, though I haven't looked for acpid response.

3) I **know** that the button and lid should work, as this machine was successfully responding to them for a 1.5 years, running Gentoo.


Any ideas? 

I'm stuck, since the kernel seems to say "Hey, I see a button!", but acpid never hears anything.

---

