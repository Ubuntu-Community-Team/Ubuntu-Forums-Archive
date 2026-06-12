---
title: "Mouse and HID"
date: 2009-02-12
forum: Hardware
---

### Post by xardias on 2009-02-12
Hi!

I want to use the 3dconnexion spacenavigator with ubuntu 8.10. The software I want to use expects it as an HID device at /dev/input/eventX, and does not use the original 3dconnexion driver. 

My problem is the following:
- The Space Navigator is recognised by Ubuntu as a mouse and I can use it in gnome just like a normal mouse (well its pretty hard to use a relative pointing device as mouse though :D). 
- I don't know much about linux HID stuff. But cat'ing /dev/input/event12 (which is the spacenav) does not show any data at all.
- /dev/input/mice,mouse0,mouse1 and any other eventX also do not show any data at all.

What do I need to do to get the data to the eventX devices?

Thanks a lot!
Dennis

---

### Post by zucche on 2009-04-14
If I remember correctly, I solved this problem by following [instructions published here]("http://jira.secondlife.com/browse/VWR-5297?focusedCommentId=91429&page=com.atlassian.jira.plugin.system.issuetabpanels%3Acomment-tabpanel#action_91429") (should the link break, look for Techwolf Lupindo's comments in VWR-5297 Second Life bug report). 
HTH...

---

