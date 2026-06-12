---
title: "Trouble Mounting Drives"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by DemoN3x on 2007-08-25
I've been using ubuntu for the last couple of weeks and having got rid of windows XP decided it was time to convert all my storage to a native linux system.  I tried to use gparted to resize a partition but it complained their was an error on the drive.

I then used a dos boot cd to run a chkdsk on my two ntfs drives and the errors where corrected.

However upon booting back into ubuntu I noticed my two drives weren't listed on the desktop as usual.  I had to manually mount them but could only do so as root.

Even after I had mounted them I could only access them by becoming root again.

Even suggestions how to get them back to where normal users can access them.

---

### Post by merlinus on 2007-08-25
```

sudo apt-get install ntfs-config

```

then

```

sudo ntfs-config

```

Tick appropriate boxes and restart.

-merlin

---

### Post by DemoN3x on 2007-08-25
Hmm the problem is more in depth than I though.  Somehow the Master File Table has been corrupted.  I managed to repair it on one drive but on the larger of the two nothing has helped.

I can mount and access the partition though linux but no go anywhere else.

Thanks for your suggestions anyway.  Best I can do now is recover my important data and delete the rest :(

---

