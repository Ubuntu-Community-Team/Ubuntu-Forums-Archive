---
title: "[SOLVED] Screen goes blank after 10 minutes"
date: 2008-07-13
forum: General Help
---

### Post by dullard on 2008-07-13
I'm wondering whether anybody has a solution to this? The threads I've managed to find  so far have not given a solution and it's proving to be the only constant annoyance I'm having since upgrading from Gutsy to Hardy.

-Screensaver settings are 'regard as idle' for 2 hours and 'activate screensaver' is unchecked.

-AC Power Management settings are ruthlessly anti-screenblanking.

-One post I came across suggested a way of removing the screensaver altogether via the Terminal, but it seems that it didn't work at all...

I'd be grateful for any suggestions or links to threads I may have missed :)

---

### Post by Rocket2DMn on 2008-07-13
Have you fiddled with gconf-editor at all?
From terminal run
```
gconf-editor
```
Then navigate the tree to apps->gnome-power-manager
Chec, out some of the settings there and in it's subfolders in the tree.  You can disable sleeping of the display, dimming and other backlight functionality.

---

### Post by monk3y on 2008-07-13
ah i had this problim before something to do with my xorg file, if i remember correctly. for some reason when i installed my ati driver with envy-ng the problim went away. sorry this was a long time ago but hopefully this gives u a hint. look under ur xorg and maybe ull find somthing wrong

---

### Post by dullard on 2008-07-13
> **Rocket2DMn said:**
> Have you fiddled with gconf-editor at all?
From terminal run
```
gconf-editor
```
Then navigate the tree to apps->gnome-power-manager
Chec, out some of the settings there and in it's subfolders in the tree.  You can disable sleeping of the display, dimming and other backlight functionality.

Aha. I like this :)

Nothing jumps out at me as a culprit in the gnome-power-manager section just yet but gnome-screensaver has a cycle_delay setting of 10 which could possibly be what I'm looking for.

I'll do some homework and check that out tomorrow.

gconf-editor is my new toy :-) Oh dear... ;)

---

### Post by Rocket2DMn on 2008-07-13
> **dullard said:**
> gconf-editor is my new toy :-) Oh dear... ;)

Play with caution, for ages 3 and up!  If you break it, you can keep the pieces.

---

### Post by dullard on 2008-07-13
> **monk3y said:**
> ah i had this problim before something to do with my xorg file, if i remember correctly. for some reason when i installed my ati driver with envy-ng the problim went away. sorry this was a long time ago but hopefully this gives u a hint. look under ur xorg and maybe ull find somthing wrong

I tried Envy last year under Gutsy and it recall having problems of some sort (probably trying to get Compiz working. No joy then but Compiz works now, although that may be more to do with backports than anything else).

Anyhow, pretty much a newbie to linux here and a google for xorg suggests it's a bit too command-line based for me at the moment. I'll get there no doubt :)

---

### Post by kaibob on 2008-07-13
> **dullard said:**
> ...I'd be grateful for any suggestions or links to threads I may have missed :)

An often suggested fix is to add the following to the end of you xorg.conf file:

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

In addition to the above, some find it helpful to change the DPMS setting in the Monitor section of your xorg.conf file as follows:

Option "DPMS" "false"

As always, but sure to have a backup of your xorg.conf file.

I tried this fix, and it didn't work. But, it only takes a few minutes and is worth a try.

---

### Post by dullard on 2008-07-14
> **kaibob said:**
> An often suggested fix is to add the following to the end of you xorg.conf file:

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection



That did the trick! For some reason I was expecting edits to xorg.conf to be far more complicated than "sudo gedit /etc/X11/xorg.conf" but now I'm beginning to love the Terminal.

Many thanks :)

---

