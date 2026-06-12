---
title: "acpi unable to turn cooling device off"
date: 2008-04-29
forum: Hardware
---

### Post by glennric on 2008-04-29
I have looked around the forums and can not find a solution to this problem.  There have been bugs posted about it, but there has to be a temporary workaround.  

The output of dmesg is line after line of
```
[  123.658547] ACPI: Transitioning device [FAN1] to D3
[  123.658550] ACPI: Unable to turn cooling device [dd8fb2b8] 'off'
```
and it is happening so often (several times a second) that it slows the whole system down, and sometimes even stalls the system for several minutes.  It usually quits after a few minutes, but then starts up again later.

This problem occurred the first time with feisty (I think), but went away with gutsy.  Now it is back with hardy.  When it happened with feisty I compiled my own kernel without the acpi fan module, and the problem went away.  I tried that now, but the problem persists.  

The computer is an celeron (pentium 4 variety) with an intel video card.

Does anyone know of a temporary work around, at least until the devs fix this?  Perhaps using the /proc/acpi stuff?

---

