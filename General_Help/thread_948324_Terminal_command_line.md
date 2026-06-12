---
title: "Terminal command line"
date: 2008-10-15
forum: General Help
---

### Post by Linuxidiot on 2008-10-15
Hiya, ive been trying everything ive know to do in the past and i just cant get it. My problem is im trying to run wine installer.exe in a directory that my terminal cannot find.I placed a file by right clicking on the desktop and used create folder option.Then proceeded to download the the newer world of warcraft cd into it(took about an hour), opened up my terminal and used the change directory command to try and find it to run the wine installer on but it just keeps popping up with no such file or directory response....please help ive been at this for about a day now:confused:

---

### Post by SunnyRabbiera on 2008-10-15
well did you try to just simply double clicking the installer?

---

### Post by Linuxidiot on 2008-10-15
yea i get nothing, im soo stumped...theres even a rightclick option that lets you browse what program to open with. but i get nothing from that either:(

---

### Post by _sAm_ on 2008-10-15
Open Nautilus and go to the place you stored the *.exe file. Drag the *.exe file to a terminal. You will now see the full path to  the *.exe file. Use your left key to navigate to the beginning and type in cd and make a space then hit enter.

---

### Post by Linuxidiot on 2008-10-15
thats great, worked like a charm!

---

### Post by _sAm_ on 2008-10-15
> **Linuxidiot said:**
> thats great, worked like a charm!

If you want to "go" to a place in the terminal where the name has space you need to use "" between. Like this:
cd "/home/linuxidiot/Desktop/world of warcraft"

If you try this you will get an error: 
cd /home/linuxidiot/Desktop/world of warcraft

Learn more here: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

