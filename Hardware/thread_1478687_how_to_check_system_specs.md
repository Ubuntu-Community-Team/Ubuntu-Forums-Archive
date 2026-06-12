---
title: "how to check system specs?"
date: 2010-05-10
forum: Hardware
---

### Post by princeofnam on 2010-05-10
i'd like to access more detailed information about my laptops specs including its CPU, RAM, GPU, etc.  do i have to install additional programs?

---

### Post by princeofnam on 2010-05-10
mostly i'd like to see detailed information about my graphics card

---

### Post by em3raldxiii on 2010-05-10
First up, you can click System > Administration > System Monitor

In there, there is a SYSTEM tab that has some of the info you are looking for.  As far as the gfx card goes, I can't remember precisely just now ... gimme a minute to remember rofl.

---

### Post by Dayofswords on 2010-05-10
theres hardinfo, its pretty sweet
```
sudo apt-get install hardinfo
```

---

### Post by em3raldxiii on 2010-05-10
Rofl I just checked out hardinfo myself.  It's awesome!!

Once you install it, if you can't find a link in your apps menu, you can just hit ALT-F2 and type in *hardinfo* and it should fire up a neat little program for you.

---

### Post by bluegene on 2010-05-10
Actually, if you want the command line, there are various to enumerate hardware information.

To list brief summary of hardware:
```
sudo lshw -short
```
For PCI devices including Graphics card:
```
lspci -v
```

HTH,
jongbergs

---

### Post by prshah on 2010-05-10
> **princeofnam said:**
> i'd like to access more detailed information about my laptops specs including its CPU, RAM, GPU, etc.  do i have to install additional programs?

System-Preferences-Hardware Information

---

