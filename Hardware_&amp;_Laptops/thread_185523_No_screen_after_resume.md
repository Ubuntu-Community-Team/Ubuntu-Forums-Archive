---
title: "No screen after resume"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by Davor281 on 2006-05-31
Hello!

The screen is in grey color after resume from suspend to RAM.

Everything elese works, I can even bring up terminal and type a restart command, power button also works, function keys also, I just can't see anything.

I remember having same experience in Breezy under Gnome, but when I enabled the screensaver, the problem was gone.

I am running Dapper 6.06RC with Kubuntu and have tried various settings in /etc/default/acpi-support with no results.

The lapotop is Prestigio Nobile 151 (AOpen 1556) with intel graphics.

Any ideas?

ENjoY!

Davor.

---

### Post by OPaul on 2006-06-01
I had a similar issue with Breezy. I disabled DPMS to resolve my problem, maybe try that.

---

### Post by Davor281 on 2006-06-01
:confused: :confused: :confused: 

Tried every possible solution, even installed Ubuntu instead of Kubuntu, still nothing.
Strange is, that resume was working in Breezy.

Seems something had to be changed in kernel, Xorg or i810 drivers.

AGAIN!

Everything works, I can type, switch between consoles, special function keys also work. Backlight is ON, I just can't see my desktop, everything is bright grey.

Any ideas ???

EnjoY!

Davor.

---

### Post by Davor281 on 2006-06-01
More info ...

Found out that Xorg has problems finding saved state for i810.

Also if VBESTATE is enabled, resume script can't find the vbestate in /var/lib/acpi-support where it should be???

If pci state is enabled, there are no errors from resume.sh, but Xorg has same problems and reports 
> (WW) I810(0): Setting the original video mode instead of restoring
        the saved state

Any ideas now?

ENjoY!

Davor.

---

