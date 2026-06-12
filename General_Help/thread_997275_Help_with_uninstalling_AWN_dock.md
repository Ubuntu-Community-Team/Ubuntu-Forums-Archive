---
title: "Help with uninstalling AWN dock"
date: 2008-11-29
forum: General Help
---

### Post by brandon88tube on 2008-11-29
A while ago I installed the awn(avant-window-navigator) dock through add/remove to see what it was like. I didn't care for it that much and decided to uninstall it through synaptic package manager. This got rid of it, but it ended up leaving some files behind and I thought I got rid of them, but whenever I open up gnof or Applications>System Tools>Configuration Editor, under apps avant-window-navigator is listed. I thought I got rid of these files. Why is it still listed? Can anyone help me completely remove this from my computer?

---

### Post by seren6ipity on 2008-11-29
I would suggest using sudo to remove it completely. - 
sudo apt-get remove avant-window-navigator

---

### Post by brandon88tube on 2008-11-29
That doesn't work because it is no longer installed, but it still appears in gconf and I don't know if there are any other files still lingering.

---

### Post by seren6ipity on 2008-11-29
Try sudo apt-get autoremove. It should remove all the redundant packages including awn-manager etc.

press ctrl+alt+backspace to refresh.

---

### Post by brandon88tube on 2008-11-29
Yeah, I tried that and it still appears in gconf. I'm at a loss as to what to do.

---

### Post by trendyabinash on 2008-11-29
[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

try using the information provided here

---

### Post by brandon88tube on 2008-11-30
Well from what I have read, everything on there I tried and I still can't remove this. Is it by any chance located in a file as text somewhere that makes it appear in the list of gconf?

---

### Post by brandon88tube on 2008-12-01
Well I found a file that has avant in it that deals with gconf (/var/lib/gconf/defaults/%gconf-tree.xml) but I don't know if it would be wise to delete the lines containg info dealing with avant. Can anyone help?

---

### Post by lucidapparition on 2008-12-02
In your home directory there should be a hidden folder called .gconf. Go into that folder, find the awn files, and delete them.

---

### Post by brandon88tube on 2008-12-02
Already did that and it still is showing up. I think it might have to do with the file I listed above.

---

### Post by loomsen on 2008-12-02
The file you listed above, or more likely its name is actually pretty self-explainatory don't you think?

lib/gconf/defaults/%gconf-tree.xml

A LIBRARY specifiying the DEFAULT TREE for GCONF.

Anyway, most probable to me, just guessing as you are not willing to give a little more info, is, that you used sudo to open up gconf-editor. 

If so, you probably messed up your permissions. Or maybe you set awn to autostart?

As long as you won't tell what and where AWN still occurs, this all is and everything else will just be guessing. However, my 
/var/lib/gc... 
seems to be unattended. Actually, it is never a good idea to change any files which will be overridden by any userconfig anyway.

However, update your locate database, or use any other tool you prefer for file searching, and check which files are left of awn.

**sudo updatedb**
**locate avant | grep -v home**   [color=blue]this will most likely show you whats left of awn anywhere but in /home[/color]
**locate avant | grep /home**  [color=blue]Well...[/color]

See what's left, think about it, remove it. Anything thats explicitely called avant-window-navigator should hardly be of any further use if you removed it anyway.

Btw, the command to COMPLETELY remove any pkg from a terminal is:
**apt-get --purge remove <pkg-name>**

Anyway, open up Synaptic, chose sort by Status, and remove everything labeled Not installed (residual config)

[[img]http://www.ubuntu-pics.de/thumb/6676/screenshot_19_HrKK9v.png[/img]](http://www.ubuntu-pics.de/bild/6676/screenshot_19_HrKK9v.png)

Btw, there is also an option, equal to the --purge option:
[[img]http://www.ubuntu-pics.de/thumb/6677/screenshot_21_Dowihs.png[/img]](http://www.ubuntu-pics.de/bild/6677/screenshot_21_Dowihs.png)

If you simply mark a pkg for removal it always will leave configurations behind, so if you wanna completely get rid of a pkg use this option.

You may want to grab system-cleaner, which basically will do just that, searching for orphaned pkges/residual config files and autoclean them for you.

**sudo apt-get install system-cleaner-gtk**

to grab the gtk version of it.

---

### Post by brandon88tube on 2008-12-02
> **loomsen said:**
> The file you listed above, or more likely its name is actually pretty self-explainatory don't you think?

lib/gconf/defaults/%gconf-tree.xml

A LIBRARY specifiying the DEFAULT TREE for GCONF.

Anyway, most probable to me, just guessing as you are not willing to give a little more info, is, that you used sudo to open up gconf-editor. 

If so, you probably messed up your permissions. Or maybe you set awn to autostart?

As long as you won't tell what and where AWN still occurs, this all is and everything else will just be guessing. However, my 
/var/lib/gc... 
seems to be unattended. Actually, it is never a good idea to change any files which will be overridden by any userconfig anyway.

However, update your locate database, or use any other tool you prefer for file searching, and check which files are left of awn.


What info do you want? I never said I wouldn't give you anymore info its just that I thought what I provided was enough. I am opening up gconf through the launcher set up under Applications>System Tools> Configuration Editor. Also I removed avant by selecting avant and anything related to it in the Synaptic package manager. Then from there I went and deleted the files in my home folder. I don't know what other info you may want, but I tried to provide as much info as I could think of. I'll try removing any residual packages through synaptic and see if that works.

---

### Post by brandon88tube on 2008-12-03
Well all of those did not do the trick. It still shows up in the configuration editor.

---

### Post by ku5165 on 2008-12-13
i was wondering, if this has not been solved,
Can you still find the details to it in the Synaptic Package Manager? Shows its installed?
If you can right click on it and click "mark for complete removal"
Maybe this can help,
Ku

---

