---
title: "Update offline repository"
date: 2008-10-14
forum: General Help
---

### Post by brian_c_m on 2008-10-14
Hi all. 

I'm running hardy 8.04 at home without an internet connection so I've been downloading all necessary repo files at work and then putting them in a repo directory on my USB. 

I've got a repo with all files for hardy, hardy-security, hardy-updates. Then I also have a couple of files in the pool directory with all the necessary dependencies etc for whichever apps I want to install. 

Here's my problem. I wanted to install mysql so I downloaded mysql-server-5.0.67 and all it's necessary files but when I got home to install it via apt-get, it said "unable to find /mysql-server-5.0.51 blah blah blah". So my question is, rather than having to download all the 5.0.51 files, where/how do I update my repository so that it knows to install 5.0.67 instead of 5.0.51. 
Is there a way to specify the app's version you'd like to install when using apt-get??

Thanks
Brian

---

### Post by hyper_ch on 2008-10-14
put them into /var/cache/apt/archives

---

### Post by mac9416 on 2009-07-11
You may find [Keryx]("http://keryxproject.org") useful. It will make it ridiculously easy to get .debs and dependencies offline.
The next release will allow you to install software directly from the Keryx interface.

---

### Post by Cheesemill on 2009-07-11
+1 for Keryx

---

