---
title: "Back up files from live CD"
date: 2008-08-20
forum: General Help
---

### Post by Reactor5 on 2008-08-20
Hi, I seriously screwed up my installation (beyond the point of booting) and I need to back up files to an external drive. Both the drive and my hard disk are readable, but if I try to copy (via nautilus or cp) the files it says I can't read them from the disk. I'm guessing I don't have the proper permissions to do so, but I don't know what command to issue to 'unlock' the drive, so to speak.

Also, having learned from my mistake this time I'll be putting my home drive on a different partition ;)

---

### Post by Potatoj316 on 2008-08-20
use the terminal to move all your files and put a sudo infront of the cp or the mv command.  you also could start a root nautilus with this command
```
gksudo nautilus
```

---

### Post by Reactor5 on 2008-08-20
I did that, but for some reason it didn't work, it still couldn't read the files. I chmoded everything to 777 and it worked.  I'll change it back (755? 700?) once I restore the files.

---

