---
title: "[SOLVED] Where's the Hollywood Got Nothing Effects"
date: 2008-08-13
forum: General Help
---

### Post by Nazty_Nayt on 2008-08-13
Ok, I have Ubuntu on my PC, and I just installed it on my laptop, but I can't find the hollywood got nothing effects setting?  Normally I would go to Sys/Pref/Appearance, and select the visual effects tab, but when I do I just get none, normal, and extra.  Can't figure it out.  I have compiz, and emerald installed, and both work fine.  Can anyone help me out here?

---

### Post by overdrank on 2008-08-13
> **Nazty_Nayt said:**
> Ok, I have Ubuntu on my PC, and I just installed it on my laptop, but I can't find the hollywood got nothing effects setting?  Normally I would go to Sys/Pref/Appearance, and select the visual effects tab, but when I do I just get none, normal, and extra.  Can't figure it out.  I have compiz, and emerald installed, and both work fine.  Can anyone help me out here?

HI and if you select normal of extra and get no effects then compiz and emerald are not working. Try and run compiz in the terminal. Or use the alt, F2 keys and enter compiz --replace. You may also want to look at the FAQ's link in my signature.

---

### Post by Nazty_Nayt on 2008-08-13
Thanks for the response.  Like I said compiz, and emerald work fine, I got my borders, I can draw fire, I have wobbly windows, and all that.  The only real thing I can't do is when I open or close anything, it explodes, turns to fire, paper airplane, etc... I can't find those options, and everything else works fine.

---

### Post by overdrank on 2008-08-13
> **Nazty_Nayt said:**
> Thanks for the response.  Like I said compiz, and emerald work fine, I got my borders, I can draw fire, I have wobbly windows, and all that.  The only real thing I can't do is when I open or close anything, it explodes, turns to fire, paper airplane, etc... I can't find those options, and everything else works fine.

In the animations tab in the  advance desktop effects settings CCSM.

---

### Post by Nazty_Nayt on 2008-08-13
Thanks Overdrank, I found them, and they were all selected, but just aren't working.  So obviously I did something wrong.  I'm going to try re-installing, and see what happens.  Thanks.

---

### Post by jmate24 on 2008-08-13
Step 1: First go to the Applications menu, click and mouse down to Add/Remove and click then you'll see a list of catagories on the left of the window and at the top center you will see  where it says 'Supported applications' click and select 'All Available applications' if a window pops up then click 'Reload' or 'OK'

Step 2: After that _in the search pane just to the right of 'All Available applications_ click your left mouse button and type 'compiz' and then hit enter.

Step 3: Following the 'Enter', in the pane just below you'll see the names of applications with little empty boxes on the left side of the pane. the program that is first on the list: Advanced Desktop Effects Settings (ccsm) mouse over to the empty check box just to the left of the name and click, It will ask you if you want to Enable the 'Universe' or 'Multiuniverse' Repository, click enable and wait 2-10sec. 

Step 4: Next mouse down to the bottom right corner of the window and click 'Apply Changes', a window will pop up and ask if you wish to install the 'Advanced Desktop Effects Settings (ccsm)' click 'Apply'.

Step 5: Then it will ask for the password that you use to login with type it in and hit enter. it will download and install the necessary files and the application so you may use it in the future.

Step 7: When the install is finished it will show a window telling you that you have installed an application and asks you if you wish to continue

Step 8: Finaly to find the app you just installed mouse up to 'System>Preferences>Advanced Desktop Effects Settings.

p.s. If at any time durring the steps a window pops up saying 

"The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue." click 'Reload

or "Another Package Manager is Working" make sure that Synaptic Package Manager when finished, Update Manager when finished, or Terminal Windows are finished or not in use, that they are closed. Then retry from Step 2.

---

### Post by Nazty_Nayt on 2008-08-13
> **jmate24 said:**
> Step 1: First go to the Applications menu, click and mouse down to Add/Remove and click then you'll see a list of catagories on the left of the window and at the top center you will see  where it says 'Supported applications' click and select 'All Available applications' if a window pops up then click 'Reload' or 'OK'

Step 2: After that _in the search pane just to the right of 'All Available applications_ click your left mouse button and type 'compiz' and then hit enter.

Step 3: Following the 'Enter', in the pane just below you'll see the names of applications with little empty boxes on the left side of the pane. the program that is first on the list: Advanced Desktop Effects Settings (ccsm) mouse over to the empty check box just to the left of the name and click, It will ask you if you want to Enable the 'Universe' or 'Multiuniverse' Repository, click enable and wait 2-10sec. 

Step 4: Next mouse down to the bottom right corner of the window and click 'Apply Changes', a window will pop up and ask if you wish to install the 'Advanced Desktop Effects Settings (ccsm)' click 'Apply'.

Step 5: Then it will ask for the password that you use to login with type it in and hit enter. it will download and install the necessary files and the application so you may use it in the future.

Step 7: When the install is finished it will show a window telling you that you have installed an application and asks you if you wish to continue

Step 8: Finaly to find the app you just installed mouse up to 'System>Preferences>Advanced Desktop Effects Settings.

p.s. If at any time durring the steps a window pops up saying 

"The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue." click 'Reload

or "Another Package Manager is Working" make sure that Synaptic Package Manager when finished, Update Manager when finished, or Terminal Windows are finished or not in use, that they are closed. Then retry from Step 2.

Uh...appreciate it there, but I'm a few steps ahead of you.  All that stuff is already checked, other wise I wouldn't be able to go to animations like Overdrank had me go to.

---

### Post by overdrank on 2008-08-13
> **Nazty_Nayt said:**
> Thanks Overdrank, I found them, and they were all selected, but just aren't working.  So obviously I did something wrong.  I'm going to try re-installing, and see what happens.  Thanks.

Ok if you would like the close animation then you will have to highlight the first animation in the close effects, duration and edit it. Change it to burn or explode or whatever you want then test it on a window.

---

### Post by Nazty_Nayt on 2008-08-13
Sweet, thanks Overdrank, works perfectly thanks.

---

