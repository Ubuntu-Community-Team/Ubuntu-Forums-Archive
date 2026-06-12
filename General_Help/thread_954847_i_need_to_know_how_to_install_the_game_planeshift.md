---
title: "i need to know how to install the game planeshift"
date: 2008-10-21
forum: General Help
---

### Post by bradpurvis on 2008-10-21
the file name is PlaneShift-v0.4.01-x86.bin and it is on my desktop

---

### Post by Elfy on 2008-10-21
In a terminal 

```
cd Desktop
chmod +x PlaneShift-v0.4.01-x86.bin
./PlaneShift-v0.4.01-x86.bin
```

If it needs root rights use sudo

---

### Post by bradpurvis on 2008-10-21
brad@brad-laptop:~$ cd Desktop
brad@brad-laptop:~/Desktop$ chmod +x PlaneShift-v0.4.01-x86.bin
chmod: cannot access `PlaneShift-v0.4.01-x86.bin': No such file or directory
brad@brad-laptop:~/Desktop$ ./PlaneShift-v0.4.01-x86.bin

---

### Post by bradpurvis on 2008-10-21
> **bradpurvis said:**
> brad@brad-laptop:~$ cd Desktop
brad@brad-laptop:~/Desktop$ chmod +x PlaneShift-v0.4.01-x86.bin
chmod: cannot access `PlaneShift-v0.4.01-x86.bin': No such file or directory
brad@brad-laptop:~/Desktop$ ./PlaneShift-v0.4.01-x86.bin

omg never mind some butt hole deleted it off my desktop. its over 300 MB

---

### Post by Elfy on 2008-10-21
check trash then - it'll only go completely with a shift+delete or rm in a terminal

---

### Post by bradpurvis on 2008-10-21
i downloaded a patch. it says i have to have admin privilages or something when i run it from the terminal. can you help? here is what it says

PlaneShift Updater Version 5 for linux32.

Checking for updates:
This program requires admin/root or write privileges to run. Please restart the program with these.
In windows, this means right clicking the Updater shortcut and selecting "Run as administrator".
For everyone else, login as the root user. If you don't have root access, contact someone who does and ask them nicely to run the updater!

Updater finished, press enter to exit.

---

### Post by Elfy on 2008-10-21
not sure how you run it - but whatever command you used try sudo in front of it

---

### Post by bradpurvis on 2008-10-21
there is no command i used i just double clicked the updater. the game will take me to the screen which i use to logon but i can't get any further until i update :(

---

### Post by Elfy on 2008-10-22
Try to change into the directory it is installed in and run 

```
./updater --auto
```

Also try and run the game from the command line append --help to see different options available. If it currently runs from a launcher - right click it to see the command which runs the game

---

### Post by ofirishere on 2008-10-26
> **forestpixie said:**
> In a terminal 

```
cd Desktop
chmod +x PlaneShift-v0.4.01-x86.bin
./PlaneShift-v0.4.01-x86.bin
```

If it needs root rights use sudo

Thank you very much, It was helpful and to the point

---

