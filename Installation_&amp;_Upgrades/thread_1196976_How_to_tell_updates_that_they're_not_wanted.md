---
title: "How to tell updates that they're not wanted?"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by rexy1 on 2009-06-25
There's alot of updates I don't want to download but they, ofcourse, always come ticked when the update manager starts. Is there any way to prevent this, so I won't have to untick all the updates I don't want everytime I update the system?

---

### Post by starcraft.man on 2009-06-25
> **rexy1 said:**
> There's alot of updates I don't want to download but they, ofcourse, always come ticked when the update manager starts. Is there any way to prevent this, so I won't have to untick all the updates I don't want everytime I update the system?

Had this trouble before when I did some manual tweaks on a box of mine.

The easiest way is via gui (there is also a few means by terminal but not needed). Open up Synaptic package manager, search for the package you never want to upgrade again and then - after selecting it, not the check box on the left just highlight in orange - go to the package menu > lock version. The package will never upgrade again unless you want it to and unlock it.

This will prevent all updates including security ones, only do it if you really must. Is there a separate problem that needs addressing? Unless you have a reason to I strongly advise staying up to date.

---

### Post by rexy1 on 2009-06-25
The update manager advises me to install stuff that I don't want and certainly don't need. I did what you said but found another way that practically became a somewhat simpler solution; I ticked off all sources of updates but jaunty-security. So now it won't bother me unless it's stuff that's actually important, I guess. Thanks!

---

