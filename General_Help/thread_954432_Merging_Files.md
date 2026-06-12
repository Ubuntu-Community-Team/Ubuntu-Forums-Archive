---
title: "Merging Files"
date: 2008-10-21
forum: General Help
---

### Post by Tupopoflungo on 2008-10-21
Hi, Im sort of new to ubuntu, and I am trying to figure out how to merge a TV shows folder I have on my laptop, with one on my portable hard drive, without having to pick and sort the 20+ tv shows I download a week, and without having to delete the folder from my portable drive, and recopy the 25g or whatever that I have on my computer...


Anyone know how I could do this, so as to keep my drive as up to date as possible, without it consuming 3 hours of my day?

---

### Post by cmnorton on 2008-10-21
1) cat both files into a temp file.

2) Sort the temp file using sort. You would do this to obtain consecutive duplicate lines.

3) Use sed to remove the duplicates:

This web site has some interesting sed "one-liners":

[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

Edit:
----------------------
You can also remove the duplicate lines with uniq.

---

### Post by Tupopoflungo on 2008-10-22
> **cmnorton said:**
> 1) cat both files into a temp file.

2) Sort the temp file using sort. You would do this to obtain consecutive duplicate lines.

3) Use sed to remove the duplicates:

This web site has some interesting sed "one-liners":

[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

Edit:
----------------------
You can also remove the duplicate lines with uniq.



I have no idea what any of this means...

---

### Post by cmnorton on 2008-10-22
Assuming the two files are schedule_file1 and schedule_file2, and you are at an X term (command line)

cat schedule_file1 > temp_file
cat schedule_file2 >> temp_file

sort temp_file > sorted_temp_file

uniq sorted_temp_file > final_schedule_file

---

### Post by Tupopoflungo on 2008-10-23
> **cmnorton said:**
> Assuming the two files are schedule_file1 and schedule_file2, and you are at an X term (command line)

cat schedule_file1 > temp_file
cat schedule_file2 >> temp_file

sort temp_file > sorted_temp_file

uniq sorted_temp_file > final_schedule_file


um...What?  I'm sorry, I have no idea what this means...perhaps I didn't explain my problem correctly.

I store my downloaded TV shows, on both my internal, and an external hard drive.  Each day, I download new shows, and then individually click and drag them to sort them on my internal hard drive.  Then, I plug my external drive in, and have to go through each folder and drag and drop the new files to the external drive.  I am trying to figure out a way that I can get the computer to see which files I'm dropping onto the external, and skip over ones that are already there...

---

### Post by Liviu-Theodor on 2008-10-23
Have you tried the [FONT="Courier New"]Unison[/FONT] package?

---

### Post by kpkeerthi on 2008-10-23
You could use rsync. If you want to sync two folder, you would just do:
```

rsync -a source/ destination/

```

You could also try grsync, if you prefer a GUI.

---

