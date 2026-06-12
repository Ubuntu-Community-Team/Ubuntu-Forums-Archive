---
title: "ubuntu install"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by kilbride on 2009-07-03
can any one help ? i cant install ubuntu on to HP compaq nx 7300 laptop iv tryed wubi and a few others. any ideas ?):P

i get this message when i try to install

C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\zepmozqd.iso.part could not be saved, because the source file could not be read.

---

### Post by ptn107 on 2009-07-03
If you wish, you can delete everything in that folder as it's just temp space.  From windows [Vista] click Start -> All Programs -> Accessories -> Command Prompt and type the following:
```
del C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\*.* /F /S /Q
```

Then try the Wubi install again.

* If you need an explanation of the command:
'del' is the delete command
'C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\*.*' is the path to the folder with the stuff your deleting, note *.* means all filenames with any file extension
'/F' force-deletes read only files
'/S' tells del to go into any subfolders of this folder
'/Q' suppresses delete confimation

---

### Post by kilbride on 2009-07-03
hi ya 
reloaded ubuntu  NOW  asking me which program i want to open with ?
1 exploer
2 word pad
3 adobe
etc
i think theres a program missing ):P

---

### Post by kilbride on 2009-07-05
its ok now i installed then re installed wubi  now all working 

thanks

---

