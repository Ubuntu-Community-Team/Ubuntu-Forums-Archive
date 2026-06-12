---
title: "Toshiba Satellite A10"
date: 2004-11-01
forum: Hardware &amp; Laptops
---

### Post by Seti on 2004-11-01
I just don't know how to go about solving this problem; I've googled around, can't find much that helps. I have installed Ubuntu on a Toshiba Satellite A10 with a 30GB HDD. Ubuntu is great and works nicely. However, on boot I am getting "errors found on /dev/hda1, filesystem check forced...." then it goes through checking the filesystem. Usually this fails and it then starts telling me about I/O errors. Any ideas??

---

### Post by Fred_og_ro on 2004-11-05
Not sure this has anything to do with what you're experiencing...but its probably worth a try.

Check out this thread over at OSNews: [Six Weeks with Ubuntu Linux](http://www.osnews.com/comment.php?news_id=8754) 

There's some comments in there on using ext3 filesystem vs reiserfs...maybe that'll help you

---

### Post by Seti on 2004-11-06
Thanks for your reply! I edited /etc/default/rcS so that FSCKFIX=yes. Going to see if that fixes it. Otherwise this fsck keeps happening. Going to learn how to use fsck though so that I can run it manually  from time to time.

---

