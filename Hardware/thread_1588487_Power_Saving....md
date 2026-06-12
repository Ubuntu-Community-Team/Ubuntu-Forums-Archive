---
title: "Power Saving..."
date: 2010-10-05
forum: Hardware
---

### Post by v1ad on 2010-10-05
i have a laptop that has a i5 processor. and i swapped out the hard drive for a SSD. it was a power hog then and still is now.

i was wondering is there any tips that you can give me to save energy.

wifi idle, cpu throttle anything. i cleanup start up programs, just not sure why it eats so much cpu.

(btw with the SSD my bootup time is 7 seconds after bios :D with bios its 17 to login screen)

---

### Post by Axx83 on 2010-10-05
as always try this:

[http://ubuntuforums.org/showpost.php?p=8315253&postcount=1](http://ubuntuforums.org/showpost.php?p=8315253&postcount=1)

only the part that says USB AUTO SUSPEND

and report back the results

---

### Post by NightwishFan on 2010-10-05
Try using the package powertop. Every boot run powertop as root and press the corresponding keys to commit its suggestions. There are ways to make them permanent however I have no idea.
```
sudo powertop
```

---

### Post by mastablasta on 2010-10-05
With great power comes great energy consumption....
 
YOu have to trade off. if you want i5 porcessor you will need power. if you want less power conusmption i would suggest you got for celeron or atom next time...

---

### Post by NightwishFan on 2010-10-05
Yes, but most Intel CPUs have an Idle state. Trick is to write software that does things as fast as possible and become idle.

---

### Post by v1ad on 2010-10-05
Masta that i know, but i already have the processor. so i just wanted the processes to idle more.. or anything to idle more..

---

### Post by NightwishFan on 2010-10-05
Other than powertop, use a lighter desktop environment.

---

### Post by v1ad on 2010-10-05
got this from powertop, how to i this:

Enable the CONFIG_INOTIFY kernel configuration option.This option allows programs to wait for changes in files and directoriesinstead of having to poll for these changes

---

### Post by NightwishFan on 2010-10-05
You would need to compile a new kernel and enable that option. It is not required as that is just a suggestion from powertop.

---

### Post by cascade9 on 2010-10-05
Its not likely that your laptop BIOS supports this, but you could try underclocking and/or undervolting.

---

