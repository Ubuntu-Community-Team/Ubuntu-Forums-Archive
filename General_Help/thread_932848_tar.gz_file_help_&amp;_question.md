---
title: "tar.gz file help &amp; question"
date: 2008-09-28
forum: General Help
---

### Post by tlovaj on 2008-09-28
Hello guys, I ran into a problem after emailing myself a file from school.  I sent it as a "tar.gz" file and when I tried to unzip it on my new dual boot ubuntu/xp laptop *HURRAY!!!* I got the "not a tar archive" error.  After doing some research I found out I had to gzip it and then tar -xf it.  Just wondering how this all works, since I'm able to open up tar.gz files at school with no problems.  Is there some program that I still have to install?  Thanks!

---

### Post by taladan on 2008-09-28
first type:

```
file <whatever>.tar.gz
```

that should tell you what type of file it is, whether it's a tar file or a gzip file.

In the future if you're wanting to create tar archives, the easiest way is:

```
tar -czf <filename>.tar.gz <directory_or_file_you_want_archived>
```

This calls tar to Create,gZip,File an archive named <filename>.tar.gz from the directory_or_file_you_want_archived

Hope this helps,

Tal

---

### Post by raul_ on 2008-09-28
you can also install and use a program called atool.

atool is a wrapper for pretty much all the common compressing utilities, and all you have to do is use for example

atool -x file.zip

or

atool -x file.7z

pretty handy tool, IMO. you can install with

sudo aptitude install atool

---

### Post by tlovaj on 2008-09-30
i use this to zip a file 

```
    tar -cvzf <filename>.tar.gz <directory>


```

Just wondering why I can't double click my tar.gz files and get it to open on my laptop, but I can do it at school.  Thanks.

---

