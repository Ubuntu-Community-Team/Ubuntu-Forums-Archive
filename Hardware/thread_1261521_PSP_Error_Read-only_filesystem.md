---
title: "PSP Error: Read-only filesystem"
date: 2009-09-08
forum: Hardware
---

### Post by andyzammy on 2009-09-08
Hi all!

I've come across a very weired bug. earlier on today, i was able to move files and folders across to my psp, but now i'm unable to move anything across, getting a Read-only Filesystem error.

according to mount -v my psp is (rw) so at least it is mounted as read write. the error then suggests to me that somehow the memory card protection has been changed to read only? (i'm doing this through the usb cable btw)

is anyone able to point me in the right direction?

thanks for your time,
zammy

---

### Post by andyzammy on 2009-09-09
solved this by reformatting the memory stick duo.

---

### Post by c00lryguy on 2009-09-09
Reformatting? Youch. I was gonna say to get a card reader and see if the card is somehow locked. But hey, whatever works, eh?

---

### Post by andyzammy on 2009-09-10
> **c00lryguy said:**
> Reformatting? Youch. I was gonna say to get a card reader and see if the card is somehow locked. But hey, whatever works, eh?

all data that was on the card was backed up, so i had nothing to lose.

actually, this problem isn't quite solved yet. i didn't notice this at first, but it must have been the time this problem occured, the /media/disk/ folder is still there (even though device was long unplugged). reinserting the same psp device (and this was before the reformat) created a disk-1. the properties of the card show its pre-reformatted state (ie read-only filesystem) and trying to rm it gives a device busy error.

can someone help me remove this phantom memory stick please?

---

### Post by andyzammy on 2009-09-11
Trying to unmount this devive gives me a "DBus error" mount not found if that helps any.

---

### Post by andyzammy on 2009-09-15
it dissapeared by its self. not sure if a restard did it because at the time i was on an uptime spree. so solved i guess. woudld have been nice to know how to get rid of it should it ever happen again if anyone knows how to though?

thanks for everyones posts,
zammy

---

