---
title: "Mount Option for 500GB Drive (This is just plain silly.)"
date: 2009-01-02
forum: Hardware
---

### Post by Celestika6 on 2009-01-02
Trying to mount 500GB external harddrive formatted to ext3. Mounted, then went to properties to change mountpoint from root to username. Accidentally hit a character in the "mount options" input. Now no matter what I do I get an error that says "Could not mount volume due to invalid mount option"

Here are my questions:
a) How do I fix this as I can't get into the properties without mounting the volume? (Using the terminal would be easier)
b) What mount options are available and what do they do?
c) Right now it's an MSDOS disklabel... do I want to change the disklabel and to what?
d) This harddrive IS NOT to backup my system... it's to store files on so I don't plug up my ancient computer that was purchased in 1994 and only has 5GB of download space. Mainly music, photos and videos. Is there anything I should do differently because I'm not using this hard drive for a backup?

---

### Post by Rohan Kapoor on 2009-01-02
This happend to me! I used the live-cd to repartiton it and it worked fine in the normal one again.

In the livecd go to system->administration->partiton editor!

---

### Post by SuperSonic4 on 2009-01-02
Can you post the output of ```
cat /etc/fstab
```

---

