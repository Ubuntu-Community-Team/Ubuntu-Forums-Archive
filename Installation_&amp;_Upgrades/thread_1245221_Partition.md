---
title: "Partition"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by mercules2178 on 2009-08-20
I have formatted my drive to have "/" and "home" on different partitions.
What are the advantages of this vs just installing all to one partition?

---

### Post by mibadt on 2009-08-20
Well done!
With a separate /home partition, you can (in the future) do a fresh install (of newer of other distribution) and maintain all you data (as long as you remember NOT to format /home during the fresh install).

Best regards,

Michael Badt

---

### Post by mercules2178 on 2009-08-20
When I need to do a fresh install how do I install without it creating a new home directory?

---

### Post by Bartender on 2009-08-20
I think probably the biggest single advantage is that you can install a newer version of Ubuntu right over the / partition, and leave the /home partition untouched.

There are a few things you must know to do this correctly.  Let's jump ahead to late fall of this year.  You have an Ubuntu 9.10 install CD in the optical drive.  You must use the same username and password as was used previously.  If you do not Ubuntu will set up another /home partition inside of the / partition with your new username.  

I did that once or twice and had to start over again.

When you get to the partitioner segment of installation, you'll have to use the "manual" option.  Mount / to the same partition as it was before, and make sure to click that little "format" box.  Mount /home to the same partition as before, and make sure the "format" box is NOT clicked on.  You do not want to tell the installer to format /home.

When you're done, you'll have Ubuntu 9.10 on / partition, and everything that was in /home will be untouched.  One of the cool things about this is many (all?) of your settings, such as desktop wallpaper and etc. will come right on over to the new installation.

---

### Post by mercules2178 on 2009-08-20
You gave me an explanation that I needed, Bartender. I have asked many questions and have never recieved an answer that just explained it without someone pointing me in another direction or an answer that I did not understand, thank you! I am glad that I am able to reinstall or upgrade in this manner. It is a great idea and something winblows does not do for me without great pain.

---

### Post by ronparent on 2009-08-20
Great answer Bartender. You clearly explained away some of my own nagging doubts on what would happen to /home if for any reason / had to be reloaded.

---

### Post by Bartender on 2009-08-20
Well, thanks, guys, I get a kick out of helping out when I can.

If you've got access to YouTube or similar, pull up a couple of videos showing manual partitioning.  It's not hard.  I can buzz thru that section now in a couple of minutes.  But some of the concepts, such as "mounting" a directory, seem very weird at first.

If you've got a spare HDD laying around, I'd strongly suggest practicing once or twice!

---

