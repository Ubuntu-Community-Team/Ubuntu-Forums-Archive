---
title: "windows external HD's"
date: 2009-03-23
forum: Hardware
---

### Post by pilkington on 2009-03-23
I just installed ubuntu on another HD since my windows HD died.
Now I can't access my external usb HD's, it says it can't mount them though it sees them.
they are ntfs formatted.
Nautilus does suggest "forcing" it (whateve that means) with this line:

mount -t ntfs-3g/dev/sdc1/media/SimpleDrv1 -o force

(SimpleDrv1 is the name of the partition on that external HD.)

But entering this line in a CLI didn't make any difference, just caused it to spew out details about the mount command.

---

### Post by binbash on 2009-03-23
> **pilkington said:**
> I just installed ubuntu on another HD since my windows HD died.
Now I can't access my external usb HD's, it says it can't mount them though it sees them.
they are ntfs formatted.
Nautilus does suggest "forcing" it (whateve that means) with this line:

mount -t ntfs-3g/dev/sdc1/media/SimpleDrv1 -o force

(SimpleDrv1 is the name of the partition on that external HD.)

But entering this line in a CLI didn't make any difference, just caused it to spew out details about the mount command.

There is a space after 3g.I got that errors every week and if you write what nautilus suggests it always work.You can also plug that into a windows and do a safely remove ;)

PS : I am not sure but you are not gonna write SimpleDrv1, just write the mount point there.

---

### Post by pilkington on 2009-03-23
> **binbash said:**
> There is a space after 3g.I got that errors every week and if you write what nautilus suggests it always work.You can also plug that into a windows and do a safely remove ;)

PS : I am not sure but you are not gonna write SimpleDrv1, just write the mount point there.

You've lost me - what is the mount point and how do I find it?

Also do I have to do this every time I log on? If so, how do I set it to auto-mount every time?

(I'm finding linux so much harder to use than Windows!!)

---

### Post by pilkington on 2009-03-23
> **binbash said:**
> There is a space after 3g.I got that errors every week and if you write what nautilus suggests it always work.You can also plug that into a windows and do a safely remove ;)

PS : I am not sure but you are not gonna write SimpleDrv1, just write the mount point there.

also I tried to enter the line again but it says it has to be done from "root" but I have no idea how to get to "root"???

---

