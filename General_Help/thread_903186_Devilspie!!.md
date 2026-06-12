---
title: "Devilspie!!"
date: 2008-08-28
forum: General Help
---

### Post by Wickd on 2008-08-28
Hi  there I have discovered a problem. I am using the desktop cube from compiz and in order for that to work the Visual Effects has to be on extra. But if it is on that setting it does not allocate different names to different workspaces, therefore not allowing Devilspie to operate.

Example I want Skype to open in workspace 4. It will then proceed to open in workspace 1, because there is only one workspace with several columns.

Is there a way to change this? I would like to use Devilspie to open 3 applications on three different windows at startup

Thank You

---

### Post by Wickd on 2008-08-28
Nevermind found the solution! Very simple set_viewport.

---

### Post by mb_webguy on 2008-08-28
You don't need to use devilspie if you're running Compiz.  If you haven't already, install the compizconfig-settings-manager package by typing "sudo apt-get install compizconfig-settings-manager" in the terminal.  Now go to System->Preferences->Advanced Desktop Effects Settings and click the Place Windows plugin in the Window Management section.  Click the Fixed Window Placement tab, and you'll see a section called "Windows with fixed viewport".  Click the New button, and that will open a new window with placement options.  

At this point, if you're familiar with devilspie you should be able to figure things out on your own.  Click the "+" button, which will open another window which lets you select the program you want to place.  If you open the application you want to place, then click the "Grab" button and click somewhere on the application window, it will add the value for whatever type you specify.  Click the Add button, which will take you back to the first window.  Select the workspace where you want to place the application (if you're using a desktop cube, you would enter an X value from 0 to 3), and click close.  Now when you open the application, it will automatically open on that workspace.

In my opinion, it's considerably simpler and easier to manage than writing devilspie scripts...

---

### Post by kaligus on 2008-08-28
> **mb_webguy said:**
> {deletia}

At this point, if you're familiar with devilspie you should be able to figure things out on your own.  Click the "+" button, which will open another window which lets you select the program you want to place.  If you open the application you want to place, then click the "Grab" button and click somewhere on the application window, it will add the value for whatever type you specify.  Click the Add button, which will take you back to the first window.  Select the workspace where you want to place the application (if you're using a desktop cube, you would enter an X value from 0 to 3), and click close.  Now when you open the application, it will automatically open on that workspace.

In my opinion, it's considerably simpler and easier to manage than writing devilspie scripts...

I second that much simpler, I have been using devilspie and sometimes gdevilspie to configure.

I should click on a few more of the compiz boxes to see what else is hidden therein :)

---

