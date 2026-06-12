---
title: "Dual boot with two physical drives?"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by Texne on 2009-07-02
I would like to set up my Vista computer to dual boot Ubuntu.  I have a separate physical hard drive that I haven't been using.  Is there any reason I can't install the Ubuntu on that drive?  Would there be a problem with the boot loader recognizing that another OS is on a separate physical hard drive?

---

### Post by merlinus on 2009-07-02
Most likely not, but it can be fixed if there are problems.  Just be sure that the vista hdd is set to boot first in bios.

---

### Post by lindsay7 on 2009-07-02
There should be no problem doing this. Just choose the manual option for the installation and pick the disk drive that is not being used.

Set up and format a partition with a mount point of / for the system and a partition for /home (this is where you can keep you data, pictures, music, etc. You can also choose a /swap partition.  The / partition only needs to be 10 to 15 gigs of so and the /home can be as large as you want. The swap only needs to be 2 to 5 gigs or about two times your ram size. You may also want to set up an extra partition  just to have an extra place to put stuff.

Doing the above will let you upgrade to future Ubuntu versions and only install the program data on the / partition. When you do this you just choose to format and install the new version on the / partition and you do not choose to format any of the other partitons. You can choose how to format the / and /home partitons as ext3 or ext4 the newer ext4 is said to be faster.

---

### Post by Mark Phelps on 2009-07-03
If it's really important to you to retain Vista in its corrent state, I recommend that you do the following:
1) Disconnect the Vista drive
2) Boot from an Ubuntu CD and install it to the second drive
3) Reconnect the Vista drive but continue to boot from the Ubuntu drive
4) Add a stanza to the menu.lst file on the Ubuntu drive to allow booting into Vista.

---

### Post by ronparent on 2009-07-03
Or, leaving vista in place, change the boot order in biosto your set your second drive as boot. Boot to the ubuntu live cd and install it to the second drive. Just be very careful you don't select the  wrong drive to install to and overwrite your vista. The advantage of this approach is that you leave the vista drive unaltered (including the mbr) and have vista automatically included in the grub boot menu without further intervention. Also, at any time, you can boot back to the vista by merely changing the boot order in bios (handy if somehow the new install is screwed up, you still have access to you computer). 

What you want is doable and either approach is valid as long as it meets you needs. Mark's approach is safer to protect the vista install but with more likely hood of you having to return for more help to setup grub to boot windows.

---

### Post by Mark Phelps on 2009-07-04
> **ronparent said:**
> Just be very careful you don't select the  wrong drive to install to and overwrite your vista.

From the posts, this "mistake" happens more often that we would otherwise guess.

It's a lot easier to then add a few lines to a config file than to figure out how to get their entire investment in Vista back.

Which ... is why I recommend the disconnect-prior-to-install approach.

---

