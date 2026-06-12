---
title: "Download Entire 7.04 latest repositories"
date: 2008-09-30
forum: General Help
---

### Post by Trzone on 2008-09-30
Since 7.04 is getting closer to the end of its support period, i am wondering if there is a way to get the entire repository from online, and keep it just in case i decide that i want to go back to 7.04

---

### Post by kk0sse54 on 2008-09-30
> **Trzone said:**
> Since 7.04 is getting closer to the end of its support period, i am wondering if there is a way to get the entire repository from online, and keep it just in case i decide that i want to go back to 7.04

Why would you want to go back when there will soon be three support Ubuntu OS's to choose from. As for downloading the entire repo it's very very large and will take up a lot of space so I wouldn't recommend it. But if you insist all the repos are kept here [http://ww.us.archive.ubuntu.com/](http://ww.us.archive.ubuntu.com/) and it looks like it has everything back to dapper. Goodluck ;)

Edit: Forgot to mention that OSDisc.com offers the entire Ubuntu repo for about $30

---

### Post by Trzone on 2008-10-01
Well i used the command wget -r [http://ww.us.archive.ubuntu.com/ubuntu/dists/feisty/](http://ww.us.archive.ubuntu.com/ubuntu/dists/feisty/)   and that seems to have worked quite well.  I still don't have some of the issues fixed from feisty, known as sound problems ([http://ubuntuforums.org/showthread.php?p=5871046#post5871046](http://ubuntuforums.org/showthread.php?p=5871046#post5871046))   Oh, and well i feel that since my computer is 7 years old, feisty was the best version, and i would love to be able to go back to it...how long are the updates kept? and what exactly does "supported" until this date mean? does it mean no new updates or..?

---

### Post by cariboo on 2008-10-01
A much better way to mirror a repository is to use apt-mirror, this will create an exact duplicate of the repository, with all the files being in the right place, so that you can use apt to install packages.

Jim

---

### Post by CREEPING DEATH on 2008-10-01
I think you could just jigdo a DVD image...

CD

---

