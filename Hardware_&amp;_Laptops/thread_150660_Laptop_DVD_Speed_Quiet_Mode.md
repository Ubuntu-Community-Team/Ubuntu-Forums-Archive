---
title: "Laptop DVD Speed: Quiet Mode?"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by MiniJames on 2006-03-26
Along time ago before replacing Windows XP Pro with a Dapper Ubuntu daily build, I remember a software DVD drive feature that would reduce the spin speed of the disk and therefore the amount of noise / vibrations generated without any noticable decline in performance.

Whilst playing a DVD this morning, the distracting noise coming from the DVD drive spoilt what otherwise would be a great film.

Any ideas / suggestions on this? Thanks in advance.

---

### Post by wakady on 2007-03-28
same problem here

---

### Post by El_Matthews on 2007-11-19
Gents

with 7.04 it worked like this;

You can reduce the speed of IDE CD-ROM drives with hdparm or a program called setcd. It works like this:

    hdparm -E [speed] [cdrom device]

    setcd -x [speed] [cdrom device]

You can also try

    echo current_speed:4 > /proc/ide/[cdrom device]/settings

but you will need root privileges.

for 7.10 I have to have a look because I don't find /proc/ide anymore but the command to set the speed still works.

Greetings

Matthews

---

### Post by atlas95 on 2007-11-19
Hello,
I search how to do a switcher for cd speed...could you help me?
For create a launcher which switch between 2 speed of more.

---

