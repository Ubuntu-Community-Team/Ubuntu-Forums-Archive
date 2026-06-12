---
title: "How replace dll for wine?"
date: 2008-10-20
forum: General Help
---

### Post by flipflopper81 on 2008-10-20
Hi,

I'm on my first few days of using linux / ubuntu-eee and I really like it!  Besides not being able to get on encrypted wireless internet, here is another problem I hope someone can help me with:

I have successfully installed a windows program (called Training Peaks WKO+) using Wine.  The program works but a few things are off and I am told I need to replace the msvcrt.dll.  I downloaded the dll, but when I navigate to the folder usr/lib/wine, I can't do anything to files in that folder.  I can't replace the dll, or do anything in that folder at all actually it looks like.  Any tips?

Also I read in the same place there is a command in wine you can use to see all the DLL's a program is calling up.  Anyone know what that is?  Apparently if I replace all those files the program works much better.  Thanks!

---

### Post by cariboo on 2008-10-20
You have to root to copy files in any directory but your home directory. THe easiest way to do that is to press Alt-F2 and type:

```
gksu nautilus
```

Enter your password when asked. This will open Nautiuls (Places-->Home Folder) as  root. You can now copy, paste, move and delte files in directories owned by root.

Jim

---

### Post by flipflopper81 on 2008-10-20
Thanks!!

If anyone know that trick to list all the dll's that would be appreciated.

This program is heavy on graphing lines and they graphs draw slower than they should but this problem should be corretable w/ new dll's.

More importantly, if anyone has had this problem before, the graphs, instead of using normal numbers for the y axis labels (i.e. 100, 200, 300), many if the numbers are in a wierd long scientific form (i.e. 2700000000000000000000e+02) so the graphs aren't usuable right now, another problem I hope to correct with dll's. (or if anyone else has a suggestion as to why wine is bringing up wierd numbers that would be great.)

---

### Post by flipflopper81 on 2008-10-20
Okay, I was able to fix the problem with the graph lables with the msvcrt.

Now, I have read I just need to replace more dll's that this program is calling up to increase performance.

If anyone knows the command to call up the dll's wine needs for a certain program that would be great.  I have been googling the answer for forever but I can't find it.

---

### Post by scurvy on 2009-12-26
Hey, Looks like you may have figured out how to use Training Peaks' device agent with WINE.  Can you tell me how you found out what dlls to replace?  I can get the agent to run, but I don't see all of the text for buttons and so forth.  Thanks!!

---

