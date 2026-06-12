---
title: "Where's the wastebasket?"
date: 2009-08-20
forum: Hardware
---

### Post by RainKap on 2009-08-20
I've installed Jaunty Netbook Remix on my Aspire One (1GB RAM, 16GB SSD) and mostly I'm happy with it. However I needed to restore something that I'd mistakenly deleted (fortunately to the wastebasket) today, and realised that there's no wastebasket icon when I have the Netbook Remix desktop - I have to change to the "classic" Ubuntu desktop to find it. Is there something simple that I've missed? It would be nice to be able to access the wastebasket without changing the desktop...

Thanks in advance for any help

Ian

---

### Post by JOHNNYG713 on 2009-08-20
Hi, Right click task bar, Add to panel, Scroll to trash, Add
also you can install ubuntu tweak and get icons on your desktop amongst other things!

---

### Post by RainKap on 2009-08-20
Thanks, JohnnyG - the only problem is that when I have the Netbook Remix desktop (as distinct from the "classic" desktop) there's no taskbar. I've downloaded Ubuntu-Tweak, and selected the option to display the trash can on the desktop - that seems to have done what it says on the tin, but the UNR setup seems to have got screwed up now - having switched to "classic" desktop and back to the Netbook Remix desktop, applications open in "classic" style, and having closed a Nautilus window I have a bare desktop with the "Computer", "Deleted Items" and "ian's Home" icons on it and nowt else - time for a reboot, I think!

At least the reboot got me back to the usual UNR favourites screen, but applications now open in "classic" style, but with no minimise, maximise/restore and close buttons in the top RH corner.:confused: This looks like I need to do more digging...

After switching to "classic" desktop view, I got the full screen window of "ian's Home" - when I closed that, it was back to the bare desktop with the "Computer", "Deleted Items" and "ian's Home" icons on it and nowt else. Time for bed...

Ian

---

### Post by kerry_s on 2009-08-23
open the trash in nautilus, click bookmarks-> add bookmark

---

### Post by stacych on 2012-04-01
Total n00b advice from Ubuntu NBR

what worked for me is to open the file folder where you normally store thigns. Any of these folders will do.
click VIEW on the drop down menus along the top
The chose to view the Side pane

Trash is visible in the side pane

I went through all the advice about nautilus, and when i finally found it it was empty. I have no idea what nautilus is, but if what you want is to empty your trash, or fine a file accidentally sent there, the above works with no complicated stuff about this Nautilus thing.

:)

---

### Post by tuxtout on 2012-04-01
1. Open gconf-editor (via Alt-F2)
2. Browse to /apps/nautilus/destop
3. Check trash_icon_visible

---

