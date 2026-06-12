---
title: "Comix replaced Nautilus on Ibex install?"
date: 2008-10-31
forum: General Help
---

### Post by plain_jim on 2008-10-31
Had a problematic Ibex upgrade (wouldn't boot; had to download the CD and install Ibex from new). Since then, if I install Comix thru the Synaptic Package Manager dropdown in the "System" item on the desktop menu bar, then click on an icon in the "Places" dropdown, the location (e.g., "Home Folder") opens in Comix rather than Nautilus.  When I uninstall Comix, Nautilus returns.

Info that may be useful:
- /home directory is in a separate partition that I did not change when I did the Ibex install
- Did searches for "Comix", "replace file manager", and other things in this forum, and couldn't find anything that appeared to fit.

---

### Post by plain_jim on 2008-11-03
I worked out my own kludgey solution, 'cause I have a few comic files for which I couldn't find a better solution than Comix.  The file manager for Gnome is nautilus (did everybody know that but me?)  I put shortcuts for nautilus in the menu, on the desktop, and on the top menu bar.  When I need to work with files, I can use those. In the meantime, I can use Comix.  If Comix ever becomes a problem, I'll uninstall it.

(I shoulda left my Hardy installation alone...)

---

### Post by emackey3k on 2008-11-03
I am having the same problem.  I had to uninstall comix and am currently using qcomicbook instead.  My home directory is not on a separate partition.  Any folder I had bookmarked under places would open in comix instead of the file manager.

---

### Post by plain_jim on 2008-11-05
I found ANOTHER solution, that works better.  Use nautilus to open a file window (do it from a terminal), and maneuver around until you get to a window with few files*, so there's white pace below the last file on the right-side pane.  Right-click in the white space, and click "Properties" if the resulting menu box.  The next box will have tabs.  Click on the tab named "Open With"  (well, DUH!), and choose "Open Folder"... and you go back to your standard view of opening folders when you click on a folder under "Places".

(*You can also create a new, empty folder for this step; when you open that, you'll have all the white space you need.)

I don't know how to ask for this feature, but I'd be grateful if El Exigente over at Ubuntu could include this ability in "Preferred Applications" in "System/Preferences".

(And I didn't like qcomicbook, and the /home on a separate partition has nothing to do with the "comix replaces nautilus problem", although I didn't know that when I posted the first message.)

---

### Post by emackey3k on 2008-11-05
Thank you that worked like a champ.  It is strange that it defaulted opening folders to Comix, especially since I have a laptop that I also just upgraded to 8.10 with Comix installed and didn't have the same problem.  I am happy I get to use Comix again because I like it better than qcomicbook too.

---

