---
title: "Freeing space on 2nd drive..Not"
date: 2008-09-13
forum: General Help
---

### Post by jjocsak on 2008-09-13
I had recently creates an image of my Ubuntu OS on a secondary drive. 

I wanted to use that space for something else so I delete it. 
Now I  do not see it in listed anymore and do not see it in the .trash-0 folder on that drive.

The problem is that the drive is indicating that this space has not freed up. 

This is an 80 gig sata drive with nothing on it but it says that I only have 15 gig left.

How do I clean this drive other than doing a format?

Jeff

---

### Post by javaJake on 2008-09-13
Open Appications -> Accessories -> Disk Usage Analyzer, and click the Scan Filesystem button. This will tell you where all your hard-drive space is getting used.

---

### Post by cariboo on 2008-09-13
Using the gui app will not give a true reading of disk space as it also includes gvfs. The best way to check disk space is to open up a terminal and type:

```
df -h
```

You will get an output which includes a percentage of use. Your trash can is probably hidden. In Nautilus press Ctrl-h to see the hidden files and directories.

---

### Post by jjocsak on 2008-09-13
Disk usage analyzer said I have 19.3 gig left
df -h said I have 16 gig.

I have nothing on the drive anywhere I look even trash.
It's an 80 gig drive.

Jeff

---

### Post by javaJake on 2008-09-13
Jeff, the point of Disk Usage Analyzer isn't to get an accurate GB count of space, but to find out what is using your space the most, and possibly find that missing file (if it's GB's big). That will help you free up your hard drive a bit.

---

### Post by jjocsak on 2008-09-13
I did that and here are the results:

[IMG]http://jjocsak.smugmug.com/photos/371682050_UvSGt-M.jpg[/IMG][IMG]http://jjocsak.smugmug.com/photos/371935920_FxqPR-M.jpg[/IMG][IMG]http://jjocsak.smugmug.com/photos/371682028_LrhF7-M.jpg[/IMG]

---

### Post by mb_webguy on 2008-09-13
Well that's... odd.  Very odd.

Since there's nothing on the partition, reformatting it would be the simple solution.  But I don't have any idea what's taking up your drive space...

---

### Post by jjocsak on 2008-09-15
Yes that is very odd. I did format the drive but I am still curious as to why that happened.

Jeff

---

