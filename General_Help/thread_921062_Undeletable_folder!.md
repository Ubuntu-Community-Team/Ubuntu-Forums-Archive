---
title: "Undeletable folder!?"
date: 2008-09-15
forum: General Help
---

### Post by rbolio on 2008-09-15
Hi! 

This is kind of a funny question, I think... heres the deal,  For some reason (seriously unknown)  there is a folder called "documents" in my trash.

-cant delete it- 

The strange thing is that this documents folder goes down over 400 levels (yes, i counted them...) [too much free time >.<]   anyways....

I mean, its not like it bothers me or anything....but its always there! AH! help!

---

### Post by Unanimated on 2008-09-15
```
gksu nautilus
```
If that doesn't work (it doesn't for me), go [here]("http://www.psychocats.net/ubuntu/") and follow the script to install Thunar. If you had to do that, type
```
gksu thunar
```
(Note: Type these in alt+f2)
Then, go to /home/NAME/(ctrl+h).local/share/Trash/files
Delete the folder, then click Trash on the side (if using Thunar), then delete the files from there. If you managed to get Nautilus to work, then go [here]("http://ubuntuforums.org/showthread.php?t=898573") and follow the instructions.

---

### Post by iaculallad on 2008-09-15
Had you tried using the terminal to delete the folder?

```
sudo rm -r ~/.local/share/Trash/files/*
```

---

### Post by rbolio on 2008-09-17
Thanks for the help, but even with sudo thunar, it wont work the  Documents undeletable folder is still there =X

---

### Post by rbolio on 2008-09-17
o wait woot!; iaculallad that worked XD

---

