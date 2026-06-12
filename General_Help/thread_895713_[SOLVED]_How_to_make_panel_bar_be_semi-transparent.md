---
title: "[SOLVED] How to make panel bar be semi-transparent"
date: 2008-08-20
forum: General Help
---

### Post by gjr5017 on 2008-08-20
Is there a way to do this? It would make my desktop look a lot better. I also need the backgrounds of all the icons (clock, weather, notification area) to be the same transparency as the panel instaed of staying opaque behind the icon.

---

### Post by Genius314 on 2008-08-20
You can't make just the panel background transparent (yet), but you can make the whole thing transparent (the icons and text will also be transparent).

Set up Compiz, if you haven't done so already, and install CCSM:

> sudo apt-get install compizconfig-settings-manager

Now go to System>Preferences>CompizConfig Settings Manager. Go to the General Options, and click on the Opacity tab.
Click "New," and in the box that appears, type:
> type=Dock & class=Gnome-panel
And set the opacity to something around 90 (less or more, depending on how transparent you want it.)
You'll have to compromise between transparency and readability (at least until there's a way to make just the background use real transparency).

---

### Post by timcredible on 2008-08-20
to make the panel transparent, right-click on the panel, properties->background->solid color, and move the slidebar to your liking.

---

### Post by crwmike on 2008-08-20
On my panel, I created a .png image in GIMP with a vertical gradient from white to transparent and set it as the panel background.

---

### Post by gjr5017 on 2008-08-20
Okay. I already had all the stuff for compiz set up but I didn't know there was an opacity thing in the general settings (actually didnt even notice this area haha). But I've got the opacity set a 65 I think which is actually really good. I can see through the panels but still see everything clearly. Thanks a lot...only gripe is teh icons are slightly faded but its a small price to pay haha. Thanks again.

---

### Post by abdusamed on 2010-08-23
I've done this before I know it happens. How can I only reduce the transparency of panel, not the text or anything? It has to do with RGB... any light?

---

### Post by WorMzy on 2010-08-23
Just right-click on the panel, click Properties -> Background -> Solid Colour, then move the "Style" slider to the left.

---

