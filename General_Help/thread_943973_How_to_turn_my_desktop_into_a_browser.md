---
title: "How to turn my desktop into a browser"
date: 2008-10-10
forum: General Help
---

### Post by josephellengar on 2008-10-10
Like make it a browser- I don't like to browser screenlet. Hardy, Gnome,

---

### Post by kerry_s on 2008-10-10
????

open your bowser and press f11? :lolflag:

---

### Post by Jose Catre-Vandis on 2008-10-10
You can use wmctrl to send a firefox window to below all other windows and maximise it (don't go full screen or it comes to the front). If you get your theming right you can "merge" the menubar with the browser window background.

Here are instructions and a script you could use to do such a thing:

install wmctrl:
```
sudo apt-get install wmctrl
```

open a text file and paste the following:
```
#! /bin/bash
firefox &
sleep 5
wmctrl -r firefox -b add,maximized_vert,maximized_horz &
wmctrl -r firefox -b add,below & 
```

You need the sleep command to ensure that firefox loads up before the window commands try to run. they won't work if the firefox window isn't there!

If you wish you can create a new firefox profile just for this purpose, so your normal profile can operate in a smaller window.

Save this as "desktopbrowser.sh" somewhere you like and make executable.

Change the background in firefox to a wallpaper you like. To make it look "seamless" use the same wallpaper as your real desktop.

Add the script to your startup sessions list Applications>System>Preferences>Sessions (? I am on openbox!)

Log out and in again - your firefox should open, maximise and go below other windows. If you want icons, Try using the Fast Dial extension to set up clickable images on your new browser "desktop".

check out [lovinglinux]("http://ubuntuforums.org/showthread.php?t=913671") thread on making a media center out of firefox for more ideas and on how to setup fast dial

---

### Post by josephellengar on 2008-10-11
no i mean a background that I can put my widgets/shortcuts, whatnot on, but it still acts like a browser, not just a window that automatically opens.  But thank you for the help

---

### Post by armageddon08 on 2008-10-11
> **idigchess said:**
> no i mean a background that I can put my widgets/shortcuts, whatnot on, but it still acts like a browser, not just a window that automatically opens.  But thank you for the help
Open compizconfig-settings-manager and enable the widget plugin. Right Click on any screenlet and select Widget.

---

### Post by celticbhoy on 2008-10-11
search google for pyro desktop and see if it meets your needs. It is the only desktop i can think of that sounds like what you want.

---

