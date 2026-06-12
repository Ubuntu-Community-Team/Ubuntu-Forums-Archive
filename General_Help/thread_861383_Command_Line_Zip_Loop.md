---
title: "Command Line Zip Loop"
date: 2008-07-16
forum: General Help
---

### Post by phaedo5 on 2008-07-16
I have a directory full of files that I want to zip (not tar).  I want to find all the jpgs and zip each one individually with the original filename and zip extension.
 

for file in `find . -type f -name "*.jpg"`; do echo $file; done
-I can get that far. 

zip archive test.jpg 
-And I can get that far.  


I just don't know how to combine them.

If I have test1.jpg, test2.jpg...
I want test1.zip, test2.zip...


Can anyone help me with this?

---

### Post by dracayr on 2008-07-16
replace archive with

`basename $file .jpg`

dracayr

---

### Post by baju on 2008-07-16
be carefull, since list works recursivly, you should not place subfolder in that directory or use ls instead.

---

### Post by phaedo5 on 2008-07-16
Awesome.  Thank you!

---

