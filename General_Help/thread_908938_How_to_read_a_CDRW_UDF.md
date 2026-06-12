---
title: "How to read a CDRW UDF"
date: 2008-09-03
forum: General Help
---

### Post by thegitksan on 2008-09-03
Good evening all. To my surprise, I am posting an answer, rather than a question. I originally was having problems finding a simple solution to my laptop (Ubuntu 7.10) reading a CDRW created in WinXP. Searching the forums here, very few threads actually dealt with the problem clearly. Some even suggested it is primarily a problem with the way WinXP or WinVista write the UDF format.

I did find a solution elsewhere, from a link posted by a fellow called billgoldberg, and it turned out to be very simple.

I did not search for solutions for reading DVDs - I specifically wanted to read a CDRW. I have a stack of them I use with Windows all the time. I did not find anything useful for CDRWs, but this link billgoldberg provided worked very well.

Here is the thread:
[http://ubuntuforums.org/showthread.php?t=775775](http://ubuntuforums.org/showthread.php?t=775775)

And here is the external link billgoldberg provided:
[http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/](http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/)

The external link provides much very useful information for understanding the problem. The solution is very quick:
~~~~~~~~~~~~~~~~~~~~~
Ubuntu (and maybe other Linux distros - Debian?) seem to have a problem mounting UDF formatted discs. The solution to this is as simple as editing your /etc/fstab file and restarting. Here are the steps, from the Terminal:
[B]
sudo gedit /etc/fstab[/B]

Here you should see a line similar to this:

**/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto 0 0**

The first part (/dev/scd1) is the device name (could be different with your computer), the second part (/media/cdrom0) is the mount point (where you access the disc in the file system). The third part is the file systems supported. This is where the problem lies. It shows UDF and ISO 9660, but if both are there (which is supposedly ok if comma-separated), then one or the other will not work, depending on the order they are written in the line. So the solution is the change both of those to:

**auto**

Now the edited line will look something like:

**/dev/scd1 /media/cdrom0 auto user,noauto 0 0**

Now save the file and restart.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

It worked quickly, cleanly, and with no re-compiling anything.

I have not tested writing anything to the CDRW disk yet. That's another adventure.

Russell in Canada

---

