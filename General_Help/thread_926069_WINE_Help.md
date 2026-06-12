---
title: "WINE Help"
date: 2008-09-21
forum: General Help
---

### Post by Sly-.- on 2008-09-21
Hey everyone. Someone told me about WINE some time ago, thought I'd try it out now. I just installed it, could someone run past me how I can use it to use Windows applications on Ubuntu?

Hope someone could run it past me, this would really mean I wouldn't have to use Windows again. :D

---

### Post by kokkus on 2008-09-21
It's very simple. Wine lets your windows installed programs run in ubuntu but you don't have to use wine. 
In the applications menu you will see a Wine menu. There you'll see the program files list, a launcher to the c driver directory where all the installed windows programs will be placed in. And an uninstall program for the windows programs to be removed.
Sometimes the uninstall program won't let you delete the program, so then you can use this code in terminal: 
nautilus ~/.local/share/applications/wine

The c drive folder for wine is located under your home directory/.wine/c_drive.

OH, and here's a list over some of the most stabile programs Wine can run.
[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=distribution&iId=527&sAction=view&sTitle=View+Distribution](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=distribution&iId=527&sAction=view&sTitle=View+Distribution)

Hope this helps you:)

---

### Post by MetalFanLiam on 2008-09-21
Use it through terminal or Nautilus.

Through terminal, cd to the directory where the .exe (or .msi) is located, and use the command wine to execute it.

EG for app.exe in MY home directory: 

cd /home/liam
wine app.exe

Or through nautilus, if you right click the .exe, it should say "Open with WINE Windows Emulator" and this will open the .exe file.

You should configure WINE before use, using the "winecfg" command in terminal.

Liam

---

### Post by Bukarts on 2008-09-21
Does windows programs work as fast in wine as fast they run in win??

---

### Post by kokkus on 2008-09-21
Most of the programs will run faster, but some programs are not that sabile with Wine. THe link I gave you contains stabile programs only.
Everything uses much less memory and CPU with ubuntu because of the way things works here.

---

### Post by Sly-.- on 2008-09-22
If I go to Browse C:\, I have a Windows and Program Files folder. I have the usual files inside the Windows folder, by nothing inside the Program Files folder. So if I can't see the Windows applications, how am I meant to use them?

---

### Post by howefield on 2008-09-22
> **Sly-.- said:**
> If I go to Browse C:\, I have a Windows and Program Files folder. I have the usual files inside the Windows folder, by nothing inside the Program Files folder. So if I can't see the Windows applications, how am I meant to use them?

I don't run many windows applications in wine, only one really. To install I just double click the exe file and it installs a program launcher in Applications > Wine > Programs

---

### Post by Sly-.- on 2008-09-22
Thats what I mean, there are none of my Windows application executables when I look inside Program Files.

---

