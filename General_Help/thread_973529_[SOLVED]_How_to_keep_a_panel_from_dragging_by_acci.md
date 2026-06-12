---
title: "[SOLVED] How to keep a panel from dragging by accident?"
date: 2008-11-06
forum: General Help
---

### Post by L a r r y on 2008-11-06
There HAS to be a better way of handling this!

My top panel is too full to be on the side of the screen.  I want the top panel to STAY PUT when I happen to drag the mouse across an empty spot on the panel because I was aiming for the title bar just below it.

I just got through mis-dragging it to the side, and then trying to grab a panel handle pixel SOMEWHERE to run it back to the top.  Instead I put icons on the desktop, opened the menus, opened a volume control or did nothing on a dozen tries.

I was too impatient to create a new panel and drag some stuff off the side panel to get an open place to grab it and put it back on top, then drag stuff off the new panel back to its old place on the top panel.  Then delete the new panel.

There has GOT to be a better way.

Supposing there were a _**System > Preferences >Appearance > Panel settings**_ where if I drag a full panel to the side like this, I can go and reassign it to the top?  Or set a lock on the panel position to prevent an accidental move?  Go there to unlock the panel, then move it as it can be moved today, or better, use a dialog box to choose the position, because the long top panel is too full to fit on the short side and show any kind of space to grab hold of it instead of its contents.

Is there already a solution that I am not familiar with, short of creating a new panel and dragging icons off of the full panel and then dragging the emptied panel?  Followed by moving the icons back and blowing away the new panel?

[COLOR="DarkRed"]**Edit:  My thanks to all of the folks who responded with a lot of good suggestions and potential solutions!  Read on!**[/COLOR]

---

### Post by ezramorris on 2008-11-06
Short answer:
Right click on the panel and press 'lock panel position'.


Long answer:
You can also change the panel position from the gconf-editor, although it's a bit of a pain. Hit Alt-F2, type gconf-editor and hit enter. Navigate to apps>panel>toplevels. One of the items listed in there will be for the panel you want. Your guess is as good as mine. Click on the item you want, double-click orientation, and change it to one of left, right, top, bottom. You might have to log out and back in again to see the change.

---

### Post by OrangeCrate on 2008-11-06
> **ezramorris said:**
> Short answer:
**Right click on the panel and press 'lock panel position'.**


Long answer:
You can also change the panel position from the gconf-editor, although it's a bit of a pain. Hit Alt-F2, type gconf-editor and hit enter. Navigate to apps>panel>toplevels. One of the items listed in there will be for the panel you want. Your guess is as good as mine. Click on the item you want, double-click orientation, and change it to one of left, right, top, bottom. You might have to log out and back in again to see the change.

Just an additional thought, in case the OP is not on 8.10...

I don't recall if that was an option on Hardy, or earlier releases, but it is standard behavior on Intrepid, to be able to lock the panels. Nice feature.

---

### Post by ezramorris on 2008-11-06
> **OrangeCrate said:**
> Just an additional thought, in case the OP is not on 8.10...

I don't recall if that was an option on Hardy, or earlier releases, but it is standard behavior on Intrepid, to be able to lock the panels. Nice feature.

There should be an option in ubuntuforums's user profiles for which Ubuntu version you are on.

---

### Post by OrangeCrate on 2008-11-06
> **ezramorris said:**
> There should be an option in ubuntuforums's user profiles for which Ubuntu version you are on.

Let me rephrase...

If the original poster is not using 8.10, he may not have the option to lock the panels. I believe that is a new feature on Intrepid.

Edit:

And, I'm sorry, I didn't understand your comment until Sam jumped into the thread. As he said, there is one - I didn't know that until now. Frankly, I'd prefer to see it openly on the forums again, as it use to be, rather than having to search it out in someone's profile. I wonder how many people actually know it's there?

---

### Post by Sam on 2008-11-06
> **ezramorris said:**
> There should be an option in ubuntuforums's user profiles for which Ubuntu version you are on.

There is ! As long as the user adds it on his/her [profile details](http://ubuntuforums.org/profile.php?do=editprofile).

---

### Post by OrangeCrate on 2008-11-06
> **L a r r y said:**
> There HAS to be a better way of handling this!

My top panel is too full to be on the side of the screen.  I want the top panel to STAY PUT when I happen to drag the mouse across an empty spot on the panel because I was aiming for the title bar just below it.

<snip>

Is there already a solution that I am not familiar with, short of creating a new panel and dragging icons off of the full panel and then dragging the emptied panel?  Followed by moving the icons back and blowing away the new panel?

You would find this blog post by Matt Cutts very interesting...

[http://www.mattcutts.com/blog/moving-the-locked-top-panel-in-ubuntu-gnome/](http://www.mattcutts.com/blog/moving-the-locked-top-panel-in-ubuntu-gnome/)

---

### Post by drs305 on 2008-11-06
Larry,

I now use Intrepid, which can lock the panel in position, but I feel your pain. I have had to try to find the empty pixel to get to the properties.

My inelegant solution was to put a shortcut on the panel (an up arrow was the icon) which ran the following:
```
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation "top"
```

Whenever I inadvertently moved the panel to either side, I just clicked on my new shortcut and restored the panel to the top.

Note: I am liking Intrepid more each day!

---

### Post by L a r r y on 2008-11-07
> **drs305 said:**
> Larry,


My inelegant solution was to put a shortcut on the panel (an up arrow was the icon) which ran the following:
```
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation "top"
```


Drs305,

And it works!  Thank you!  I am using a set of keys for my icon, because your solution has released me from this mess!  After I posted, I did a Google search and found another possible solution in a different thread involving ubuntu-tweak, which is supposed to let me do a fairly simple assignment of where the panel is supposed to be, but I am yet to find how to access the new install.

It sounds like Intrepid, version 8.10 is right on track with a locking solution to this problem, while I am still using 8.04 Hardy.

This thread is definitely solved, and I will be clicking the Thanks button on a whole bunch of responses as I get to investigate their solutions.  My sincere thanks to everyone!

---

### Post by ezramorris on 2008-11-07
> **OrangeCrate said:**
> As he said, there is one - I didn't know that until now. Frankly, I'd prefer to see it openly on the forums again, as it use to be, rather than having to search it out in someone's profile. I wonder how many people actually know it's there?

I agree. I'd completely forgotten it was there. I just looked now, and apparantly I'm still using Gutsy!

All sorted now, but no doubt I'll forget again; it's no way obvious enough.

---

### Post by L a r r y on 2008-11-07
> **ezramorris said:**
> Short answer:
Right click on the panel and press 'lock panel position'.


Long answer:
You can also change the panel position from the gconf-editor, although it's a bit of a pain. Hit Alt-F2, type gconf-editor and hit enter. Navigate to apps>panel>toplevels. One of the items listed in there will be for the panel you want. Your guess is as good as mine. Click on the item you want, double-click orientation, and change it to one of left, right, top, bottom. You might have to log out and back in again to see the change.

Thank you ezramorris,
Your short answer doesn't work on Hardy 8.04, but I found the use of the gconf editor to be a way to lock my panels in place.  A little draconian, but if one has the panel set up just the way it should be, one can navigate to apps > panel > global and place a check in the lock down selection, then restart the computer.

Icons cannot be moved, or removed, and the panel goes no-where.

I said restart the computer:  I locked down and logged off, had satisfactory results, ran the editor again and unlocked and logged off, and had Nautilus come up unusable because it couldn't find the factory -- whatever that means.  I shut the computer down and when I restarted this morning all was well.

I am looking this gconf editor over to see if there are any other issues it may help me with.

Thank you for your kind support.

---

### Post by ezramorris on 2008-11-07
> **L a r r y said:**
> I am looking this gconf editor over to see if there are any other issues it may help me with.

I don't use it very much, however the two things I do use it for are changing the network/volumes/home folder/etc. icons on the desktop on/off (apps>nautilus>desktop) and changing the URL handlers (ie. what happens when you create a launcher or run something such as [ftp://something](ftp://something) or mailto:someone) (desktop>gnome>url-handlers>whatever).

And by the way, drs305's solution was in essence the same as my long one, but just done on the command line. As such, you could make these changes on a regular basis by using variations of that command.

---

