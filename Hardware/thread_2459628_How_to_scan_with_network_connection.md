---
title: "How to scan with network connection"
date: 2021-03-22
forum: Hardware
---

### Post by acefromspace on 2021-03-22
Using Ubuntu 20.04 and have HP all in one (HP officejet pro 8020) connected through network cable. Printer works just fine but don't know how to scan. I was told that Ubuntu 20.04 comes with hplip (although I don't know if this is even used for printing through a network connection) Do I need to use this to scan? Do I need to install other software (like the GUI, ect)? In settings, it shows the printer but I don't see anything about scanner.

---

### Post by ajgreeny on 2021-03-22
I assume you have either ***document-scanner*** or ***xsane*** installed in Ubuntu-20.04 but I don't know which one.
Open up either of those two applications and it should find the scanner and allow you to use it.

If you wish to change any settings easily and quickly in the scans you make I suggest xsane is the better, though more complicated of the two apps with all settings showing in the main window; you can make changes in simple-scan but they are rather more hidden from the user in the Preferences dialogue (see my screenshot)

---

### Post by brian_p on 2021-03-23
You are very likely experiencing a bug in SANE, but it is easy to get you scanning. Let's check first. Give the output of ```
scanimage -L
```

---

