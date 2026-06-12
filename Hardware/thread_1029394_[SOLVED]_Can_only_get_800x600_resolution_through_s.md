---
title: "[SOLVED] Can only get 800x600 resolution through screen switch"
date: 2009-01-03
forum: Hardware
---

### Post by piddewest on 2009-01-03
Hi!

Im using Ubuntu 8.10. Computer connected through a keyboard, mouse and screen switch. Another computers is using windows also connected through the same switch.

On my Ubuntu 8.10 machine, is there a way to set the screen resolution the manual way? Thrugh some program or something.

If i understand it right ubuntu detects the monitor connected to the computer in an automated fashion. But that doesnt work for me. It cant detect my Samsung Syncmaster 713N through the switch ( i only get 800x600 resolution, nothing higher). But It detects the monitor if i connect it directly to the computer.

But i just want to specify the monitor and resolution somewhere. And yes i dont know what do do with the xorg.conf file. Dont have any clue to what to change in it.

Please help...

---

### Post by piddewest on 2009-01-04
No one has replied with any idea but i managed to find the solution by myself. I am posting it here if it may help anyone else with the same problem. Maybe not the optimal solution but i worked for me.. :D

I modified the XORG.CONF file with the following:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Samsung SyncMaster 713n"
Option "DPMS"
HorizSync 31.5 - 80.0
VertRefresh 50-75
Option "UseEdidFreqs" "1"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Samsung SyncMaster 713n"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

---

### Post by barrieg on 2009-01-04
Hi - I have a similar problem and will try you suggested fix (I am also new to Linux), I have a high res NEC monitor which will only display at 800x600. 

Thanks for your post, this seems to be a common issue.

Cheers :)

Barrie

---

### Post by piddewest on 2009-01-04
Nice...hope it works for you...
I think that the vertical sync and horisontal sync can be different depending on the monitor you use...so find out your values...

---

### Post by barrieg on 2009-01-04
sorry ... really basic question - (told you I was new, but keen to learn). 

Where do I find the XORG.CONF file, do I have to use the command line editor? (I can can see via the graphical user interface a fie called XORG.CON.NEW in the icon 'filesystem' but it won't let me save changes to it (and I am not sure this is the right file anyway).

 A bit of help would be much appreciated (I can get to a command line)< i;m sure this post would help others like me who are keen to try Linux.

Chrs

Barrie

---

### Post by piddewest on 2009-01-04
Well everybody are beginners some time :)

You can find xorg.conf in /etc/X11 directory

I used a terminal and then the command:

sudo nano xorg.conf

to edit the file. Thats all. Make sure you make a copy of it before you edit it. If you make a mistake you could end up with no graphical interface at all.

---

### Post by barrieg on 2009-01-04
thanks P, tried what I suggested but no joy, as you said I got no GUI. Managed to copy the old /etc/X11/xorg.conf back and I have the 800 x 600 GUI back.

Not sure what to do next ... any suggestions. I have tried the envy program, but no joy with that.

any pointers appreciated :)

Chrs

Barrie

---

### Post by piddewest on 2009-01-05
Im so sorry but i dont think i can help you...
Im no expert on linux....maybe you have the wrong data for your monitor in your xorg.conf file.

Maybe someone else here with more experience can help you?

Anyone out there?

---

### Post by Rohan Kapoor on 2009-01-05
> **barrieg said:**
> thanks P, tried what I suggested but no joy, as you said I got no GUI. Managed to copy the old /etc/X11/xorg.conf back and I have the 800 x 600 GUI back.

Not sure what to do next ... any suggestions. I have tried the envy program, but no joy with that.

any pointers appreciated :)

Chrs

Barrie


Can you give us the content in your xorg.conf file please?

---

