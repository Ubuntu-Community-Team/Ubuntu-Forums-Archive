---
title: "Touchscreen Issues in Ubuntu 14.04"
date: 2014-05-07
forum: Hardware
---

### Post by thorstenr_42 on 2014-05-07
Hi,

i have a problem with my touchscreen on ubuntu 14.04. In Firefox i am not able to open dropdown menus like for example folders in the bookmarks-toolbar but also dropdown lists on websites: they open and are immediately closed again (also happens in ubuntu 14.04 live version). In chromium there is also a strange behavior in dropdown menus, like the bookmarks-folder or the settings menu: they can be open per touch but i can only select an element if i touch it very very fast, almost instantly otherwise there is just no reaction until i open the menu again. 
Scrolling in firefox per touchscreen isn't possible but thats a firefox problem and i am able to achieve this with the grab & drag addon. in Chromium however touch works perfectly, scrolling, pinch to zoom etc.. just the above bug(s).
I think it isn't a specific bug of firefox or chromium but an overall issue in handling touchscreen input, because i only notice this bug on a thinkpad t440s and not on a x220t (there is all working flawlessly)
Can someone help me to find a solution, or how i can find the source of this issue to fill a bug report? 

Thank you very much!

---

### Post by joel-6 on 2014-07-16
I have had this problem using Planar optical touchscreens since Ubuntu 13.04.  It is definitely a touch driver issue, as mouse clicks work perfectly fine.  Dropdown menu's briefly flash open and closed, focus on the menu is lost, and the main website body is "selected" (bordered by a dotted line indicating selection).  You can circumvent this behavior using Onboard's special mouse click modes, such as Hold-click or Timed-click.  I wish I knew of a better solution.

---

