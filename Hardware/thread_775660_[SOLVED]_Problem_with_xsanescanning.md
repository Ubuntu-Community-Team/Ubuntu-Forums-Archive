---
title: "[SOLVED] Problem with xsane/scanning"
date: 2008-04-30
forum: Hardware
---

### Post by Bubtottle on 2008-04-30
I have a problem with scanning that is driving me mad. If anyone can think of anything that can possibly help, please tell me.

I have an HP Scanjet 5300C. I am running Ubuntu 8.04 (Gnome). I plugged the scanner in and xsane started up perfectly fine. I scanned a few test pages and it worked well with few problems. The problems that did occur were that I could not find a way to exit the full screen preview and at one point the menus grayed out. I cannot quite remember but I think I pressed Ctrl+Alt+Delete and logged out to get rid of the windows.

After the leaving the computer for a few hours to do other things, I attempted to scan documents that I need to scan. However, when I clicked xsane, it displayed a message box saying 'scanning for devices' and then came up with a solitary window titled Histograms. After a few seconds the window was greyed out and I eventually force quitted. This has happened every time I have tried this method since, although I did leave it for longer at one point and a further grayed out window titled 'Preview' (or something similar) appeared. If I unplug and replug the scanner, the 'scanning for devices' message appears before being grayed out after a few seconds.

I have tried unplugging the scanner, restarting the computer and then plugging the scanner in again, with the latter of the two results described above occuring. I have installed sane, removed sane, completely removed xsane (including configuration files) and deleted some files that seemed to be related to xsane in the 'tmp' folder. None of these helped the program at all. When I try to use Gimp, it gets stuck on xsane when loading. I tried installing flegita but it indefinitely searches for devices.

I know the scanner and xsane can work because of the test pages I was able to scan. Any help resolving this issue would be welcome.

---

### Post by marufaberlin on 2008-04-30
1. Do you have compiz?
2. try using gksu xsane
3. Try this
```

sudo dpkg-reconfigure -a

```
4. if that dont help:
```

sudo apt-get update xsane*

```
5. and if that dont help:
```

sudo apt-get remove xsane
sudo apt-get install xsane

```

---

### Post by Bubtottle on 2008-04-30
Unfortunately, none of those have worked, marufaberlin. I get either a grayed out scanning for devices window or a grayed out histogram window

---

### Post by jblackthorne on 2008-04-30
Have you tried coming into XSane directly through the HPLIP Toolbox?  If you have not, ensure the following packages are installed:

hplip
hplip-data
hplip-gui

* click System/Preferences/HPLIP Toolbox
* Press scan

If that does not work, try enabling "Autorefresh

* click System/Preferences/HPLIP Toolbox
* Find the device icon on the left and highlight
* Click Configure/Settings
* Check the auto refresh box

Hope that helps

---

### Post by Bubtottle on 2008-05-01
Thankyou to those who tried to help. I have managed to get the scanner working by reinstalling libsane and also installing and using gscan2pdf instead of xsane.

---

### Post by marufaberlin on 2008-05-05
K mark thread as solved then

---

