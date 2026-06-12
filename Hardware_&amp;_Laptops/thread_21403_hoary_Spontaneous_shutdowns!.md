---
title: "hoary: Spontaneous shutdowns!"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by hap0 on 2005-03-22
Just installed Hoary on an HP Pav. zd7140 widescreen, and it won't stay on more than five minutes past booting up. It just totally randomly shuts the power off.

---

### Post by alastair on 2005-03-22
Could be some sort of buggy ACPI e.g. sending spurious power events?

Try booting with ACPI off as a test - see if things improve e.g.

ESC at boot -> grub menu
select kernel line and "e" to edit
Add "acpi=off" at end of kernel line as an extra arg

Then boot ("b" to boot perhaps) - see if things act differently (note - you will perhaps miss battery status, fan control etc.).

---

### Post by hap0 on 2005-03-22
[QUOTE=alastair]Could be some sort of buggy ACPI e.g. sending spurious power events?

Try booting with ACPI off as a test - see if things improve e.g.

ESC at boot -> grub menu
select kernel line and "e" to edit
Add "acpi=off" at end of kernel line as an extra arg

Then boot ("b" to boot perhaps) - see if things act differently (note - you will perhaps miss battery status, fan control etc.).[/QUOTE]I'm sorry I should have mentioned that I tried this in a variety of ways. Although I haven't tried appending it to the end of the line, I've just tried inserting it after the 'ro' argument. I can't image it matters, but I will tried it again.

BUT, why I've not had to do this with Gentoo, Yoper, or *Mepis is quite the mystery. I'm simply testing distro's, and so far this is one heck of a show stopper from the point of this review so far.

---

### Post by alastair on 2005-03-22
OK - I'm sorry you are having problems. It is worth trying the various options on the kernel line - acpi,apic,lapic etc. Just in case. Check the logs and make sure the arg has the desired effect (e.g. acpi IS off etc.). Turn off as much as possible. What if you don't use X? etc.

The other thing you have to do is see if anything's printed in the syslog ofcourse. Any indication of theproblem when the shutdown occurs? Any pattern?

If all else fails, see if a later kernel helps. Or acpi update. Or roll your own kernel. Plus patch perhaps with newer acpi latest source.

But I understand - at the end of everything, you need to achieve something e.g. work. So, unless you have the time and energy to chase this, use a distro that works for you.

---

### Post by Nano on 2005-03-24
[QUOTE=alastair]OK - I'm sorry you are having problems. It is worth trying the various options on the kernel line - acpi,apic,lapic etc. Just in case. Check the logs and make sure the arg has the desired effect (e.g. acpi IS off etc.). Turn off as much as possible. What if you don't use X? etc.

The other thing you have to do is see if anything's printed in the syslog ofcourse. Any indication of theproblem when the shutdown occurs? Any pattern?

If all else fails, see if a later kernel helps. Or acpi update. Or roll your own kernel. Plus patch perhaps with newer acpi latest source.

But I understand - at the end of everything, you need to achieve something e.g. work. So, unless you have the time and energy to chase this, use a distro that works for you.[/QUOTE]
 It only happens to me playing Enemy Territory :S

---

### Post by sabione on 2005-04-01
I had the exact same problem on my zd7000 with Hoary Ubuntu and then Kubuntu was the same. It would just shutdown on its own very soon after logging on to kde. I tried backing down to the CLI and the same happened. I checked the logs but couldn't find anything. So, I was thinking about what it could be and it dawned on me that it happens soon after I enter my password in either kdm or CLI. I use the shift key in my password but I don't know if that's the one. I .old'ed the powerbtn.sh in /etc/acpi and also acpid, acpi-support, apmd, and powernowd in /etc/init.d. I should have disabled them one at a time but I was in a hurry. I did this with a live cd of MEPIS. I am going to reenable them one by one and see where the problem is coming from but I am almost positive that it is the powerbtn.sh script interpreting the shift (or one of my other password characters - sorry nice try;) as the power button. It seems as if it sees the button press and sits on it for a little while, then shuts down the puter.

Its been up for about 9 hrs and no probs installing software and updates...tweaking!

regards,
sabione

---

