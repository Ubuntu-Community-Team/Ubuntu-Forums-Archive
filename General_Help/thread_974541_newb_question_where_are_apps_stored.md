---
title: "newb question: where are apps stored?"
date: 2008-11-07
forum: General Help
---

### Post by a_toff on 2008-11-07
Hi folks, I'm a recent convert from Mac OS X. Love Ubuntu, but there's some things puzzling me...

In OS X, applications are stored in the "Applications" folder either at in the user's home or at the root of the filesystem. Where do they go in linux? 

I just downloaded Songbird for music management and I now have a folder on my Desktop containing the executable as well as all the junk that Songbird needs to run. Where do I put this thing and how do I add it to the Applications menu?

thanks kindly,
S.

---

### Post by Therion on 2008-11-07
You don't really run executable files in Ubuntu to install software.

Probably the quickest, easiest way to get Songbird installed is by using the Add/Remove option in your Applications menu.

For the rundown on how software installs are done 'buntu style, see the following:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Julian.Shaver on 2008-11-07
This should explain everything you need to know...
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

---

### Post by drs305 on 2008-11-07
Here is a pretty good guide from the Ubuntu Documentation folks on the Ubuntu/linux file structure. The structure hasn't changed much since this guide was written:
[https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html]("https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html")


**Added**: To add it to your menu, you can right click the menu icon on the panel or run "alacarte" from terminal. Either will open the main menu for editing. Select the folder or category in the left pane and click 'New Item' in the right. Give it a name, enter the command to launch it, and if it doesn't automatically add an icon (if it recognizes the app) you can click on the upper left icon and select one of your own. If the package is meant to run in terminal, click on Type and select 'Application in Terminal'.

One other note, if you are adding an app via a compilation, keep the folder created by the install as it will probably have an uninstall script in it (sometimes called *postuninst* or something similar). If dpkg/apt/aptitude/synaptic doesn't install it, it won't be able to uninstall it either.

---

### Post by nnamdi on 2008-11-07
you asl Application > Addand remove or click on System> Administration> Synaptics Package Manager that should help

---

### Post by a_toff on 2008-11-07
> **Julian.Shaver said:**
> This should explain everything you need to know...
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

thanks for the resources guys...

I'm re-downloading Songbird now from the link quoted, but I'm still wondering what I would do in theory with the Songbird folder which I downloaded previously, containing the working app.

---

