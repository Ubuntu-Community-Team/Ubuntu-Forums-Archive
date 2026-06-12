---
title: "cairo-dock session startup"
date: 2008-08-29
forum: General Help
---

### Post by TDragon on 2008-08-29
After reinstalling Ubuntu recently, and the rest of my programs,  I reinstalled cairo-dock and set it to start up in the sessions control panel using the "cairo-dock" command. However, it will always launch in maintainence mode when I log in or restart. When I type the command into Terminal, it will launch normally. Any ideas?

I know that from previous experience, uninstalling/reinstalling doesn't remove settings and prefrences. If I go that route, what directory I should delete so I can make sure I start from sratch with that program. Also, is it possible when I initially had the setting to auto remember running programs in the Sessions panel (currently turned off) turned on that it caused a conflict with the manual startup entry I made?

---

### Post by yoman on 2008-08-29
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by fabounet on 2008-08-29
maybe it crashes on startup, and then open the config panel ?
you should try to launch with a delay to see.

if you want to start from scratch, do a 
```
mv ~/.cairo-dock ~/.cairo-dock.bak
```
and relaunch the dock.

---

### Post by TDragon on 2008-08-31
> **fabounet said:**
> maybe it crashes on startup, and then open the config panel ?
you should try to launch with a delay to see.

if you want to start from scratch, do a 
```
mv ~/.cairo-dock ~/.cairo-dock.bak
```and relaunch the dock.

I removed the cairo-dock directories and reinstalled it (through the script posted on their site) in order to try to start from scratch.

I forgot how to delay a start-up item, could you tell me how to do that again?

Also, another minor problem, but I cannot get the dustbin to display how many items are in the Trash, even when the "Total Number of Files" option is selected for the QuickInfo. Furthermore, when I click on the dustbin icon, it does not open the trash, or when I delete the trash the icon will not update from full to empty or vice-versa. *Note: I actually had to manually point the dustbin applet to the trash bin path (/home/<user>/.local/...) in the options.*

---

### Post by TDragon on 2008-08-31
Nevermind. I modified the sessions entry for it w/ "*sleep 5s && cairo-dock*" and restarted the computer (just to be safe; instead of a logoff). The dock didn't even launch. However, when I run that exact command in the terminal, it will work on a delay. Go figure.


UPDATE: I was able to get the dustbin to delete files and update its status properly (through some permission changes on the actual directory), but I still cannot get it to display the file count or open the Trash folder when clicked on. Also, the "Shortcuts" applet doesn't display the submenu.

---

### Post by fabounet on 2008-09-01
are you under KDE ?
if not, then you shouldn't specify yourself the trash folder (let it blank). it will use the gnome VFS then, and you will be able to have the number of files displayed.

---

### Post by Wollombi on 2008-10-04
I figured out how to make it display/open the trash folder.

- Right on the trash applet and choose Configure this applet from the menu.
- In the config window, click on the module tab.
- Expand the Desktop-less support section.
- In the section labeled, "Alternative file browser used to show a trash:", enter in the name of your file browser.  In KDE it will either be konqueror or d3lphin (dolphin, but the command is spelled d3...), and in Gnome it should be nautilus.  Of course you can choose others if they better fit your preference.
- Click OK and you're all done!  You should now get a window open to trash:/ when you click on the trash applet.


Sean

---

