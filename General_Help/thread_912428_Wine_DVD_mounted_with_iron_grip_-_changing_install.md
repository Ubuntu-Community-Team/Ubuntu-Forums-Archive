---
title: "Wine: DVD mounted with iron grip - changing installation disk impossible"
date: 2008-09-06
forum: General Help
---

### Post by perixx on 2008-09-06
Well, hello there.

I just wanted to know if anyone has managed to install a game or anything else with Wine, where one has to change disks?

Tried to install a Steam-game under Wine and it wouldn't let me unmount the DVD upon the request to change disks, regardless of what I've tried:

- using the 'eject' tool
- sudo unmount /dev/sdc
- manually removing mountpoint from /etc/mtab (fstab missing)

and so on. 

Even when 'illegally' removing the disk with the 'mtab-trick' or via emergency-eject, re-inserting mtab's entry after ejecting 'blindly' and closing the tray won't mount the new disk. 

I had to copy all disk's contents into one folder and install from there - a workaround, but not desirable behaviour by any means...

regards,

perixx

---

### Post by Shazaam on 2008-09-06
"I had to copy all disk's contents into one folder and install from there - a workaround, but not desirable behaviour by any means..."

I agree but it works. Next time you get stuck try...
```
sudo eject
```

---

### Post by perixx on 2008-09-08
"sudo eject"

I assumed that one could've expected from me to use sudo - of course I did. Sorry, if I wasn't all that precise :)

As I said, I've really messed around to get Ubuntu re-mounting the DVD (I managed to 'illegally' eject it), but it was REALLY stubborn. 
Supposedly, nobody has yet thought of such a situation to be possible, hence no one implemented a way to 'pause' a program's drive-capturing request and make flipping disks possible, while that app is still taking hold of the drive...  

At least, that seems to apply to wine.

perixx

---

