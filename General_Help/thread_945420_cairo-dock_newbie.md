---
title: "cairo-dock newbie"
date: 2008-10-12
forum: General Help
---

### Post by perlsyntax on 2008-10-12
How do i get the main unbuntu menu on my cairo-dock?

---

### Post by BandD on 2008-10-12
There's a long way and a 2/3 short way, 1/3 long way option.  The long way is to create a sub-dock on the main dock.  

The long way:
Click over on the left-hand side of the dock and select "Add new sub-dock" It'll bring up a window for you to fill in info such as the name of the dock and the icon you want to use.  Click ok.  The icon should appear on the left side.  Then, let's say you created the Places sub-dock, open up the gnome places menu and drag all the icons in the gnome menu to your newly created cairo sub-dock.  A few of them might not want to be drag 'n dropped and will place themselves as a launcher on the dock.  To remedy this, right click on the launcher and select "modify this launcher".  Change the "Name of container this launcher belongs to" to "Places" instead of "Main Dock".

The short way to add the Applications and the Prefrences menus is to use the nifty python script a fellow ubuntu forum mate which can be found [here]("http://ubuntuforums.org/showpost.php?p=5208447&postcount=9").  Then you'll have to to the long way fro the Places menu as I suggested above.

Hopefully that makes sense.

---

### Post by fabounet on 2008-10-13
there is a one-click way now, you just activate the applet GMenu ^_^
it works for XFCE too, and probably KDE (not tested though)
available on the SVN, and in the coming 1.6.3

---

### Post by BandD on 2008-10-14
That's awesome!  I didn't know about it...  I wish I had like 2 weeks ago, I had to reinstall cairo-dock because I boinked something...it would have saved me quite a bit of time!  Oh well.

---

