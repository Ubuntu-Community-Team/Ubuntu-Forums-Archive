---
title: "wubi installation problem?"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by rlawton91 on 2009-09-22
first off, I'm not by any means a linux user, however my school work requires Ubuntu (computer science major) and I'm having an issue when booting. I used Wubi to install.

At the boot menu when I choose Ubuntu, it begins to load and then opens up a busybox shell instead of the Ubuntu GUI. any ideas?

---

### Post by rlawton91 on 2009-09-23
bump for answer?

---

### Post by oboedad55 on 2009-09-23
> **rlawton91 said:**
> bump for answer?

I don't use wubi so can't help directly. Have you done a search of the forums? Congrats to your school for asking for an OS other than windows. Very unusual.

---

### Post by rlawton91 on 2009-09-23
> **oboedad55 said:**
> I don't use wubi so can't help directly. Have you done a search of the forums? Congrats to your school for asking for an OS other than windows. Very unusual.yes I have done a thorough search of the forums, nobody seems to have a problem such as this one that I could find. My school does require windows but I prefer to program within Ubuntu (professor recommended it to all students) so that I can print directly from emacs (cant print the code from a putty terminal)

---

### Post by rreese6 on 2009-09-23
Most likely a setting issue with your video( or might be another error)
From the prompt, type "dmesg | tail -n20" (no quotes) to see if there are errors with your video. 

You could try to start the GUI by typing in "startx" 
if that fails (which I suspect it will) paste the dmesg output here.
you can make a report file via the prompt my modifying the dmesg command
like this (again, no quotes in command) :

"dmesg |tail -n20 >> dmesg.txt" you will then have a file called dmesg.txt that you can post here

Let me know

---

### Post by rlawton91 on 2009-09-23
startx didnt do anything (startx not found)

after entering the dmesg |tail -n20 >> dmesg.txt  everything appeared to be fine, however I'm not sure where to look to find the text file. I used LS and saw that the file was there but I'm not sure how to read it from vista. If it is in fact a video error (I see a lot of these on the forums) it might help to know I'm running a 9600M GT 1GB card in my acer laptop.

---

### Post by oboedad55 on 2009-09-23
> **rlawton91 said:**
> yes I have done a thorough search of the forums, nobody seems to have a problem such as this one that I could find. My school does require windows but I prefer to program within Ubuntu (professor recommended it to all students) so that I can print directly from emacs (cant print the code from a putty terminal)

I did a tag search for "busybox" and came up with five pages of hits.

---

### Post by rreese6 on 2009-09-23
to see the file you can use "less dmesg.txt"
if that doesn't work, just typ in "dmesg | tail -n20" at the prompt and it will show up on your screen
Very interesting why startx x did not run. seems like you do not have a GUI type installation.
You might want to try to uninstall Ubuntu through windows and reinstall it paying close attention to the method of install.
you want to use xorg (that is the GUI Program(system)).
Like I said before I have never tried the wubi install.
Most people I know, do dual boot installations. they are less problematic.
If you decide to do a dual boot.google and read up on it for Vista.
also make sure you defrag your windows drive before doing a dual boot install.
The difference is that there will be a partition made for Windows and one made for Linux. when you install dual boot fashion it will ask you about the new partition size...that refers to the new size for windows partition. 
I have been googling and reading tons of stuff about your issue, however I am not finding much except that peopl stopped using the wubi install and did the dual-boot.
good luck

---

