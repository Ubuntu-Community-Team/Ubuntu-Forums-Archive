---
title: "WD External HD not showing it's face!"
date: 2008-12-30
forum: Hardware
---

### Post by johndoughy on 2008-12-30
So I borrowed a 110gb External Hard Drive from my friend to hold my music while I make the switch to Ubuntu from Windows XP.  Problem is, windows doesn't recognize that it even exists.

So I booted up Linux with the cd, and the external is recognized and visible!  And Read-only. :(

It tells me I have no permission to alter the files!  There's no lock or anything simple like that on the external, but gparted isn't even recognizing it!  I would like to format the bugger, wipe it clean, make it NTFS and hold my music so I can format my hard drive!

Help?  I don't know much yet about the command terminal, but I'll try pretty much whatever.

---

### Post by taurus on 2008-12-30
Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by johndoughy on 2008-12-30
Ok it's on another machine, but I did it and the first command was not recognized.  The second provided me with a list of drives, and one seemed to be the one in question.  I will dictate:
"
/dev/sdf2            112g  104g  8.2g  93%  /media/Macintosh HD
"

Is that all you needed?  If you need more, I can try to type the rest up!

---

### Post by johndoughy on 2008-12-30
Ah I dropped the "sudo" part and got this:
cannot open dev/sda
cannot open dev/sdf

---

### Post by johndoughy on 2008-12-30
I think I got it!  Thanks for the tips.

---

