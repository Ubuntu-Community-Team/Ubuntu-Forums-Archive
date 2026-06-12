---
title: "what command is force quit button?"
date: 2008-10-01
forum: General Help
---

### Post by smain on 2008-10-01
Hi all

I would like to make a hotkey that uses the force quit button you can add on the gnome panel... but what command is that, I will need the command so i can use it in gconf-editor ^-^

Smain

---

### Post by Whiffle on 2008-10-01
"xkill" would probably work.

---

### Post by russlar on 2008-10-01
CTRL + ALT+ ESC might work, too.

---

### Post by smain on 2008-10-01
CTRL + ALT + ESC doesn't work at all... 

hmm well xkill would do... but it not quite the same command I guess.. I get another cursor than the button, and no little window popping up asking me to click on the program to close...

Does anyone know the specific command that the force quit button uses?

---

### Post by lintoon on 2008-10-01
Right click on the panel and select "Add to panel", scroll down and select "Force quit", click "Add".
This puts a nice little icon on your panel which you click on to activate then click on the window which is hung.
It's really handy.

---

### Post by smain on 2008-10-02
> **lintoon said:**
> Right click on the panel and select "Add to panel", scroll down and select "Force quit", click "Add".
This puts a nice little icon on your panel which you click on to activate then click on the window which is hung.
It's really handy.

Yeah I know that, but I don't want the button (I hate buttons on my panel, they are ugly xP)... I want to bind the command THAT exact button uses to a hotkey like e.g. CTRL+ALT+Q (So far I have bound the xkill command to this hotkey)...

---

### Post by lintoon on 2008-10-02
Try xkill

---

### Post by lintoon on 2008-10-02
There's also ALT-F4 to kill the frontmost window.

---

### Post by lintoon on 2008-10-02
Oops sorry I've just noticed you've tried xkill.  I just totally missed it.

---

### Post by Meow27 on 2008-10-02
what about sudo halt?

i know thats the shutdown command but i never had any problems with it (when ever i freeze i just ctrl+alt to one of the 5 alternate terminals and either reboot or shut down)

edit
woops misread.... if there was only a delete function.....

---

### Post by smain on 2008-10-03
hmm doesn't seem like anyone knows the exact command... oh well then I'll just continue using xkill, works well soo... but if someone should know then I'm still interested in that exact command...

---

### Post by VCoolio on 2009-06-02
I'm still interested in this, so... bump. Xkill works of course, but you can't escape it, so if you command xkill and the stuck application closes in the meantime, you need to kill something else, which is pretty awful if you're left with your desktop only... (well, there is gnome-panel to kill but I didn't think of that fast enough :p). The force quit button listens to the escape key. Who knows?

If someone knows how to 'escape' xkill that's ok too.

---

### Post by kc3 on 2009-06-02
Meh, I just use the terminal, I like to keep it separate from the GUI just in case so I can go to a console and do it just as easily as I'm used to it. Just
ps aux | grep [PROCESS NAME] - will get you the process id than just kill and the process number

---

### Post by mcduck on 2009-06-02
> **VCoolio said:**
> I'm still interested in this, so... bump. Xkill works of course, but you can't escape it, so if you command xkill and the stuck application closes in the meantime, you need to kill something else, which is pretty awful if you're left with your desktop only... (well, there is gnome-panel to kill but I didn't think of that fast enough :p). The force quit button listens to the escape key. Who knows?

If someone knows how to 'escape' xkill that's ok too.

You can escape xkill very easily. just click anything with any other button than the left mouse button. ;)

For example a right-click anywhere on your desktop will escape xkill.

---

### Post by deja on 2010-04-16
How does nobody know what the force-kill button's program name is?  I'm in the exact same situation as the OP.  Want the applet to run on a key-binding...

---

### Post by Monotoko on 2010-04-16
I'm looking at Gnome's source code now...i shall post when i find out what commands it uses :)

---

