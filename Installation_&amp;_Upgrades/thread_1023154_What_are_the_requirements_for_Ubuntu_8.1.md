---
title: "What are the requirements for Ubuntu 8.1"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by Numbat on 2008-12-27
Hi
  I have an old P3 machine I am attempting to load Ubuntu 8.1 on. It appears to load up but when it is finished, the display resolution is stuck on some low resolution and refuses to allow me to change it. Worse is that most of the screen is 'off-screen' meaning it is inaccessible. 

I was wondering if the computer has the minimum required for 8.1. I previously loaded version 7.04 on and although I had problems getting the modem to work, the screen was OK. All the cover on the new version says is it needs 256Mb memory and 4Gb of disk space. No mention of display requirements.

Any ideas?

---

### Post by Partyboi2 on 2008-12-27
What are your system specs including graphics card?

---

### Post by Numbat on 2008-12-27
> **Partyboi2 said:**
> What are your system specs including graphics card?
[http://supportapj.dell.com/support/edocs/systems/opgx100/en/ug/specs.htm#processor](http://supportapj.dell.com/support/edocs/systems/opgx100/en/ug/specs.htm#processor)

I was under the impression it was a Pentium but looks like a Celeron. Has 384Mb ram in it. I think it is 667MHz but could be wrong.

---

### Post by polmir on 2008-12-27
Type in terminal:```
lspci
```and post output.

---

### Post by Numbat on 2008-12-28
> **polmir said:**
> Type in terminal:```
lspci
```and post output.
Can't do it, I am afraid. Screen is uncontrollable.

I think I might try to reload the system and see if I can get some control.

---

### Post by Numbat on 2008-12-28
Well, I reloaded from scratch and no improvement. Screen is almost completely uncontrollable. I have a desktop and I can select sub-menus but a terminal just comes up as a blank. Same with any other sub-menu I open.

This is step backwards.

---

### Post by polmir on 2008-12-28
Ctrl+Alt+Fn

Fn = F1 or F2 or F3 or F4 or F5 or F6

Login and type:```
lspci>hardw.txt
```and post file hardw.txt

---

