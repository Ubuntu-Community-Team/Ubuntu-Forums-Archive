---
title: "[SOLVED] Java not downloading"
date: 2008-10-23
forum: General Help
---

### Post by cromertech on 2008-10-23
Been trying to install Java on 8.04 server 64bit on amd through vmware but I get the following error
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse sun-java6-bin 6-07-3ubuntu2
  Connection failed

It will install everything except the sun-java packages which it can't download.

Is there a possible solution for this?:confused:

---

### Post by kpkeerthi on 2008-10-23
May be the US mirror you are connecting to is down. You can switch to main servers by removing the word **us.** from the URLs in all the lines in your apt sources.list file and try again.

---

### Post by cromertech on 2008-10-23
Thanks for your quick reply. I'm not having any problem downloading any other files from this server. I can browse to the sun-java6 files in firefox and download manually but i then get hassles with dependencies that i could really do without.

---

### Post by cromertech on 2008-10-24
Ok solved this one downloaded all depedant packages and installed with dpkg

---

### Post by jespdj on 2008-10-24
You can mark a thread as solved by clicking "Thread Tools" on the top right of the page and selecting "Mark as Solved".

---

### Post by matey3 on 2008-10-24
I put that address in my browser and got errors, oops I got errors also using wget? at first it said it was OK then errors came?


why dont you use this link and pick it manually?

[http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/)

---

