---
title: "programs to identify hardware?"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by pwright2 on 2006-12-15
In Windows there is a plethora of programs to indentify the hardware in your computer.  BelArc Advisor and SiSoft Sandra come trippingly to the tongue.  Is there anything in the Linux universe like that?

-----Paul-----

---

### Post by yabbadabbadont on 2006-12-15
Inside of a terminal, try running: "lspci -v"

You can also run "dmesg" to see what hardware was detected by the kernel during boot.  You'll want to run that shortly after booting though as the output only goes back so far and new log messages are added to it as time goes on.

---

### Post by hikaricore on 2006-12-15
Also if you need to see in  GUI interface what's installed in your system I suggest: [Sysinfo]("http://www.gnomefiles.org/app.php/Sysinfo") for gnome.  It's decent little tool that shows you information about your current hardware.  There's an rpm linked from gnomefiles.org that you can easily convert using alien to a deb file for easy installation.  :)

---

### Post by po0f on 2006-12-15
pwright2,

`lspci` and `lshw` are both console applications that you could use, though after your mention of SiSoft Sandra, I hardly think these are what you are after.  :)

Is there any information lacking in System->Administration->Device Manager that you are wanting to know?

---

### Post by Brian Smith on 2006-12-17
Sysinfo is also simply available for installation by opening System>>Administration>>Synaptic Package Manager

I've just installed it and it does provide me more and better information than System>>Administration>>Device Manager ever has for me.  Thanks H-core!

---

### Post by pwright2 on 2006-12-26
Sysinfo flashes a blank form up for a moment and disappears.  I have reinstalled with no improvement.  Any obvious error checking I can do?

-----Paul-----

---

