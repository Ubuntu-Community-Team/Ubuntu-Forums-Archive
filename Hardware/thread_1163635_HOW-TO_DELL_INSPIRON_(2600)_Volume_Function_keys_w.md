---
title: "HOW-TO DELL INSPIRON (2600) Volume Function keys working in XFCE"
date: 2009-05-18
forum: Hardware
---

### Post by kessaris on 2009-05-18
Hello my dear fellow ubuntuers,

After some searching and anxiety, I have finally enabled the volume keys on my xubuntu laptop running xfce.  I would like to share my research here in the hopes that it will help someone else too!

Laptop specs: Inspiron 2600 (Celeron 1200)
OS: Xubuntu 9.04 woot!

Problem: In XFCE, although there is a cute little mixer panel applet to control the volume, there is no way to adjust the volume using the blue Fn key and the volume controls built in to the Page Up, Page Dn and End keys on the keyboard.

Solution: In XFCE it is possible to assign a command to a shortcut key via the Settings->Keyboard panel.

Not sure if it's part of the solution: I installed the package i8kutils which is supposed to handle the dell inspiron function keys etc.

Extra requirements: You need to get the aumix mute toggle script attached here.  The original is here: [http://www.nirvani.net/software/aumix-mute-toggle/](http://www.nirvani.net/software/aumix-mute-toggle/) but it doesn't work unless you change it to #!/bin/bash

Walkthrough

1) Install the attached script to /usr/local/bin
$ sudo cp aumix-mute-toggle-1.1.0.sh /usr/local/bin
$ chmod +x /usr/local/bin/aumix-mute-toggle-1.1.0.sh 

2) pull up the Keyboard settings in XFCE
Applications->Settings->Keyboard
Access the second tab.. Applications Shortcuts

3) We will create three shortcuts.. Volume up, Volume Down and Mute.
The process is simple: click the green plus icon 'Add' and enter a command followed by pressing a key combination.

a) Volume up.. 
Command: aumix -v+10
Shortcut: Press your laptop's volume up key combo, in my case Fn+Page Up
It should be recognized as XF86AudioRaiseVolume

b) Volume down.. 
Command: aumix -v-10
Shortcut: Press your laptop's volume down key combo, in my case Fn+Page Dn
It should be recognized as XF86AudioLowerVolume

c) Mute
Command: aumix-mute-toggle-1.1.0.sh
Shortcut: Press your laptop's volume down key combo, in my case Fn+Page Dn
It should be recognized as XF86AudioMute

And that should be it!  Now you can test it out and you should be able to see the little volume icon raise and lower the little blue bars when you press your keys!

---

### Post by tuuca on 2009-06-09
Thank you very much for this HOWTO. Helped me a lot :-)
Works perfectly with my Fujitsu-Siemens Amilo pro v3205 as well.

---

### Post by kickwin on 2009-06-26
Worked perfectly with my Dell Inspiron 1300. Thanks a lot. 

It would be even cooler if we could activate all Fn shorcut keys.

---

### Post by mkfnx on 2009-07-15
Thanks. It also works on my Dell Inspiron 1318.

---

### Post by kickwin on 2010-12-04
It worked on Xubuntu 9.04 but not 9.10 :(

---

