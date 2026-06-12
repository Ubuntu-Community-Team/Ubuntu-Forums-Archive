---
title: "How can I determine the hardware I have with ubuntu?"
date: 2008-12-21
forum: Hardware
---

### Post by shalomhk on 2008-12-21
In Windows one was able to select "System Properties" and pull up a list detailing the make/model of each piece of hardware. How can I do this in linux?

---

### Post by empthollow on 2008-12-21
open synaptic and look for the program gnome-device-manager.   i think it shows in the menu but you can also run it by pressing ctrl + f2 and typing gnome-device-manager.   That is the closest thing i have found to the windows device manager.

---

### Post by computerjunkie on 2008-12-21
Go to applications >> system tools >> system monitor. that will give you information about certain types of hardware in your computer like your processor and amount of RAM. You may be able to manually check the directories in /proc  I could have sworn there was an app called "hardware browser". I can't find it on my Fedora machine now either but I know i've used something like that on linux before. Look through the applications menu for something like that but the above poster is right, gnome-device-manager will work.

---

### Post by zvacet on 2008-12-21
```
lshw
```

---

