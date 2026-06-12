---
title: "lexmark x1270 . . ."
date: 2008-09-29
forum: General Help
---

### Post by Forbees on 2008-09-29
i know this has been posted alot

i've looked at a few, and they're all for older versions of ubuntu, and didn't work for me :(


i'm running 8.04

help?

---

### Post by c4n75p34k1337 on 2008-09-29
Yeah I have the exact same printer as you and for the life of me I couldn't get the damn thing setup in uBuntu. However I found that emulating XP in Virtual Box supported the printer. So try virtualization first...

---

### Post by Forbees on 2008-09-29
i tired installing virtual box and it didnt work >,<

i went to the site, used the .deb . . . and i can't find any way to execute it

so i went to terminal

sudo apt -get install virtualbox-ose
virtualbox

i get an error missing files >,<


i give up

---

### Post by c4n75p34k1337 on 2008-09-29
You have to add yourself to the vboxusers group first! Don't worry I didn't know how to start Virtual Box the first time either.

---

### Post by Forbees on 2008-09-29
blsh, i already uninstalled it >,<

---

### Post by Crafty Kisses on 2008-09-29
Lexmark isn't really supported in Linux, but HP is very well supported.

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

---

### Post by acidrums4 on 2008-11-15
I have ubuntu 8.04, the lexmark x1270 scanner works well but the printer dont't work!!! Can someone help me? I tried with the z600 driver but nothing happens.

---

### Post by ColeenM on 2008-11-27
I am a new Linux user so I need things explained clearly, I got this from another thread, from Timothy632, and using it and following some other links to pull it all together I finally got it working. I thought I'd share what I did with other folks who might need more info.
The driver that works is the Z600 v1.0-1.
I uninstalled my printer, turned it off, changed the USB port it was in, turned it back on, Linux detected it, and wanted to use the Generic driver. Let it for now, you'll use the web based Common Unix Printing System 1.3.7 to select the driver that works. 

This is directly from timothy632:
MUST INSTALL BOTH OF THESE
[http://leighm.dgtlmoon.com/misc/bina...1.0-2_i386.deb]("http://leighm.dgtlmoon.com/misc/bina...1.0-2_i386.deb")

[http://leighm.dgtlmoon.com/misc/bina...2.0-2_i386.deb]("http://leighm.dgtlmoon.com/misc/bina...2.0-2_i386.deb")

USE THE GDEBIAN PACKAGE INSTALLER

Click both of those links and install both packages.

Next go to a browser window, enter [http://localhost:631/]("http://localhost:631/"). This is the Common Unix Printing system. 

Click on the Printers tab, you should see the Lexmark listed, click on the Modify Printer button, name and description should be fine, click Continue, Lexmark 1200 Series USB #1 (Lexmark Series 1200) is fine, click Continue again, choose or Provide PPD file, click on Browse, drill down to File System/Usr/Share/Cups/Model, and here you will see the Z600 driver, choose Open, Modify Printer, and you'll see a message that the printer was successfully modified and the print test page should work. If you go back into System, Administration, and Printing, you should see that the printer driver is now the Lexmark Z600 v1.0-1.

---

