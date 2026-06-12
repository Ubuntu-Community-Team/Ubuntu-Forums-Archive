---
title: "[SOLVED] Where does wine hide things?"
date: 2008-08-28
forum: General Help
---

### Post by no-1-uno on 2008-08-28
I installed a program using wine and it auto started and worked great. I shut it down and went to restart after registering it and now I cannot find it.

When I look in the applications/wine it show me its help file but no way to open the program.

I am still very new to Linux and do not know where to go and look for programs like I could in windows so could someone please help me out?

Frustrated

---

### Post by VMC on 2008-08-28
Wine installation file are "hidden" under ".wine" in your user directory. Open a terminal and type

```
ls  ~/.wine
```

"drive_c" is where your installed Wine programs lay. Use Nautilus to investigate. Just make sure you turn on "Show Hidden Files".

---

### Post by drs305 on 2008-08-28
The command to launch wine apps once you have installed them through wine depends on how you installed wine. In mine it is:
```
wine "C:\Program Files\app-folder\app.exe"

```

You can add a shortcut on your desktop or panel. Select "Application" as the type.

---

### Post by malachi1990 on 2008-08-28
You should be able to find it using Wine's virtual C:\ drive, from the application > wine > Browse C:\ drive,  but if you can't:

Go to your terminal and type wine PROGRAM (meaning the program name is in all caps). You should be able to run the program that way, but you have to keep the terminal window open.  

Sorry I can't help more, but I don't know how to display a folder with a command, as the .wine directory is apparently inaccessible from your user directory.

---

### Post by no-1-uno on 2008-08-28
First off, Hello and thank you for your help.

When I run what you have suggested in terminal this is what I get

no1uno@Frankenstein:~$ wine "c:\program files\app-folder\app.exe"
wine: cannot find 'c:\program files\app-folder\app.exe'
no1uno@Frankenstein:~$ c:\program files\app-folder\app.exe
bash: c:program: command not found


no1uno@Frankenstein:~$ ls  ~/.wine
dosdevices  drive_c  system.reg  userdef.reg  user.reg
no1uno@Frankenstein:~$ 

Thank you for your help but I am still clueless.

What is Nautilus?

---

### Post by BLTicklemonster on 2008-08-28
Open Nautilus, press ctrl+h, then find .wine, then go to drive_c, then program files. Your program will most likely ( :) ) be there, if clicking on it does not open it in wine, try right clicking it and choose open with wine. Otherwise, now that you know where it is, use the method mentioned above to open it or create a launcher using it.

---

### Post by drs305 on 2008-08-28
> **no-1-uno said:**
> First off, Hello and thank you for your help.

When I run what you have suggested in terminal this is what I get

no1uno@Frankenstein:~$ wine "c:\program files\app-folder\app.exe"
wine: cannot find 'c:\program files\app-folder\app.exe'
no1uno@Frankenstein:~$ c:\program files\app-folder\app.exe
bash: c:program: command not found


no1uno@Frankenstein:~$ ls  ~/.wine
dosdevices  drive_c  system.reg  userdef.reg  user.reg
no1uno@Frankenstein:~$ 

Thank you for your help but I am still clueless.

What is Nautilus?

I failed to properly capitalize my previous entry to "Program Files".

The key is to find the path to your apps folders. Look at your setup with nautilus or another file browser and see what is listed under "~/.wine/drive_c"
```
nautilus ~/.wine/drive_c
```

This is my start code for an app in ~/.wine/drive_c/'Program Files/EasyBid6/EasyBid6.exe':
```
wine "C:\Program Files\Easybid6\EasyBid6.exe"
```

---

### Post by no-1-uno on 2008-08-28
I hate to seem so stupid but this is about my second or third month now running Ubutu and coming from 20 plus years of windows I feel lost most of the time.

I tried
no1uno@Frankenstein:~$ wine "drive_c/
> 
> nautilus ~/.wine/drive_c"
wine: cannot find 'drive_c/

nautilus ~/.wine/drive_c'
no1uno@Frankenstein:~$ 

And this is what I got

I have downloaded a couple of Linux books but still do not understand the whole command line thing but I am trying.

Thanks for your help and patience

---

### Post by no-1-uno on 2008-08-28
Is "tracker search tool" like Nautilus? By the way I am running ubuntu 8.04

Should have mentioned that earlier sorry

---

### Post by mocoloco on 2008-08-28
Nautilus is the file manager, just like Windows Explorer is for a Windows system.  When you go to anywhere in the "Places" menu, that opens Nautilus (titled by the friendly name "File Browser").

Just go to Applications -> Wine -> Browse C Drive

That will take you to the place in your home folder where wine puts everything, a folder called .wine/drive_c
From there you can go to Program Files, into the apps directory, and double-click it's executable.

---

### Post by drs305 on 2008-08-28
I was writing a response when you added your last two entries.
Run this command:
```
nautilus ~/.wine/drive_c
```

Otherwise, just open nautilus, make sure hidden files are viewable (CTRL-h) and look for your .wine folder. If you can't find it, run this to do a search of your system:
```
sudo find / -type d -iname *wine*
```

You can also try to locate them with:
```
sudo find / -type d -iname "Program Files"
```

Once you have located them, refer to the command in Post 7 and modify for the folder location in your system.

---

### Post by no-1-uno on 2008-08-28
Thanks mocoloco that worked perfect.

---

### Post by no-1-uno on 2008-08-28
drs305 that first one worked great and was fast too

Thank you 4 your help

---

### Post by drs305 on 2008-08-28
Command line junkie fails to keep it simple... sorry for the aggravation. ;-)

Please mark this SOLVED via the "Thread Tools" link at the top right of the first post if you have no more questions.

---

### Post by no-1-uno on 2008-08-28
Thats OK I really want to become a command line junkie. I am just way behind on learning how it works.

I thought I understood more than I do so obviously I need to hit the books harder or find sometuts online

Thanks again

---

### Post by mocoloco on 2008-08-28
The trick here is when apps have a name they don't show you in the GUI. Running Firefox or F-Spot from the terminal is as easy as typing "firefox" or "f-spot".
On the other hand things like Nautils or Eye of Gnome have been given friendlier names like File Browser and Image Viewer to keep things simple.

---

### Post by no-1-uno on 2008-08-28
Thanks for all of your help everybody Y'all are great.

I will close the thread now.

Thanks again

---

### Post by BLTicklemonster on 2008-08-28
I like your attitude. You should do fine with Ubuntu.

---

### Post by anachronon on 2008-09-11
> **mocoloco said:**
> Nautilus is the file manager, just like Windows Explorer is for a Windows system.  When you go to anywhere in the "Places" menu, that opens Nautilus (titled by the friendly name "File Browser").

Just go to Applications -> Wine -> Browse C Drive

That will take you to the place in your home folder where wine puts everything, a folder called .wine/drive_c
From there you can go to Program Files, into the apps directory, and double-click it's executable.
Also, you can type "winefile" in the terminal, which will open a Windows Explorer type browser of your virtual C drive.  From there, just find the .exe file that you want to run, right-click it, and select "open".  The program should then run.

As another note, not all programs install themselves in "Program Files".  just like in Windows, some create their own folders in the virtual C drive.  If fact, the programs can be found in the same places that they would on a Windows machine.

---

