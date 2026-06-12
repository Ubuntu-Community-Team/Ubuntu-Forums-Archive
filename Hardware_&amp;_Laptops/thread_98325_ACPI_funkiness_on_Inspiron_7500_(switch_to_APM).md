---
title: "ACPI funkiness on Inspiron 7500 (switch to APM?)"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by rootneg1 on 2005-12-03
I used to have Debian on this laptop and it worked great with APM (never got ACPI working).  I decided to give Ubuntu a shot, and now power management is fsck'd:

Fn-Esc no longer initiates a suspend-to-disk; this is REALLY lame.

Whenever I close (and reopen) the lid, acpid continuously respawns lid.sh caused a serious resource drain; this is mildly annoying.

Is there a quick and dirty way to switch ubuntu to APM rather than ACPI?  It would be nice to have the extra features of ACPI if anybody knows what the problem might be, but really all I want is my suspend-to-disk working again...

for those interested it's a Dell Inspiron 7500 model no. PPI

---

### Post by amohanty on 2005-12-03
Warning: never been tried.

Fire up BUM
System->Administration->Boot Up Manager

uncheck acpid
check apmd

HTH
AM

---

### Post by quietglow on 2005-12-03
As I understand it, the 2.6 APM really sucks...I don't know if this is because there is a decreasing interest in it or what. If you google, you'll see LOTS of complaints about it. If I were going to run APM, I believe I'd regress to 2.4.

What the lid does is controlled by the "/etc/acpi/events/lidbtn" script. You can modify it to point to whatever script you like in /ect/acpi/ (sleep, hibernate etc)

Most laptops which understand acpi need to be careful on APM cause of the fan controls etc. You've run this one with APM before so perhaps that isn't an issue.

---

