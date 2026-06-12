---
title: "I burn a data dvd in k3b and get a &quot;Blank DVD+R DL Disc&quot;"
date: 2008-09-06
forum: General Help
---

### Post by karnakdk on 2008-09-06
Hi,

When I burn a data dvd project in k3b using a dual layer DVD+R, everything goes well, I get no errors, but when I put the dvd in the drive, Ubuntu recognizes it as a "Blank DVD+R DL Disc". Yes, I have a dual layer dvd burner, and the burning process looks "normal"... It takes a lot of time...

Any ideas of what the problem is? I tried searching for it in Google and here in Ubuntu Forums, and didn't find any similar problem.

I have Ubuntu Hardy Heron, K3B 1.0.4 (gnome)

Thanks in advance

---

### Post by Shazaam on 2008-09-06
Did you "name" the disk/project? And is there anything on it?

---

### Post by karnakdk on 2008-09-06
oh, please...
Yes. I tried twice... in the first time I had 8 GB of data... and in the second I put 7.5 GB only, because I thought the problem could be the 8 GB... and the name was "Backup 01" LOL

---

### Post by karnakdk on 2008-09-06
In the first time I burnt with Rock Ridge + Joliet, and in the second, Rock Ridge only. I got the same with both discs, "Blank DVD+R DL Disc". I tried to read the Joliet one in Windoze and it appeared empty too.

---

### Post by Shazaam on 2008-09-06
> **karnakdk said:**
> oh, please...
Yes. I tried twice... in the first time I had 8 GB of data... and in the second I put 7.5 GB only, because I thought the problem could be the 8 GB... and the name was "Backup 01" LOL

What I am asking is when it mounts and shows up as "Blank DVD+R DL Disc" does nautilus show any files on the disk? Sorry for the confusion.

---

### Post by karnakdk on 2008-09-06
No, it opens the CD/DVD Creator folder (with nothing in it).

---

### Post by karnakdk on 2008-09-06
dmesg|tail shows

[ 3682.975238] cdrom: This disc doesn't have any tracks I recognize!

when I put the disc in the drive.

---

### Post by stinger30au on 2008-09-06
i have never had a problem with k3b buring data for me.
i leave it do burn with default settings and i just double checked my settings now

when u hit burn go to the box that says file system and make sure it is set to linux+unix / windows file system

and it should be ok

---

### Post by Shazaam on 2008-09-06
What about this (sounds similar)...
[http://ubuntuforums.org/showthread.php?t=725048](http://ubuntuforums.org/showthread.php?t=725048)

---

### Post by karnakdk on 2008-09-06
thank you Shazaam.

Since I don't feel like switching to Windoze to fix this (and change the drive's firmware too), i'll have to get some new media to see whether that's in fact the problem.

I'll post the results here in the (maybe not-so-near) future.

---

