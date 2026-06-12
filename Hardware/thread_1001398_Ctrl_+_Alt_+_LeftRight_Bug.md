---
title: "Ctrl + Alt + Left/Right Bug"
date: 2008-12-03
forum: Hardware
---

### Post by aviscich on 2008-12-03
Just installed a fresh Ubuntu 8.10.  While the update was running I pressed Ctrl + Alt + Right to switch to the second desktop and nothing happened.  I realized later after several restarts that everytime I try to switch desktops using the keyboard shortcut there is a bug.  None of the toolbars or menus work.  As an avid windows user, the bug seems to be the windows equivalent of an explorer.exe crash.

However, in Ubuntu I have no idea how to get things to start responding again like I would in windows.  Is there an Ubuntu equivalent to ctrl+al+delete?

Anyways, I'm running it on an older Dell Inspiron 9300 laptop with ATI video card, 1gig of RAM.  Thought the bug should be passed along the proper channels.

---

### Post by pytheas22 on 2008-12-04
If you press control-alt-backspace in Ubuntu, you will kill the X server and be brought back to the login screen.  This would get you out of the frozen environment, although of course you'd lose any unsaved work.

In order better to diagnose the problem, you may want to open up a terminal before switching desktops.  Then switch desktops and let the menus freeze, and go back to the terminal and type this command:
```

dmesg > ~/Desktop/dmesg.txt
```

This will create a text file on your desktop with diagnostic information that will hopefully contain a clue about why the toolbars are crashing.  Please upload that file here so that we can take a look.

There are numerous possible culprits here--it could be a problem with compiz, with Gnome, with the ATI driver or with X--and in order to file an effective bug report, you should try to narrow down the source of the problem.

Also, does the problem still occur with desktop effects disabled (from the System>Preferences>Appearance utility)?  And can you switch desktops using the workspace-switcher applet (you can add this to your panel by right-clicking an empty place on the panel, selecting 'Add to Panel', then adding the applet called 'Workspace Switcher') without crashing?

Once we figure out more precisely where the problem lies, I can explain to you how to file a bug report if necessary.

---

### Post by cabinetman on 2008-12-11
I had the problem that the shift keys stopped working. I read "Also, does the problem still occur with desktop effects disabled (from the System>Preferences>Appearance utility)" I opened this and clicked on none and that solved my problem. I have been reading forums for 3 hours and finally. Thank you

---

### Post by pytheas22 on 2008-12-11
> I had the problem that the shift keys stopped working. I read "Also, does the problem still occur with desktop effects disabled (from the System>Preferences>Appearance utility)" I opened this and clicked on none and that solved my problem. I have been reading forums for 3 hours and finally. Thank you

I'm glad that fixed it.  If you want to use desktop effects, we can try to figure out how to make them work without causing the control-alt-arrow problem (if you don't care too much about desktop effects and are happy to leave well-enough alone, then don't worry about this).

If you want to try to figure it out, it would be good to know:

1. when the crash occurs, if you press control-alt-backspace, what happens?

2. try installing the desktop-effects configuration center by typing:
```

sudo apt-get install compizconfig-settings-manager 
```

Then launch it from System>Preferences>CompizConfig Settings Manager.  If you disable 'Viewport Switcher' and 'Desktop Wall', does the problem still occur?

3. can you switch desktops using the workspace-switcher applet (you can add this to your panel by right-clicking an empty place on the panel, selecting 'Add to Panel', then adding the applet called 'Workspace Switcher') without crashing?

4. what is the model of your graphics card?

5. what is the output of:
```

lspci -nn
```

---

