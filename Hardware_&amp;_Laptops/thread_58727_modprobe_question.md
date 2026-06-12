---
title: "modprobe question"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by unkemptwolf on 2005-08-21
Alright, I can get my TV Tuner working in Fedora Core 3 by adding the following lines to my modprobe.conf
[B]
alias char-major-81 saa7134
options saa7134 card=42 qss=0[/B]

How do I go about doing this in Hoary? Thanks in advance! (and sorry if this is a dumb question)

---

### Post by stepper on 2005-08-21
Create conf file saa7134 this way
```

sudo gedit /etc/modprobe.d/saa7134

```
and copy the followin into this file
> 
alias char-major-81 saa7134
options saa7134 card=42 qss=0

To load it when your system boots include it in the list of loaded modules by append the list of modules with saa7134
```

sudo gedit /etc/modules

```

> 
mousedev
psmouse
............
ide-core
........
saa7134


---

