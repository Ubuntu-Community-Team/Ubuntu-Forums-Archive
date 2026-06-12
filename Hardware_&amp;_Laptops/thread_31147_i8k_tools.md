---
title: "i8k tools"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by aleahey on 2005-05-02
when i run sudo modprobe i8k force=1 i can get all the temperature/fan crap to work in gkrellm, but as soon as i reboot the module is gone and ive gotta redo it. anyway to automate this process?

---

### Post by ivoks on 2005-05-02
[QUOTE=aleahey]when i run sudo modprobe i8k force=1 i can get all the temperature/fan crap to work in gkrellm, but as soon as i reboot the module is gone and ive gotta redo it. anyway to automate this process?[/QUOTE]

In /etc/modules put the line:

i8k force=1

---

### Post by aleahey on 2005-05-02
[QUOTE=ivoks]In /etc/modules put the line:

i8k force=1[/QUOTE]

ahh thanks man =]

pardon my stupidity

---

### Post by nacnud on 2005-05-05
Sorry for my ignorance, but how do you actually run the i8kutils utilities once installed?

---

### Post by moon2js on 2005-05-13
Me too. I can't seem to find any good documentation on i8kutils and how to use it.

---

### Post by Determinist on 2005-05-17
You'll need some GUI tool to display information from the I8K monitor (which the command above helped make active).

SideCandy Dell I8K plotter is a desklet you can use to display the information I8Kmon puts in "/proc/i8k". You'll need gdesklets tho.

Deter.

---

### Post by 0okami on 2006-08-10
subscribing to this msg. ^_^

---

### Post by jethomp3 on 2006-10-10
type "info i8kctl"
type q to exit the help

this works for all commands, you can also try "man i8kctl" or "help i8kctl"

---

