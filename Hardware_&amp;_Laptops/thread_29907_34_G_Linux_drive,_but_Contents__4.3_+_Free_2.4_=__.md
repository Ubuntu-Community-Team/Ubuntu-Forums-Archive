---
title: "34 G Linux drive, but Contents  4.3 + Free 2.4 =  6.7"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by dishbert on 2005-04-26
When I installed Warty in the fall, it created it;s own 34 Gig partition on my 80 Gig drive (with XP using the rest).  Now file manager says there is only 2.4 Gig free, even though "Filesytem" properties shows only 4.3 Gig of contents.

What am I not understanding?

---

### Post by GrumpySmurf on 2005-04-26
What is the output of the "df -H" command?

---

### Post by dishbert on 2005-04-27
That's a command I was looking for!

df -H returns 31 G total on Linux side, 27.6 used, and 2.7 available.

But I still can't figure out what is using all the disk space.  I look at "Properties" for all the suspect directories, and none have any where close that amount data.  I have recorded a bunch of video, but I always move it to a DVD, then delete off the hard drive.

Is there a command, or app, that will show me the size of the files in each directory?

---

### Post by GrumpySmurf on 2005-05-02
Once again, I delay in responding.  Sorry about that.

You can use the 'du' command to determine which files or directories are using the most space on your system.  I find the -s and -h (or -H) options to be quite handy.

```
$ man du
...
       -h, --human-readable
              print sizes in human readable format (e.g., 1K 234M 2G)

       -H, --si
              likewise, but use powers of 1000 not 1024

       -s, --summarize
              display only a total for each argument
...

```

---

### Post by dishbert on 2005-10-16
In the end, I was down to only 1.2 G left, and no command could seem to produce a list that showed where all the bytes had gone.

So........I formated the Linux partition and loaded 5.10 rc1, and now I'm back to having 26 G to work with.  I had another problem I couldn't solve as well, so it made sense to me to start fresh.

---

