---
title: "I want to install 9.04 in an existing partion. HOWTO?"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by penguinv on 2009-05-03
I want to install 9.04 in an already existing partition.
How do I do this?

Here's the overview of my problem. I started out wanting to save my user and data, (pics, docs, etc) not any programs, applications, in my new installation. I posted here and was told that was impossible I had to back it up elsewhere.

Then I stepped though the installation to see what happens:

Re: Will 9.04 reformat my drive? Another solution possiblility?
New solution part:

1. I found another solution. Had trouble with it and am going to post that separately. *(HERE, this is that.)*

Ubuntu said it can split about 3.2G off my 7.04 partition and install 8,04 in that. Wow, I think, that will do it for me.

(for the meanwhile. It is hard-to-believe that Ubuntu cannot copy a user account and all its files from anther Ubuntu installation. And I want that capability.)

But Ubuntu had disk problems of some kind. The error message seemed mixed up between the CD/drive? being at fault or my hard drive being at fault.
[INDENT]a. if it is referring to the CD, but note that the CD passed the hash test. I think the CD is good.
b. if it is referring to the hard drive, couldn't I do a scandisk or a checkdisk and mask the bad sectors. How much did it try?[/INDENT]

And last, when I try again to install I see that the just made 3.2G sector is considered taken and it wont give me an option to reinstall on that partition but wants to take out another 3.2 chunk of hard drive. Arg. 

-----
I found out about [FONT="Courier New"]GPARTED[/FONT] and am looking at this. Somehow I need to be able to tell 9.04 to install there.

---

### Post by upchucky on 2009-05-03
the reason Ubuntu can not be taken from another install is simply that ubuntu is custom built for each and every machine it is installed on, that is to say that you can take an image of ubuntu from an identical machine that it was installed with the same options and restore that image to another machine as long as it is identical.

If ubuntu was designed to be installed on as many machines as possible without a custom install, it would become a very bloated and slow operating system.

now for the partitions, post them here and indicate the desired results.

---

### Post by rbanavara on 2009-05-03
I have not used Jaunty, but generally its like this:

you need a separate partition for linux to reside. The way you partition a room by having a barrier and resize the space by moving it along, you will parttion HDD in the same way.

gparted is a nice tool to do it manually. In most cases, the whole of the HDD is occupied by a single resident, Windows. You need to make space for linux by resizing it. You can shrink the windows partition with gparted and make space for linux. 

Once you have prepared the Disk, you can go for install and select use the free space option (not sure if this the exact name).

Enough of story...! How do you identify your HDD? normally it will be either named as /dev/sd[a-z] or /dev/hd[a-z] (one of a to z).

---

