---
title: "ACPI events on Inspiron 1100"
date: 2006-07-15
forum: Hardware &amp; Laptops
---

### Post by sung_bae on 2006-07-15
Hi, I spared 3gig of hdd at my Dell inspiron 1100 and gave a test with dapper. Apart from X windows resolution problem, it almost worked out of the box, and this small problem was easy to fix by manually configuring xorg.conf
I even confirmed most ACPI stuffs worked out of box. Suspend with lid closing event, Fn+Esc key for suspend, hibernate etc, and a power buttn press brought the original status back. 

Now, I completely removed xp partition and reinstalled dapper in the entire hdd. But those ACPI stuffs are not working any longer.

Suspend, hibernate work when I click on those gnome icons, but shortkey and lid-close no longer have effects.

I'm sure it should work, but somehow the reinstallation might have omitted appropriate configuration? Where should I start?

Thanks,

---

### Post by sung_bae on 2006-07-16
It appears that Lid switch event is never recognised by the system.
/var/log/acpid shows nothing related to Lid event...

---

### Post by goehle on 2007-12-29
This is an old thread, but seeing as I had the same problem on my dell 1100 using Hardy I figured I would update it.  It seems that the Dell bios (or ubuntu) has some issued with the pci tables.  So, the key to fixing it is to make sure that the command "setpci -s 00:1f.0 bb.b=0a" is executed both on initial system startup as well as after a standby/hibernate resume.

For example you could use /etc/rc.local for initial startup and
a new file called /etc/acpi/resume.d/95-fix-dell-powerbtn.sh for resume.

This problem affects Dell Inspiron 1100, as well as Inspiron 5150 and 5160.

---

