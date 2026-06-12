---
title: "Always open program in particular desktop"
date: 2008-08-16
forum: General Help
---

### Post by zephyrus17 on 2008-08-16
Is there a way to have a program, say, Evolution Mail, to always and only open in desktop 2? And Emesene only in Desktop 3?

---

### Post by wd5gnr on 2008-08-16
You could do this with wmctrl, I think. You'd have to write a script and either start the program with the script or do the old wrapper trick. That is rename the real program (call it Z) to Z.real and then make a script named Z that start Z.real. In the script you could use wmctrl to pick a desktop.

You can do other things too. See [http://www.hotsolder.com/2008/08/autohotkey-for-linux-sort-of.html](http://www.hotsolder.com/2008/08/autohotkey-for-linux-sort-of.html)

---

### Post by zephyrus17 on 2008-08-16
Is there anyway that doesn't involve scripts? Something more direct?

---

### Post by DaymItzJack on 2008-08-16
In compiz settings manager, type 'Place' in the search bar on the top left of the window and select the 'Place Windows' plugin.

Click the 'Fixed Window Placement' tab and under the "fixed viewport" (the bottom one) hit 'New' and add it there. X viewport will be the number, 1 is the first desktop, 2 is the second, etc.

---

### Post by zephyrus17 on 2008-08-16
> **DaymItzJack said:**
> In compiz settings manager, type 'Place' in the search bar on the top left of the window and select the 'Place Windows' plugin.

Click the 'Fixed Window Placement' tab and under the "fixed viewport" (the bottom one) hit 'New' and add it there. X viewport will be the number, 1 is the first desktop, 2 is the second, etc.
It didn't work. Am I supposed to select "Window Class", "Window Title", "Window Name"....? And then enter the application execution name?

---

### Post by zephyrus17 on 2008-08-17
Sorry, forget Compiz is there a way for that in Openbox? I just switched and it's brilliant.

---

### Post by issueperson on 2008-08-18
> **zephyrus17 said:**
> It didn't work. Am I supposed to select "Window Class", "Window Title", "Window Name"....? And then enter the application execution name?

You can use the "grab" tool to get the exact setting (the plus sign) for any window you need.  Look at the screenshot attached.  Just select "grab" and click on whichever window you need.

Then

In the case of Evolution, if I want it to open on my third desktop (I have 4 desktop arranged in one row) I would use an X of 3 and a Y of 1.  If you have your desktops arranged in a grid with two on top and two on the bottom, the default in Hardy, adjust your X and Y accordingly.

For some other tweaks, go back to the Compiz control panel.  Select "Window Rules" and see if any of those would also help with having evolution always running.  You can keep it fullscreen, off the taskbar, non-minimizable, non-closeable, and a lot of other stuff.

Finally, go to System > Preferences > Sessions and select "Add" and use "evolution" (lowercase) as the command.  This will start evolution when you start your computer, on whatever desktop you selected with Compiz.

---

### Post by zephyrus17 on 2008-08-18
Is there a way for Openbox?

---

