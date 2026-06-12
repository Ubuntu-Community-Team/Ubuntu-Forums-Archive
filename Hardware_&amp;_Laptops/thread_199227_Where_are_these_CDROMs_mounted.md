---
title: "Where are these CDROMs mounted?"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by kewldude606 on 2006-06-18
I have an audio CD that I want to rip.  I put in my CDROM drive and then Sound Juicer comes up and can play the audio files perfectly.  I went to view the files with Nautilus, tho, because I was curious.  I couldn't find the files anywhere.  I double clicked on audio cd and got an error about cdda://sometihnh.  There was nothing in /mnt/ and the /media/cdrom and /media/cdrom0 were both empty.  /dev/cdrom and /dev/cdrw both got errors.  Also, I have burned many CDs with this drive before.

Now, my DVD drive.  Ubuntu recongnizes this drive in the Device Manager and I booted off this drive to install Ubuntu but when I put a DVD or CD in that drive nothing happens at all.  What can I do to fix that?

---

### Post by userundefine on 2006-06-18
```
$ cat /etc/fstab
```

---

### Post by psylvester on 2006-06-26
When I install, it says cant find CDROM, how can I manually mount the CDROM.
If I hit ALT+F2, I get the konsole. If I mount from there, will it be presistant , if i restart.
Please let me know, cauz Im stuck in the middle

---

