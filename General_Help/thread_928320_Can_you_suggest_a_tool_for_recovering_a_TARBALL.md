---
title: "Can you suggest a tool for recovering a TARBALL?"
date: 2008-09-23
forum: General Help
---

### Post by concord on 2008-09-23
Help!  I have a 17G tarball spanning 5 DVDs and one of the DVDs is bad.  Is there any hope?

I recently backed up a system by spanning several DVDs with a giant tarball (splitting the tarball into 4.7G chunks) using:
```

$ sudo tar -cv -M --tape-length=4928307 --file=concord_home_7_18_08-1.tar /home/concord
```

When prompted I would create the next 4.7G tarball by replying "n" (no) like this:

```
Prepare volume #2 for concord_home_7_18_08-1.tar and hit return: n concord_home_7_18_08-2.tar

```

After I was done creating all the 4.7G sections of the giant tarball I copied each one to a separate DVD.  I was planning to rejoin them all later by copying the files onto new destination and recombining them like this:

```
sudo tar -x -M --file=concord_home_7_18_08-1.tar largefile.tar

Prepare volume #2 for concord_home_7_18_08-1.tar and hit return: n concord_home_7_18_08-2.tar

Prepare volume #2 for concord_home_7_18_08-2.tar and hit return:
```

I was planning to keep going until I got the completed "largefile.tar" then move it to the root "/" directory on the new destination drive and:

```
sudo tar xvf largefile.tar 
```

To extract the files.  Simple, right?  Now one of the DVDs is no good.  Does that mean all the data is gone?  Are there "tools" I can use to extract files from the other (good) sections of the tarball?

Always, always, always check your backup BEFORE you wipe your drive, doh!

Any help is apprecated.  :confused:

---

### Post by andrewc6l on 2008-09-24
You might be able to use the info here:

[http://www.linuxquestions.org/questions/linux-software-2/recovering-files-from-corrupt-tar-archive...-326716/](http://www.linuxquestions.org/questions/linux-software-2/recovering-files-from-corrupt-tar-archive...-326716/)

I'd try both by treating each file individually and also by cating them all together into one big lump and recovering that way.

---

### Post by concord on 2008-10-01
> **andrewc6l said:**
> You might be able to use the info here:

[http://www.linuxquestions.org/questions/linux-software-2/recovering-files-from-corrupt-tar-archive...-326716/](http://www.linuxquestions.org/questions/linux-software-2/recovering-files-from-corrupt-tar-archive...-326716/)

I'd try both by treating each file individually and also by cating them all together into one big lump and recovering that way.


Using the link you provided (cpio) I was able to recover 3/5ths of my data, including pictures of my son as a child which are very important.

Thanks andrewc6l!

---

### Post by Herman on 2008-10-01
> Always, always, always check your backup BEFORE you wipe your drive, doh!If you didn't reformat your hard drive yet you might be able to recover some more of your data by restoring the old partition table with [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

Even if you did already make new file systems, there is an excellent chance you can still recover more of your lost files if you use [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec").

[Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/") has the best collection of software for data recovery. 
Knoppix, GParted Live CD, and System Rescue CD also have TestDisk and PhotoRec.

---

