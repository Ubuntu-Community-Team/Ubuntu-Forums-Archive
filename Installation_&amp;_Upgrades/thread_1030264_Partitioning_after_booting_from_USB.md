---
title: "Partitioning after booting from USB"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by knottshawk on 2009-01-04
I have an Eee PC with a 160gb hdd, which is divided equally into a C and D drive with Win XP on the C. I'm wanting to dual boot it and have some questions. When I boot from USB the partitioner tries to install to USB, thinking it's a HDD. So, I'm guessing I'll have to set it up manually but, being a noob, I'm not sure how. I looked at the manual settings and it shows sda1 and sda2 installing to C and D, but I don't know how to tell it to only install to D.

Please give me some guidance and tell me if I'm making any other large mistakes along the way due to my noobishness.

---

### Post by knottshawk on 2009-01-04
I just need help manually partitioning... can't anyone help me with this?

---

### Post by knottshawk on 2009-01-05
Help please?

---

### Post by Bucky Ball on 2009-01-05
If you are getting to the partitioning section of the install, go for manual partitioning and leave the NTFS drive alone, then just install on the D partition. If I am understanding you correctly.

---

### Post by knottshawk on 2009-01-05
Yeah that's right except I need to know HOW. I'm a noob and so I'm a bit lost. If I recall correctly it looks something like this:
sda1 - 6100MB
sda2 - 7100MB

So, I don't know what 'sda1' is, but it seems to be the C drive and 'sda2' is the D drive. How do I tell it where to install?

Sorry for the noobish questions... In the past I've not manually installed.

---

### Post by Bucky Ball on 2009-01-05
That's fine. Are you using the desktop install or the alternate? I guess it would be the alternate for the Eee. A tip: sda1 = hd(0,0), sda2 = hd(0,1)

When you get to the partitioner choose manual install. You don't need to touch anything at this point. Just have a look to make yourself a bit more comfortable and confident. You will be looking at a list of the drives and partitions on your computer, what they are labelled (if anything) and what type they are. You will undoubtledly find that sda1 has the type NTFS. (perhaps the easiest way is to go to disk management in windoze and delete partition D - then you will have an NTFS partition and empty/unused space). Whichever partition is the NTFS partition, that is the Windoze partition. Leave that completely alone, delete the other partition and add three new partitions:

/
/home
/swap

A brief explaination:

/ = the root partition. This is where Ubuntu and just about everything else goes.
/home = your home partition where your data goes, music, pics, anything personal
/swap = name is self explanatory. Should be double the size of your ram but there could be something more specific with the Eee. Have a look around.

Have a good look around in there and you will find these three in the settings. Remember, you can cancel at anytime without making any changes and if you accidentally partition something, you are sure it is on the correct partition so you can go back and change it. You can keep reviewing your partitioning work, deleting and re-partitioning until you are happy with the changes (by which time you will probably be comfortable with partitioning from here on in!) and there you have it. If you are using the Desktop installer, this part is pretty easy and uses the partition manager you will get in Ubuntu, Gparted. If the alternate installer, not much harder, just read everything and keep thinking. The desktop version without the GUI, but does exactly the same thing.


Check out this excellent resource for a guided tour of dual-booting:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Table of contents just down the page a little ...

---

