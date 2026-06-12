---
title: "Enabling Nvidia drivers causes Ubuntu to start in safe mode"
date: 2008-05-02
forum: Hardware
---

### Post by byrd on 2008-05-02
All the pre-release builds of 8.04 installed the Nvidia drivers fine but after I installed the final version, enabled the drivers and reset, when Ubuntu starts the screen is all 'weird' and at the bottom there's a half cut off message of something along the lines of "Ubuntu is in safe-mode .."

I've re-installed it and it suffers the same problem.

Specs:

Intel Core 2 Duo E6750
Corsair 4GB DDR2 PC6400
BFG 8800 GT OC 512MB
500GB WD HDD SATAII 16MB Cache
Gigabyte P35-DS3P [Latest bios]

---

### Post by byrd on 2008-05-02
So.. ?

---

### Post by subzero316 on 2008-05-02
Get in the console mode{CTRL+ALT+F1)..and install the video diver properly.

---

### Post by byrd on 2008-05-02
How do I go about doing it 'properly'?

---

### Post by byrd on 2008-05-03
Woo, yeah, *awesome*. Suggestions for the seemingly broken drivers [for me]?

---

### Post by subzero316 on 2008-05-03
```

Press Ctrl+Alt+F1

sudo apt-get install envy
sudo envy -t



```


From there on youll get it.

---

