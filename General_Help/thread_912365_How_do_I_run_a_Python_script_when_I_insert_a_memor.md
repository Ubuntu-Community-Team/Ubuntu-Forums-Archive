---
title: "How do I run a Python script when I insert a memory card?"
date: 2008-09-06
forum: General Help
---

### Post by thetejon on 2008-09-06
Currently, when I insert a camera memory card into my USB reader, F-Spot opens and offers to import my photos.  What I'd really like to do is run a Python script to copy the RAW files and convert them to JPG.  The script isn't the problem.  What I need to know is how to associate the script with the insertion of the memory card.  I haven't been able to find any sort of explanation on how to adjust the "autorun" behavior.

Any help would be appreciated.

---

### Post by ryanhaigh on 2008-09-07
There are two possible solutions to this. The first is to adjust the program used to open any camera device, this can be done from System>Preferences>Removable drives and media > Camera tab. Change the program used to point to your script.

The second option is for if you want to use the script only for this particular device. For that you can use udev rules. [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

