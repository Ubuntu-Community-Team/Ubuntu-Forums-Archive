---
title: "How to view hardware list"
date: 2010-03-06
forum: Hardware
---

### Post by raunhar on 2010-03-06
I am using Ubuntu 9.10 on my laptop.
Till two days ago, it was showing my Modem (inbuilt one Motorola ML3081) in the Hardware Driver list.
But it vanished from there.
In windows, we can view the hardware list in th Systems, but is there any such facilty in Ubuntu.

---

### Post by MelDJ on 2010-03-06
in terminal type 
```
lspci
```

---

### Post by jocko on 2010-03-06
Or, to get a nicely formatted html file with all your hardware:
```
sudo lshw -html > ~/Desktop/[COLOR=Blue]filename[/COLOR].html
```
Then open the file (a file named[COLOR=Blue] filename[/COLOR].html on your desktop) in firefox.

---

