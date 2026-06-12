---
title: "Applications does not expand when clicked"
date: 2008-10-11
forum: General Help
---

### Post by le_vainqueur on 2008-10-11
I have the menu bar on my top panel, but when I click on the applicaitons buttion, nothing expands.  When I click either places or system, everything works as normal.  When I added the main menu to the panel, none of the applications or categories exist, but places and system are there to select.  I tried removing and re-adding the items, but that did not work.  When I log in as a different user, however, there are no problems.  What can I do to resolve this?

---

### Post by phidia on 2008-10-11
If your different user works ok then the problem must be in the /home/<username> directory that has this problem.

Open the home directory(folder) for that account click the "View" tab and select(tick) the "Show Hidden Files" selection. Try to replace the ones that related to the menu you're having trouble with. In other words copy those files from the working account to the one with the problem. Hope that helps.

---

### Post by fragos on 2008-10-11
When an application won't start when I click it, I try initiating the ap in a terminal window. Many problems that won't be presented to you in the GUI environment will give you error messages in the terminal window when run from there.

---

### Post by le_vainqueur on 2008-10-12
Thanks for the comments guys -- here is some more information.

> Try to replace the ones that related to the menu you're having trouble with. In other words copy those files from the working account to the one with the problem.

What do you mean by "the menu you're having trouble with?"  I cannot see the Applications menu, but there is no folder for that in the home directory (hidden or unhidden).

> When an application won't start when I click it, I try initiating the ap in a terminal window. Many problems that won't be presented to you in the GUI environment will give you error messages in the terminal window when run from there.

I am not actually having problems launching applications.  All of the applications I try to launch from the launcher (alt-F2) run just fine.  The problem is that I do not have an Applications menu -- it does not expand when I click it.

---

### Post by fragos on 2008-10-12
Some times exacutable file names change between releases. The gimp binary has the version number in the name. Make sure the the destop launch icon has the correct command line. Alt F2 isn't the same as running in a terminal window -- you don't get the error messages with Alt F2.

---

### Post by le_vainqueur on 2008-10-13
> **fragos said:**
> Some times exacutable file names change between releases. The gimp binary has the version number in the name. Make sure the the destop launch icon has the correct command line. Alt F2 isn't the same as running in a terminal window -- you don't get the error messages with Alt F2.

I think we're missing each other on this.  I do not have problems launching applications at all, and there are no desktop launch icons involved.  The problem is that I do not have an applications menu at all.  I click on the word "applications" which should expand into the categories of programs, etc, but nothing expands.

---

### Post by fragos on 2008-10-13
Sorry about the disconnect. If you right click "Applications" do you get a drop down menu with "Edit Menus"? Almost sounds like none of the applications are checked for execution. Edit menu will show you all the aps but if the check box isn't maked they won't appear in the list you get when you left click "Applications". I've never seen your problem occur.

---

### Post by le_vainqueur on 2008-10-13
Acutally, nothing comes up when I right click -- yet another absurdity with this problem...

---

### Post by fragos on 2008-10-13
If you right click on an empty portion of the panel is "Add to panel" offered? If so you can add the "Main Menu" or "Menu Bar" to see the applet actually works or is the problem limited to the left most iteration.

If you run the configuration editor select apps-> panel and perhaps you can fix your issue there. Panel-> global-> disabled_applets should be empty.

---

### Post by le_vainqueur on 2008-10-17
> **fragos said:**
> If you right click on an empty portion of the panel is "Add to panel" offered? If so you can add the "Main Menu" or "Menu Bar" to see the applet actually works or is the problem limited to the left most iteration.

I've done this, and "Add to panel" is available. See my first post for more details on this.

> **fragos said:**
> If you run the configuration editor select apps-> panel and perhaps you can fix your issue there. Panel-> global-> disabled_applets should be empty.

disabled_applets is indeed empty.  I would like to emphasize here, though, that the applet is not completely malfunctioning, only the "Applications" section of it.  The "Places" and "System" portions are functioning properly.  For the sake of clarity...Only when I click on "Applications" is there any sort of error.  When I do this, nothing happens (the menu does not expand).

I did look in the configuration editor to see if anything else would help my problem, but couldn't find anything relevant.  Any other ideas?

---

### Post by fragos on 2008-10-17
There are two styles of this applet availble in "Add to Panel". The default is the "MainMenu". Since it's like any other applet you can remove it and try the "Menu Bar" which although only an icon in the applet bar has access to the same capabilities as the other the default applet. Perhaps it will work.

---

### Post by le_vainqueur on 2008-10-17
> **fragos said:**
> There are two styles of this applet availble in "Add to Panel". The default is the "MainMenu". Since it's like any other applet you can remove it and try the "Menu Bar" which although only an icon in the applet bar has access to the same capabilities as the other the default applet. Perhaps it will work.

Yes, that's correct.  I tried this, and, as I said in my first post, the same problem exists.  The "Applications" item does not even exist in the "Main Menu" applet although "Places" and "System" do.

---

### Post by mc4man on 2008-10-17
Try going into home folder -> .config/menus and deleting the file 'applications.menu'   (note - .config is a hidden folder)
That should restore your Applications menu.

---

### Post by le_vainqueur on 2008-10-18
> **mc4man said:**
> Try going into home folder -> .config/menus and deleting the file 'applications.menu'   (note - .config is a hidden folder)
That should restore your Applications menu.

That worked!!!  Thanks a bunch, man!!!

---

