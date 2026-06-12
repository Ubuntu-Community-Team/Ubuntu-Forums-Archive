---
title: "Accessing linux files from windows"
date: 2008-10-27
forum: General Help
---

### Post by valikor on 2008-10-27
Hey folks,

I installed ubuntu from wubi, and am wondering how to access my linux files from windows XP? I'm currently having trouble getting ubuntu to boot and need to get my files (I'm not worried about fixing this problem, because I am going to install the new version of ubuntu when it comes out in a few days anyways).

I have tried Explore2fs (as per the recommendation I read in a previous post on this topic), but it doesn't seem to work.

Within my ubuntu folder, there is a /disks/ subfolder, which I thought might contain my files. But, XP says this directory is inaccessible.

Suggestions?

Thanks!

David

---

### Post by Orlsend on 2008-10-27
Hey I think I got what you need:

[I]There are a few Windows applications that can mount ext2-based file systems. See for instance:

    *

      [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
    *

      [http://www.fs-driver.org/](http://www.fs-driver.org/) 

The relevant Wubi files you need to access are located under C:\ubuntu\disks\[/I]

Theres the Wubi guide where it has about everything:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Thanks for Using Wubi :D

---

### Post by valikor on 2008-10-28
What if C:\ubuntu\disks does not exist? 

Earlier (when I first posted a few hours ago) the directory was present, but couldn't be browsed by windows (said it was inaccesible). Not sure what happened between now and then... though I did run a file recovery utility (unsuccessfully). 

--David

---

### Post by valikor on 2008-10-28
And I have explore2fs--but when I open it, nothing happens. It doesn't identify any relevant filesystems.

---

### Post by Orlsend on 2008-10-28
Make sure they are not hiden files and make sure you are the admin in Windows.

---

