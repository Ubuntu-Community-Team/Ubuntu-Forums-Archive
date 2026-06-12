---
title: "Installing Flash 10 - brand new Ubuntu user"
date: 2008-08-23
forum: General Help
---

### Post by Guyon on 2008-08-23
After running 'flashplayer-installer' in terminal:

> dirname: extra operand `flash/install_flash_player_10_linux/flashplayer-installer'
Try `dirname --help' for more information.

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 10 for Linux

Adobe Flash Player 10 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 10 will be installed in your home directory.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 10 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...





----------- Install Action Summary -----------

Adobe Flash Player 10 will be installed in the following directory:

Mozilla installation directory  = /home/guyon/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `/libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

chmod: cannot access `/home/guyon/.mozilla/plugins/libflashplayer.so': No such file or directory

Installation complete.


Perform another installation? (y/n): 


Running Ubuntu 8.04.

---

### Post by fooman on 2008-08-23
it says "installation complete"....is flash working?

if not:

> NOTE: Please ask your administrator to remove the xpti.dat from the
components directory of the Mozilla or Netscape browser.

did you try deleting the above file like the installer suggested?

open your home directory and in the task bar click on "view".  in the drop down list,  put a tick in the box next to "show hidden files"

then go to > /home/<user name>/.mozilla/firefox*/components

*folder might be called "firefox_3.0" if your using firefox3

see if there is a file named: xpti.dat

if its there, right click on it and choose "move to trash".  then try the install again.

---

### Post by Guyon on 2008-08-23
> **fooman said:**
> it says "installation complete"....is flash working?

if not:



did you try deleting the above file like the installer suggested?

open your home directory and in the task bar click on "view".  in the drop down list,  put a tick in the box next to "show hidden files"

then go to > /home/<user name>/.mozilla/firefox*/components

*folder might be called "firefox_3.0" if your using firefox3

see if there is a file named: xpti.dat

if its there, right click on it and choose "move to trash".  then try the install again.
Flash displays things, but there's no sound and it occasionally it starts freezing repeatedly. I looked for xpti.dat before but I can't find it because there's no "components" folder, even while showing hidden files. Inside the "firefox" folder, there's two files - "1a5ymegs.default" (a folder), and profiles.ini.

Not sure if this helps any, but I'm running Firefox 3, but the folder is called "firefox". 

Thanks for giving plenty of detail. :)

---

### Post by Cheesehead on 2008-08-23
Why not simply use flashplugin-nonfree in the multiverse repository?
It works great on my system....

---

### Post by gjoellee on 2008-08-23
you have to remove the existing flash player launcher found in the .mozzila folder

---

### Post by mb_webguy on 2008-08-23
The easiest way to install Flash 10 is to get the version in the Hardy backports repository.  See the link in my signature if you need more details.

---

### Post by Guyon on 2008-08-23
Alright, a lot of information here. First of all, when I said "Flash displays things, but there's no sound and it occasionally it starts freezing repeatedly" I was incorrect. The installation didn't do anything.


> you have to remove the existing flash player launcher found in the .mozzila folder 
There's nothing inside the /.mozilla besides the folders 'extensions', 'firefox', and 'plugins'. (While showing hidden files)

> Why not simply use flashplugin-nonfree in the multiverse repository?
It works great on my system.... 
> The easiest way to install Flash 10 is to get the version in the Hardy backports repository. See the link in my signature if you need more details.
I've done this and it did install completely, however there's still no sound. I guess re-installing flash didn't fix my sound issue.

---

