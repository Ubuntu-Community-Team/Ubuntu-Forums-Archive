---
title: "I've lost the title bar on all windows"
date: 2008-11-12
forum: General Help
---

### Post by highmighty on 2008-11-12
Hi there,

I have no clue what happened but I've recently lost the "title bar" on all of my windows/applications... see attached screenshot.

Is there a special function key that toggles the "title bar" ON or OFF? Could someone tell me how can I re-enable the "title bar" on all windows/applications?

Thanks you all for your time,

highmighty

---

### Post by Izek on 2008-11-12
Add Run application applet to the panel using "Add to panel.." by right-clicking the panel. Click on the run application icon and then in the dialog that comes up, try using **metacity --replace** in the textbox and clicking Run.

---

### Post by ajgreeny on 2008-11-12
I think Izek is right about the probable reason for the problem, but doesn't actually say what it is.  I suspect you have compiz running and with some hardware the symptoms are exactly what you describe and show in the attached picture.  You may however find that logging out and back in will overcome this, but if it is still there after doing so (or rebooting) you will probably need to set the option in System->Preferences->Appearance to "None", which is exactly what ```
metacity --replace
``` does, either in terminal or in the dialog from Alt+F2.

---

### Post by highmighty on 2008-11-13
FYI, the problem was still there after rebooting but the "metacity --replace" command solved it once and for all, thanks a bunch!

I honestly do not really understand what caused this but it is now resolved so... yeah :-)

Regards,

highmighty

---

### Post by highmighty on 2008-11-13
I still have a question for you guys, how can I permanently fix it because currently, whenever I reboot/restart, the "title bars" of any windows are always gone, I need to type "metacity --replace" (or appearance to "none") to make them appear again...

Thanks again,

highmighty

---

### Post by Izek on 2008-11-13
System > Preferences > Sessions

and in the startup programs, click Add then put in the information:

Name: Metacity Window Manager
Command: metacity --replace
Description: Replaces Window Manager with Metacity

if this doesn't work, it's because there's a short period of time where metacity is the WM before another WM takes control.

---

### Post by snova on 2008-11-13
Metacity is the program that draws the title bar and the border around the windows. Open the session manager as was previously suggested and see that Window Manager was not disabled.

---

