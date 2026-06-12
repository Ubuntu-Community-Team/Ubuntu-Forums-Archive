---
title: "[SOLVED] i/o error with Kingston SD Card"
date: 2008-07-05
forum: Hardware
---

### Post by stiansoftcore on 2008-07-05
I get an i/o error when trying to create a new folder to my Kingston SD Card. What is this? What do I type in the console to give you the output?

Thanks.

---

### Post by sayakb on 2008-07-05
At a terminal:
```
gksudo nautilus
```
CAREFUL: This executes Nautilus as root with r/w access permissions to all system files.

Using the root nautilus window, try to copy the files to the SD Card.

---

### Post by stiansoftcore on 2008-07-05
Already tried that, forgot to tell =/ And it won't open in xp either. It did before, but not anymore. I've also tried formatting in xp, no luck. In gparted, it said "unknown disk label", but I'll try one more time.

Thanks for the reply :)

EDIT: I got to format it, but when creating a new folder, naming it "mfe", it says that a folder is alrleady called "mfe".

EDIT #2: Formatting doesen't work. It says that it's formatted in Gparted, but when i access it, it's not empty =/
EDIT #3: It worked with windows :S Don't know what it was, but I've tried formatting it to FAT16 in Hardy with no luck. In xp, took me 1.5 seconds to do it (if you count the 3 min boot time out). Should I report this as a bug maybe?

---

