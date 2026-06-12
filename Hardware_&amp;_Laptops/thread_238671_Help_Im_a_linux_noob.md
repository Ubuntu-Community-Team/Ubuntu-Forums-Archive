---
title: "Help Im a linux noob"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by TH3W1R3D on 2006-08-18
Hey guys I have an older laptop that has ALOT of issues (OS problems). Anyway I need to reinstall Windows to really get it back to a usable point. Unfortunately I don't have the disk and so I figured hey why not Linux? All I need it to do is basic things. Then it hit me. What about the drivers for USB, That little mouse pad thing, and all that other stuff? Will Ubuntu work with my laptop? Running it off the CD seems to work, at least partially. I can't change the resolution to a resolution I know it *should* support.
Help Please.

---

### Post by spin2cool on 2006-08-18
If the live CD is functional, you should be in good shape.  Screen resolution issues can usually be fixed by mucking around with your xorg.conf.  Look around the forums to see if other people with your laptop have fixed any other issues with touchpads, etc.  

Good luck!

---

### Post by TH3W1R3D on 2006-08-18
Are there things that I will need to download? Like drivers or anything?
EDIT:
New problem, I decided that I'd install linux and figure out any problems while running linux. Anyway well I can't install Ubuntu because the resolution is lower than it should be and I can't change it. The window for the installer is too big and I can't resize it, so I can't press the "Next", "Install", etc. buttons.
Any ideas?

---

### Post by givré on 2006-08-18
linux don't work that way.
In the kernel, there is already a lot lot of driver, most of the time everything you want. It's could happens that sometimes for exotic hardware you have to search to install a driver, but in the majority of the case, it's "out of the box".
Try and if you have a specific problem, just come back, there will be always people to help you here 8)

---

### Post by TH3W1R3D on 2006-08-18
> **givré said:**
> linux don't work that way.
In the kernel, there is already a lot lot of driver, most of the time everything you want. It's could happens that sometimes for exotic hardware you have to search to install a driver, but in the majority of the case, it's "out of the box".
Try and if you have a specific problem, just come back, there will be always people to help you here 8)
Thanks :) 
Anyway yes I have a specific problem. Resolution. (Copy and pasted from old edit..)
New problem, I decided that I'd install linux and figure out any problems while running linux. Anyway well I can't install Ubuntu because the resolution is lower than it should be and I can't change it. The window for the installer is too big and I can't resize it, so I can't press the "Next", "Install", etc. buttons.
Any ideas?

---

### Post by TH3W1R3D on 2006-08-18
Nevermind I am able to Install, but if anyone has a fix for the resolution problem please post.

---

### Post by givré on 2006-08-18
Wha, that's a ](*,) problem.
You'll be able to change the resolution but that will need to restart X (the graphic system in unix), so i'm not sure that you'll be able to do that from the installer CD.
You could try that : [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)
You may try the alternate CD.

---

### Post by TH3W1R3D on 2006-08-18
> **givré said:**
> Wha, that's a ](*,) problem.
You'll be able to change the resolution but that will need to restart X (the graphic system in unix), so i'm not sure that you'll be able to do that from the installer CD.
You could try that : [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)
You may try the alternate CD.

Help or directions to restart X and get my resolution back to normal would be VERY welcome ;)

---

### Post by givré on 2006-08-18
Th link was made for that [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973) ;) 
But not sure that it will work from the installer CD, just try.
Just follow first the "How to reconfigure Xorg"
if you don't find the good resolution you think it can support, you'll have to add it yourself with "Adding custom modeline"
You may have a look also at "Problems? Things to try:"

---

### Post by Monster_user on 2006-08-18
Well, if you know the correct resolution for you screen, just put it first in the '/etc/X11/xorg.conf' file.

Try opening a Console Terminal, or switching to a full screen console. "Ctrl-Alt-F5". "Ctrl-Alt-F7" is the Desktop.


Then type,...

'sudo vi /etc/X11/xorg.conf'

Press "Insert" to start editing it, and "Esc" to stop. Press the semicolon':' to enter a command.

':write' is to save.

':quit' is to quit.

```
Section "Monitor"
        Identifier      "StudioDsply1"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Geforce 4 Mx440"
        Monitor         "StudioDsply1"
        DefaultDepth    24
        SubSection "Display"
                Depth           8
                Modes           "640x480" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "800x600" "1024x768" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

In this case, the bottom 24 Depth is used, so 1024x768 would be the default resolution. But if I were to set it to 15-bit, then it would use the 800x600 resolution.

Knowing the internal refresh rate of your screen may also help. Just in case Ubuntu did not detect it properly.

---

### Post by TH3W1R3D on 2006-08-18
Great! I'll give it a shot once this installations over.
63%...

---

