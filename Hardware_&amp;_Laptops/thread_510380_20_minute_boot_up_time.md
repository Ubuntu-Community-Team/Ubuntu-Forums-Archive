---
title: "20 minute boot up time"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by harold mccants on 2007-07-26
It now takes my laptop about 20min to boot up.  Once it finally boots up it will work fine for about 10 min. then it freezes again.

---

### Post by hessiess on 2007-07-26
thats worse than my xp install![10 min to boot]
more info plz, system spec, os verson. will the live cd boot faster

---

### Post by Jamie Jackson on 2007-07-26
I'm no expert, but I've got  a few ideas, if nobody comes up with anything better:

1. Maybe your HD is full-ish? Try running "df" from the CLI.
2. Maybe your RAM is flaky? (Try running memtest from the Ubuntu CD's boot menu)
3. Maybe your HD is flaky?  (I don't know how to do this on a mounted drive, but you could run something like fsck from the live CD)

---

### Post by Austin_KW on 2007-07-27
In addition to checking the above resources, edit your grub options at boot (select and enter "e") and remove "splash" and "quiet". It may show where it is hanging/waiting.

Also install bootchart "sudo apt-get install bootchart" and reboot;
This will give you a graphical display of your boot process, look in  /var/log/bootchart/ for the .png file. You are then looking for somewhere that the cpu and disk usage is idle at the top of the chart. It is often very obvious where the delay is.

---

### Post by fredj on 2007-07-28
You can look in the system logs, System-Administation-System Log and see where the large delay is.

---

