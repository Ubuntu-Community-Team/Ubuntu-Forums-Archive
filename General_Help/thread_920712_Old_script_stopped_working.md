---
title: "Old script stopped working"
date: 2008-09-15
forum: General Help
---

### Post by Browncoatdevil on 2008-09-15
For a long time now I've had terminal "embedded" in my desktop. I did this by using some Compiz rules and a simple startup script. Now, all of a sudden, it doesn't quite work. Do you see anything wrong with this?

[PHP]#!/bin/bash
sleep 25
gnome-terminal &#8211;window-with-profile=Clear &#8211;geometry 67×35+220+50 &[/PHP]

The only updates I've received lately are the QT4 libraries. Before, there were no window borders, and it opened relatively centered, as per the script.

Any ideas?

Edit: Upon further investigation, NONE of my Compiz settings are working. Appearance preferences shows visual effects as "none" and when I select "extra" the screen shimmers and its says no. This is after installing the new VLC.

---

