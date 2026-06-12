---
title: "iSCSI, GlusterFS, Virtual Device?"
date: 2011-10-06
forum: Hardware
---

### Post by CamoMouse on 2011-10-06
I've been racking my brain for a while now.
Did alot of digging.
Because of the way Gluster Reps data, I have to point iSCSI at a file.
That file, image, is placed in a mounted directory for Gluster to rep.
I don't like this because I need to do 2TB images. 
Gluster takes to long to reps a entire 2TB image.

I want to do Logical volumes, this is also a no go. 
iSCSI can target a LV,File, Raid. Not a directory.

My question is,
Can you mount a virtual device (file system) to a directory.
Example ... /dev/sdc1/   /replicate/


Thanks for any help in advance.

---

