---
title: "I can Finally write to my second Hard Drive"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by RMJ1940 on 2008-02-04
Finally I have my second hard drive usable.  I don’t know why Ubuntu sets up the internal hard drives with “Root” as the owner and group but it sure caused me a headache for over a year.  I would install Ubuntu / Kubuntu and try to get them running.  But always ran into the same thing, I couldn’t write to my second hard drive (which is a SATA).  After a while I would take Ubuntu back out and install Windows.  That went on for over a year.  Now with Vista, I have to learn to use Linux and I like Kubuntu the best of anything I tried.  I had the same problem as before.

I checked the Ubuntu forum and Googled like mad but none of the things that helped other people worked for me.  Changing the fstab file didn’t help and chown just plain did nothing.  I even set up so I could log in as Root and worked from there.  That didn’t help either.  After removing Ubuntu about 4 times and even trying Open Suse twice (which works fine by the way) I finally found something that worked.

I found “The Smorgasbord” at  [http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/) and it had what I had missed elsewhere.  Now it works fine.  Thank You John Pratt.

The key seems to be; “Next, here’s one of the most important things….and something that I didn’t find in any of the articles on the web when I was trying to figure out how to do this. You have to make the mount point directory ‘writable’. In other words, you have to give it writable permissions. They have to be world-writable permissions since you aren’t a member of the ‘root’ group in which all mount points are owned.
So, now you want to run the following command (again substituting my mount point name for yours):
$ chmod 777 /media/linuxstore”

I figure since I had so much trouble, other people probably do to so I wanted to leave this information.  Sorry about it being so long.
Have A Great Day.  I will not that I have Kubuntu up and running right.
Bob Jones

---

