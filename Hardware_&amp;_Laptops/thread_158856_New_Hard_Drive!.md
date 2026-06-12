---
title: "New Hard Drive!"
date: 2006-04-11
forum: Hardware &amp; Laptops
---

### Post by tux-curious on 2006-04-11
I got a new Celeron era Fujitsu HD and have it installed, but I need to reformat it from the windows setting it came with.

Are there any ways I can format it from Ubuntu?

-thx

---

### Post by gabruo on 2006-04-11
The ubuntu cd or ISO will format it for you during partitioning.

---

### Post by tux-curious on 2006-04-11
[QUOTE=gabruo]The ubuntu cd or ISO will format it for you during partitioning.[/QUOTE]

But that would mean I would have to reinstall ubuntu and lose all my files, right?

---

### Post by taurus on 2006-04-11
You will certainly lose your data on that drive if you want to reformat it!!!  So, back it up first before you do any formatting, whether it's in Ubuntu or Windows...

---

### Post by tux-curious on 2006-04-11
Ok, I don't mind losing information on the new, secondary drive, but I don't want to have to reinstall Ubuntu, I already have it installed on my old drive.

I formatted the new drive with the install cd, and it is save as an ext 3 partition, with a /home classification.

When I log back on it doesn't see the newly formatted drive.

---

### Post by taurus on 2006-04-11
Let me get this right.  You want to move your current /home to the new harddrive!  Well, you may want to boot into single user mode or recovery mode from GRUB menu.  Then, mount the new second harddrive somewhere and copy everything from current /home to the second harddrive.  Then, modify /etc/fstab to reflect the new mount point for the "new" home.
```

mkdir /mnt/second
mount -t ext3 /dev/hdb1 /mnt/second
mkdir /mnt/second/home
cp -R /home/* /mnt/second/home
nano /etc/fstab
(either modify the entry for /home if you have one or include this one in there...)
/dev/hdb1  /home  ext3  defaults  1 1
shutdown -r now

```

---

### Post by tux-curious on 2006-04-11
I want the second hard drive for additional storage, so either as a new "home" or added onto my original one.

Is this possible? Are there maybe tutorials?

I am running out of space on my first hd so I bought and installed a new one, but I can't get at the storage space.

I am fairly green, I've been using linux for the last 8 months, Ubuntu for the last 7, but I've done a decent job of avoiding things like GRUB, not really sure how to get into it (unless thats just another term for terminal).

---

### Post by taurus on 2006-04-11
The directions that I gave you will move the current /home to the new harddrive, freeing some space on your first harddrive!  Isn't that what you want to do?

---

### Post by tux-curious on 2006-04-11
um, not really. 

Is there no way I can use both drives for the storage of personal files?

I have a total of about 9gig for my current /home folder and the new drive is only 10.8gig so I would only gain about two gig by moving my /home folder and wouldn't get much use out of the remaining space on the first drive (unless I could use that too for my personal files?).

---

### Post by taurus on 2006-04-11
Well, in that case, open a terminal with Applications -> Accessories -> Terminal and type
```

sudo mkdir /personal
sudo gedit /etc/fstab
(Now, add the following line at the end of /etc/fstab...)
/dev/hdb1  /personal  ext3  defaults,umask=0000  0  0

```
Save it and mount the new drive with
```

sudo mount -a

```
Now, your new drive should appear as /personal and everybody can write to it!  Is that what you are looking for?  :)

---

### Post by tux-curious on 2006-04-11
Yup, I'm pretty sure that's exactly what I want, now to replace my home folder back where it was, lol

People here are so nice, I totally would have been flamed most places.

thanks!:)

---

### Post by taurus on 2006-04-12
Finally, came up with something you want!  :)   Just leave your /home as it and mount the second harddrive, assuming it's /dev/hdb1, to /personal and that would give you some extra storage room.  

Now, it's bedtime for me...  ;)

---

