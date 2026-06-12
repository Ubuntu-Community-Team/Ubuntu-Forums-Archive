---
title: "Firefox is useless after today's update"
date: 2008-07-25
forum: General Help
---

### Post by Zyrshnikashnu on 2008-07-25
All of my vital toolbars are gone and I can't get them back. No keyboard shortcuts are doing anything. Running "firefox -safe-mode" to disable all extensions has no effect. "firefox -ProfileManager" does not run the profile manager.

Firefox is effectively dead in the water.

Please see the attached screenshot. You can see the StumbleUpon toolbar, but it never takes me to a page. I can only presume the viewing frame is also missing.

Please help!

---

### Post by tamoneya on 2008-07-25
it hasnt had any problems for me since the update.  Try a full uninstall and a reinstall.  Note:  this will remove ALL of your preferences and extensions.  Backup ~/.mozilla so that you can restore stuff later.

```
sudo apt-get update
sudo apt-get remove --purge firefox-3.0
sudo apt-get install firefox-3.0
```

---

### Post by Zyrshnikashnu on 2008-07-25
Ah ha! I found the problem. After reinstalling Firefox, Ubuntu suggested I close any instances of Firefox that were running. However, I didn't have any FF windows open. Apparently, there was a hidden process keeping it from updating properly. I killed it, and Firefox updated properly.

Thanks.

---

### Post by dreamnid on 2008-07-25
I have the same issue w/ today's Firefox update.

Upon starting up, I get this error box:

```

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:updateDisplay()
10:init()
11:([object XULElement],119)

```

Same effect when running "firefox -safe-mode"

Menus will open fine, but clicking on things that bring up dialog (like Preference) will open a dialog with just an empty title bar.

---

### Post by dreamnid on 2008-07-25
Hahaha, I feel stupid too.  I also closed all firefox windows before updating.  But there was a hidden firefox process that I just now manually close.

Thanks Zyrshnikashnu!

---

### Post by yellerKat on 2008-07-25
Didn't find any processes but had to reboot: Shades of MS!

---

### Post by ajgreeny on 2008-07-25
Mine went faultlessly except for the need to reinstall the add-on* Tab Mix Plus*, which will not install from the usual add-ons site, but only from the developer's own site where he has a version for FF3.  None of the other add-ons I use broke, only that one for some reason.  All fixed now, however.

---

