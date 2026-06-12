---
title: "Wine virtual desktop launcher"
date: 2008-09-07
forum: General Help
---

### Post by rossjman1 on 2008-09-07
I am trying to get one of my Windows games to run in windowed mode, but there is no window mode option. If I set Wine to emulate virtual desktop then the game will run the way I want it. However, I do not want to enable/disable virtual desktop everytime I run the game. Is there a way I can achieve this using a shell script or a command line option (man wine didn't seem to have any arguments for this)?

---

### Post by evildragon2 on 2008-09-07
Go to Wine cfg and go to the Applications tab.Click add application then choose the .exe file.You can set special settings so that it only affects the game

---

### Post by rossjman1 on 2008-09-07
I will only let me change what version of Windows to mimic.

---

### Post by rossjman1 on 2008-09-08
bump

---

### Post by rossjman1 on 2008-09-10
bump

---

### Post by Aspras on 2008-11-14
In winecfg, you can see theres a tab caled Applications, you will notice "Default Settings" is selected. All the settings you have set will affect all aplications because you have that selected. If you add a new application in that list , then select it you will see it now has different settings which you can change and that will only affect the application selected in that list.

---

### Post by ncanna1 on 2008-11-14
You could also create a custom application launcher (on one of your toolbars) to run a command from the command line.  

As for flags, I think that to run something windowed, adding --windowed -height size -width size should work, substituting 'size' with the desired sizes, respectively.  I don't recall if it's exactly --windowed or --window or -windowed or -window, so maybe someone else can clarify.  

To actually run the program, you're going to need "wine program.exe", where program.exe is the exectuable for whatever you're trying to run.

---

