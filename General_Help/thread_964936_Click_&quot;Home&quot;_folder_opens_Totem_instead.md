---
title: "Click &quot;Home&quot; folder opens Totem instead"
date: 2008-10-31
forum: General Help
---

### Post by xjgnsdof on 2008-10-31
When I select "Home" from my "Places" menu, I instead open Totem movie player, which then proceeds to load every file in my home folder in the playlist. I uninstalled Totem, and everything worked fine, but does anyone know how I can have both on my system?

---

### Post by mc4man on 2008-10-31
see here for 'fix' and info. Thought this was fixed in the rc and final release, apparently not in all cases.
[http://ubuntuforums.org/showthread.php?t=936044](http://ubuntuforums.org/showthread.php?t=936044)

---

### Post by xjgnsdof on 2008-10-31
Thanks. That worked.

However, I have a follow-up question. I can only load nautilus through the "Places" menu; typing "nautilus" in the terminal does nothing. Am I entering the wrong command?

---

### Post by mc4man on 2008-10-31
> Am I entering the wrong command
No, that works here. Also the problem nautilus being 'bumped' as default app for directories has also been fixed here. Are you fully updated?

Any additions I make now to the r.click 'open with' on folders are added to the end of the 'inode/directory=' line so nautilus remains the default. (in intrepid first listed is default

---

### Post by xjgnsdof on 2008-10-31
I'm fully updated, but I still can't open nautilus by typing "nautilus" in the command line; I can only do so by clicking the icon in "Places." Finally, EasyStroke gestures don't open nautilus either.

EDIT: My mistake; I can open "nautilus" in a terminal window, but not in a Tilda drop-down window or through Easystroke.

---

### Post by mc4man on 2008-10-31
Never heard of easystroke - just tried, kinda interesting. Has no problem opening nautilus from a gesture as long as it's recognized (the gesture).

When you 'run' the gesture are you seeing the little pop up 'gesture#' box?

( I used just a right mouse button+mouse movement gesture

---

### Post by xjgnsdof on 2008-10-31
Yes, I see that little pop-up when I complete a gesture. Nothing happens when I try to open nautiuls, though. Maybe I should reinstall it?

---

### Post by xjgnsdof on 2008-10-31
I just installed the updated version of Easystroke (0.2.2-1), and it only opens nautilus with a gesture when I launch Easystroke through the command line. When I let it autostart at boot-up, I run into the problem.

---

### Post by mc4man on 2008-10-31
I've been opening from applications -> universal access, gonna try adding to start up and see.

Edit: same thing - all the gestures I set up work except nautilus when easystroke is loaded at startup...??

---

### Post by xjgnsdof on 2008-10-31
I can't launch Nautilus through any auto-started program, which would be GNOME-Do, Tilda, and Easystroke in my case. I can launch it just fine from the Places menu, but Easystroke and GNOME-Do are much faster alternatives. Only when I start the aforementioned launcher programs manually will they load nautilus.

---

### Post by kaivalagi on 2008-11-01
There is a launchpad bug for this: [https://bugs.launchpad.net/ubuntu/+s...us/+bug/260492](https://bugs.launchpad.net/ubuntu/+s...us/+bug/260492)

In summary, the best fix is to edit ~/.local/share/applications/mimeapps.list removing the offending ?.desktop entries against the inode/directory entry.

e.g. from:
```

inode/directory=userapp-baobab-OO53FU.desktop;nautilus-folder-handler.desktop;nautilus.desktop;userapp-nautilus-XXZ2JU.desktop;
```

to:

```
inode/directory=nautilus-folder-handler.desktop;
```

There is no need to go through all the places bookmarked changing the "open with" options

---

### Post by xjgnsdof on 2008-11-02
> In summary, the best fix is to edit ~/.local/share/applications/mimeapps.list removing the offending ?.desktop entries against the inode/directory entry.

I've done that, but I still can't launch nautilus through my autostarted programs: EasyStroke, Tilda, and GNOME Do. Only when I launch them manually can I open nautilus successfully.

---

### Post by xjgnsdof on 2008-11-03
up

---

### Post by mc4man on 2008-11-03
I tried a bunch of silliness like moving the easystroke exec to home dir., using a script instead of a direct nautilus command, using a script to autostart instead  of easystroke directly - same thing, everything but the nautilus gesture works.

What I did notice is gksudo nautilus will work from autostart so it may be a permission thing, maybe the autostarted easystroke doesn't have it for opening nautilus...?

---

### Post by xjgnsdof on 2008-11-04
At least I'm not alone on this. I guess it's time to wait for a bug fix in the next round of updates. If anybody has fixed this quirk, I'm all ears, though. I'm going to report this bug just to be safe. mc4man, I suggest you join me.

---

### Post by Tom Jaeger on 2008-11-05
This is a known problem that will be fixed in the upcoming 0.3.0 release of easystroke (even though it's not strictly easystroke's fault).  More information and a workaround here:

[http://ubuntuforums.org/showpost.php?p=5896382&postcount=178](http://ubuntuforums.org/showpost.php?p=5896382&postcount=178)

---

### Post by xjgnsdof on 2008-11-05
This workaround does the trick for Easystroke, though GNOME-Do and Tilda still don't perform the command. It'll have to do for now...

---

### Post by Tom Jaeger on 2008-11-05
> **elgilicious said:**
> This workaround does the trick for Easystroke, though GNOME-Do and Tilda still don't perform the command. It'll have to do for now...

Try 
```
sh -c "unset ...; nautilus ..."
```

---

### Post by xjgnsdof on 2008-11-06
> **Tom Jaeger said:**
> Try 
```
sh -c "unset ...; nautilus ..."
```

Output reads as follows:
Could not find "/home/emones/...".
Please check the spelling and try again.

---

### Post by Tom Jaeger on 2008-11-06
> **elgilicious said:**
> Output reads as follows:
Could not find "/home/emones/...".
Please check the spelling and try again.

What I meant was
```
sh -c "unset DESKTOP_AUTOSTART_ID; nautilus <the name of the folder you want to open>"
```

---

