---
title: "[SOLVED] Get Rid of Sliding Panel"
date: 2008-08-09
forum: General Help
---

### Post by Regenpak on 2008-08-09
I'm retiring my old machine running 7.04 for another lightweight box running 8.04. On the old box the Gnome (2.18.1) panels, when set to autohide, would pop into place. With Hairy Heron (2.22.2) there now is a Windows 98-esque sliding effect, which takes a long time to complete. How do I get rid of this? I can't find a setting in the Panels properties, and with the /desktop/gnome/interface/enable_animations key in Configuration Editor there's no difference. I tried in vain to find a configuration file that was modified very shortly before all to no avail.

My video adapter is a cheapo on-board affair (Jetway Mini-ITX) so effects in Appearance set to "None". No Compiz for me...

---

### Post by Krydahl on 2008-08-09
If you start gconf-editor (in the terminal) then navigate apps->panel->toplevels you should see all your panels listed. In there there is a "Hide_delay" and an "unhide_delay", specified in milliseconds, that you can set to whatever you like. Also note that I find auto hide looks much better if you set "auto_hide_size" to 1 rather than the default 6. You can't set it to 0, the panel never reappears if you do.

---

### Post by sayakb on 2008-08-09
Why don't you try out openbox WM on your machine. It is very light and flexible. Here is a link to **urukrama**'s Openbox configuration guide (the best I could find and what I used myself): [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by Regenpak on 2008-08-09
> **Krydahl said:**
> If you start gconf-editor (in the terminal) then navigate apps->panel->toplevels you should see all your panels listed. In there there is a "Hide_delay" and an "unhide_delay", specified in milliseconds, that you can set to whatever you like.
Well, *those* settings didn't solve my problem, but a setting in the same area (/apps/panel/toplevels/bottom_panel_screen0/enable_animations) was set to "true". Unchecking it solved my problem. The hide/unhide delays merely adjust the time it takes for the panel to appear once my mouse hovers over it.

Setting the size to (in my case) 3 indeed is more pleasing to my eyes. I'm very glad I got rid of this issue, I just *knew* this had to be fixable. It was just well hidden :-|

As for the Openbox: looks really nice, but it's not what I'm looking for right now. Thanx for the HU though.

---

### Post by sayakb on 2008-08-09
Please mark the thread as solved.

---

