---
title: "I need help with my web browser"
date: 2008-09-02
forum: Hardware
---

### Post by cocobrotha1 on 2008-09-02
hey everybody i need to know how to put my web browser back in order. A friend of mine tried to help me with the embedded video problem i posted about a while ago. As he was helping me he had me do a bunch of commands in the terminal and it kinda screwed up my browser. I have a list of mini toolbar tags at the bottom of my address bar: Disable, cookies, css, forms, images, info, micellaneous, outline, resize, tools, view source. on top of that i lost the use of the navigation button: forward, back, refresh, stop. my homepage doesn't even open up to the ubuntu gnome page anymore, the link is set in the hompage space but its not going there. Can someone please help me. Everyone says this is easy to run. Understanding the concept is easy, but implementing the tools to run it is hard as you know what. Please help me fam.

---

### Post by alphane on 2008-09-02
Right click up next to File Edit View History etc (or if they are hidden, right click up where they ought to be).

Uncheck "Web Developer Toolbar"
Check "Navigation Toolbar"
if wanted check "Bookmarks Toolbar"

This should get you back up and running!

---

### Post by alphane on 2008-09-02
Also.. the same submenu can be reached by going to View > Toolbars > ...

---

### Post by cocobrotha1 on 2008-09-02
> **alphane said:**
> Also.. the same submenu can be reached by going to View > Toolbars > ...

Thanks a bunch alphane. But, i'm still having trouble navigating through webpages. Let me hit y'all with the skinny.

Everytime i visit a webpage, the word icons (file,edit,view,history,etc) and the icon buttons (forward,back,refresh,stop) are greyed out and can't be used.

The web history doesn't keep my visited pages as well.

Any pages that i visit, they load up but stay loading. this is really getting on my damn nerves.

is there anyway to reset the browser in order for everything to run properly again or do i have to re-install ubuntu just to get my browswer to run right.

As a matter of fact, now that i think about it, my friend made me do something in the terminal in which i had to make my browser part of the root directory, where i was running the browser thorough the terminal. I don't know if this bit of info helps.

---

### Post by alphane on 2008-09-03
If you were running a command similar to "sudo firefox" then I wouldn't think that's too much to worry about.

I would probably look at removing firefox and reinstalling, you can do this through synaptic - search for firefox, select remove all, then reinstall.

You can do it through the terminal too, but I'm crap at remembering commands and I'm at work, but i would imagine it's something similar to:

sudo apt-get remove firefox
sudo apt-get install firefox

hope this helps...

---

### Post by Malac on 2008-09-03
Not a good idea to run your browser as root using sudo as this opens your system up to exploits.
 
```
sudo apt-get **-purge** remove firefox
``` this also removes the configuration files.
You may also need to remove your ~/.mozilla/firefox folder as well.
It would be worth saving your bookmarks.html file from inside there first. Then importing it after the reinstall.
 
Hope this helps.

---

### Post by cocobrotha1 on 2008-09-10
> **Malac said:**
> Not a good idea to run your browser as root using sudo as this opens your system up to exploits.
 
```
sudo apt-get **-purge** remove firefox
``` this also removes the configuration files.
You may also need to remove your ~/.mozilla/firefox folder as well.
It would be worth saving your bookmarks.html file from inside there first. Then importing it after the reinstall.
 
Hope this helps.

Malac, i've tried that command in the terminal and it didn't work. Also, i tried to delete the folders, but can't.  Some to do with the permission settings, bugged out thing is i'm the owner, i should be able to do it hands down, but can't. Still need help.

---

### Post by Malac on 2008-09-10
> **cocobrotha1 said:**
> Malac, i've tried that command in the terminal and it didn't work. Also, i tried to delete the folders, but can't. Some to do with the permission settings, bugged out thing is i'm the owner, i should be able to do it hands down, but can't. Still need help.
Okay,
Open Synaptic Package Manager and find anything related to firefox that you want to remove. Mark it for Complete Removal. Then Apply.
Exit
 
Press Alt-F2 type in ```
gksu nautilus
``` enter your password then navigate to the folders you want and delete them.
 
Then Logout and back in again.
 
Then```
sudo apt-get install firefox
```
 
Hope this helps.

---

