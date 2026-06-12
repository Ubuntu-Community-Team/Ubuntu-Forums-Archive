---
title: "Cannot run this executable?"
date: 2008-09-11
forum: General Help
---

### Post by Buttons840 on 2008-09-11
[http://mirror.cs.umn.edu/blender.org/release/Blender2.47/blender-2.47-linux-glibc236-py24-x86_64.tar.bz2](http://mirror.cs.umn.edu/blender.org/release/Blender2.47/blender-2.47-linux-glibc236-py24-x86_64.tar.bz2)

I downloaded the above bz2.  I extracted it to my home and now have blender folder.  When I go into the folder there is an executable called blender.  I click on this but simply nothing happens.  I navigate the the location using the terminal and then type the name of the file, but the terminal says that blender is not installed.  I could get it from the repositories, but this is an older version and I want the latest.

How can I see what's going on with the executable?

---

### Post by mb_webguy on 2008-09-11
Have you chmod'ed the file permissions to make it executable?

---

### Post by ad_267 on 2008-09-11
When you change into that directory you have to use "./" in front of the file name to look in the current directory for the executable.

---

### Post by Buttons840 on 2008-09-11
> **ad_267 said:**
> When you change into that directory you have to use "./" in front of the file name to look in the current directory for the executable.

This worked.  How can I program the terminal to run blender every time I type "blender"?  Also, how can I program a shortcut on the gui to run blender?

Thank You.

---

### Post by p_quarles on 2008-09-11
1) You do know you can install Blender from the repositories and save yourself the trouble of trying to get a standalone binary to run?

2) Be sure to add executable permission to the file (you can do this in Nautilus, or via the command chmod) and try running it again. The next thing to try is running it directly from the command line and seeing what error messages, if any you get in return.

---

### Post by p_quarles on 2008-09-11
> **Buttons840 said:**
> This worked.  How can I program the terminal to run blender every time I type "blender"?  Also, how can I program a shortcut on the gui to run blender?

Thank You.
Typing my earlier response as you posted.

The ./ refers to the present directory. You can create a universal shortcut by using the full file path (e.g., /home/username/blender/blender-bin) as the launcher command. You can also run:
```
alias blender='/home/username/blender/blender-bin
```
to create a "blender" alias that will run the program from any location.

---

### Post by ad_267 on 2008-09-11
And you can add a shortcut in the menu by right clicking on it and selecting "Edit Menus" then add a new item and for the command enter the full path. You can add one to the desktop by right clicking and selecting "Create Launcher".

It's a lot easier if you install from the repositories using Add/Remove or Synaptic, then all of this is done for you. (System - Administration - Synaptic Package Manager and search for blender)

---

### Post by Buttons840 on 2008-09-13
The repositories have an old version.  But thanks for all the help.

---

