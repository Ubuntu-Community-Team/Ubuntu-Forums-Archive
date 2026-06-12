---
title: "adding extra hard drive"
date: 2006-04-20
forum: Hardware &amp; Laptops
---

### Post by donnysrx on 2006-04-20
hi

I got a breezy box, I got a 80 gb ide drive I've just put in it for extra storage.

Now under admin drop down menu there is a package 'disks',when I click on this it opens and then just hangs not highlighted, I was under the assumption that I could use this to format the new drive(that has come out of a windows PC) and mount it.

So do I use the terminal instead,has this 'disks package' packed up? :)

if I use the terminal whats the sequence of commands pls?

TIA

---

### Post by Jose Catre-Vandis on 2006-04-20
You should find your answers here:

[https://wiki.ubuntu.com/InstallingANewHardDrive](https://wiki.ubuntu.com/InstallingANewHardDrive)

---

### Post by donnysrx on 2006-04-20
hi thx for that,got it all done.

apart from permissions,can I do the permissions in the fstab file,tried a few conbinations of what is already there but no joy. I cant write to it.

also the drive is quite a bit smaller than 80 gig, I know they are not exact but it showed at 67 gb I'm sure it was around the mid seventies in the windows PC,there was a few gb of windows files on the drive when i put it in, but i did delete all the partitions before formatting it just now.

TIA

---

### Post by donnysrx on 2006-04-20
chmod -R 777 /home/<username>/<foldername>

 -R this changes all the chrildren folders within as well, which is handy while your working with them

---

