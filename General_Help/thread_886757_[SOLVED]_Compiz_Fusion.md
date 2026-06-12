---
title: "[SOLVED] Compiz Fusion"
date: 2008-08-11
forum: General Help
---

### Post by Wrycu on 2008-08-11
I recently installed Compiz Fusion through terminal.  After installing it, I do not see it listed anywhere.  Ignoring this, I started the settings editor (ccsm in Terminal) and proceeded to change settings around.  However, when I start the settings editor, I get an error about an unexpected value and how I should delete it to allow Compiz to read the settings.  The settings I set on Compiz do not seem to be kept, and I cannot get any of the special things to work.  Ideas?

I'm running an Nvidia 9800GX2, which I believe may be the problem? Yes, the drivers are installed and up to date.

Problem is this:
Compiz Fusion doesn't know where the edge of my screen is (that's the error), and the manager isn't listed, despite being installed.  The SimpleManager comes up, but I don't want that.  Whenever I CTRL+ALT+D to my desktop, all my windows disappear.


Edit: Nevermind.

---

### Post by UbuntuNerd on 2008-08-11
what exactly did you type in the terminal to install it?

and did you try looking under system > preferences > compizconfig settings manager

---

### Post by Wrycu on 2008-08-11
I typed this exactly:
```

sudo apt-get install compiz compizconfig-settings-manager

```
it said it installed properly.

I did try looking there, it's not listed.

---

### Post by UbuntuNerd on 2008-08-11
try this  Open the Synaptic Package Manager(System > Administration > Synaptic Package Manager)

 Use the search option and search for “compizconfig” (without the quotation marks)
see if compiz manager is installed if not select the package compizconfig-settings-manager. Then, click on it and select Mark for Installation

---

### Post by Wrycu on 2008-08-11
It's listed as installed.
[IMG]http://i110.photobucket.com/albums/n107/Wrycu/Screenshot.png[/IMG]

The exact error is:
```

owner@TehPwner:~$ ccsm
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

---

### Post by chris09 on 2008-08-11
try    #sudo aptitude install compiz-config-settings-manager 
then   system> preferences> appearance> visual effects and select extra:

---

### Post by Wrycu on 2008-08-11
Without the #, that gave me:
```

owner@TehPwner:~$ sudo aptitude install compiz-config-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "compiz-config-settings-manager"
Couldn't find any package whose name or description matched "compiz-config-settings-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done     

```
With it, it did nothing.

I installed the simple manager and the cube now works.  However, when I attempt to show the desktop (CTRL+ALT+D), it moves all my windows into somewhere I cannot get them, and removes them from the list of open apps.  I think this is because of the error I was getting about not knowing where the edge of the screen is....

---

