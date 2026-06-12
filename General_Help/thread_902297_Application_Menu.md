---
title: "Application Menu"
date: 2008-08-27
forum: General Help
---

### Post by Mhurst1 on 2008-08-27
How do you change the icon next to applications where the ubuntu logo is currently located?

---

### Post by quibbler on 2008-08-27
Try this post:
[http://ubuntuforums.org/showthread.php?t=498890](http://ubuntuforums.org/showthread.php?t=498890)

Regards quibbler

---

### Post by y-lee on 2008-08-27
If I understand your question I think you can open the configuration editor -- System Tools --> Configuration Editor,   From there apps --> panel--> objects.

You will see a series of folders named object_0, object_1, etc. The trick now is to discover which of those objects is your menu application. It could be any of them. Each folder contains a similar collection of information. It might help to to click thru all the objects watching the "position" key. 

From there on, it's a piece of cake. Click the checkbox for "use_custom_icon", then right-click on "custom_icon", select "Edit key..." and enter the full path to your chosen icon.

It may be a bit of work to figure out. Good luck.

---

