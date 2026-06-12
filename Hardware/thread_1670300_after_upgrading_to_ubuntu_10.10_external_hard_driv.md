---
title: "after upgrading to ubuntu 10.10 external hard drive no longer works"
date: 2011-01-18
forum: Hardware
---

### Post by bmuir5 on 2011-01-18
Last week, I upgraded from ubuntu 10.04 to ubuntu 10.10.  Most things are working alright but I can't write to my external hard drive anymore, it was working fine with ubuntu 10.04.  Trying to copy a file to the external hard drive, which automounts when I plug it in, gives an error:

bmuir@bmuir-laptop:/media/329C-E04A/movies$ cp /home/bmuir/Downloads/Knight.And.Day.2010.avi ./
cp: writing `./Knight.And.Day.2010.avi': Input/output error

Trying it in the file browser does the same thing.  Trying to simply create a directory also gives an error:

bmuir@bmuir-laptop:/media/329C-E04A/movies$ mkdir temp
mkdir: cannot create directory `temp': Input/output error

If I just try to use a file, like watch a movie from the external hard drive, I can do that with no problems.

I've been using ubuntu for a few years now and love it but I need my hard drive to work.  If any more information is required, let me know.  Any ideas?

---

### Post by bmuir5 on 2011-01-26
No luck yet.  Formatting the hd tonight.

---

### Post by powerslave12r on 2011-03-06
Did it work?

---

### Post by bmuir5 on 2011-03-06
Yes, now that I formatted it, it works fine.

---

### Post by fjgaude on 2011-03-06
Likely the issue was one of permissions. If you would have noticed in Nautilus Permissions would have shown "root" access only.

In reformatting using your log-in name likely made the drive open to you for both reading and writing.

Just a thought.

---

### Post by bmuir5 on 2011-03-07
I doubt it, I checked ownership and permissions from the terminal (several times - this is the first thing I thought of) before formatting.  Also, I was able to copy files from the hd to my computer but not the other way around.  Besides, why would upgrading ubuntu change permissions or ownership?

---

