---
title: "Deleting 9.04 and installing 9.10"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by irohaphoto on 2009-10-26
It appears that this has not been posted.
I installed 9.04 but I cannot get the wired LAN to work on my KAV60 Acer Aspire one (dual boot with XP) so in case I never get online with 9.04 I wonder how should I go about un installing 9.04?
Or is it possible to just insert a 9.10 DVD and write right over the top of 9.04?

---

### Post by Mark Phelps on 2009-10-26
Ubuntu 9.10 uses a new GRUB -- GRUB2 -- which it will not install if it finds 9.04 already there.  So, if you don't need anything from 9.04, boot from an Ubuntu LiveCD, start Partition Editor, and remove the partitions.  When you boot from the 9.10 LiveCD, just install anew.

---

### Post by raymondh on 2009-10-26
+1 on Mark's suggestion.  This is assuming you do NOT have a wubi install and Ubuntu is in its' own partition.

You can also write on "top" of your 9.04 install.

- Boot into the Karmic liveCD
- in step 4, select manual
- click to highlight your existing ubuntu installation
- click EDIT > USE > select mountpoint > select filesystem (ext3 or ext4) and format
- continue with the install process.  GRUB2 ought to overwrite the old jaunty GRUB.

Just a suggestion ..... since you have a liveCD of Karmic, why not go live session first (TRY UBUNTU WITHOUT ANY CHANGES) and see if Karmic plays well with your system (i.e. wifi, Fkeys, sound, etc) ..... then install if ok.

Re-reading your initial post .... just in case you have a WUBI install, you delete ubuntu from within windows using the add/remove function in control panel.  You will also have to manually edit the boot.ini file to delete the WUBI related line (only the wubi-related line).  Unfortunately, I still don't know how Karmic plays with a WUBI-install.

Back-up.  Regards.

---

### Post by irohaphoto on 2009-10-27
> **raymondhenson said:**
> 
You can also write on "top" of your 9.04 install.

- Boot into the Karmic liveCD
- in step 4, select manual
- click to highlight your existing ubuntu installation
- click EDIT > USE > select mountpoint > **select filesystem (ext3 or ext4) and format**
- continue with the install process.  GRUB2 ought to overwrite the old jaunty GRUB.
Back-up.  Regards.

Thanks for this great piece of advice. I just found that installing the recovery disk does not delete ubuntu it just recovers the windows side.
So does how does one delete ubuntu forever?

another question:
**"select filesystem (ext3 or ext4) and format**"
what file system? what is the difference? and what format?

Thanks again

---

### Post by irohaphoto on 2009-10-27
> **raymondhenson said:**
> 

- Boot into the Karmic liveCD
- in step 4, select manual
- click to highlight your existing ubuntu installation
- click EDIT > USE > select mountpoint > select filesystem (ext3 or ext4) and format
- continue with the install process.  GRUB2 ought to overwrite the old jaunty GRUB.



Ok none of this exists please help me delete 9.04 and install 9.10
select manual and then? it goes to prepare partitions

sda1 (ntsf)
sda2 (ntsf)
sda5 (ext3)
sda6 (swap)

what do I do?

---

### Post by stinger30au on 2009-10-27
sda5 *should be* the current installed verison of ubuntu and the swap is the ubuntu swap file

---

### Post by irohaphoto on 2009-10-27
ok but how to delete 9.03 because as it is now if I 9.04 and 9.10 will be install next to each other in sda5. How do I get rid of 9.04 forever?
thanks

---

### Post by raymondh on 2009-10-27
> **irohaphoto said:**
> ok but how to delete 9.03 because as it is now if I 9.04 and 9.10 will be install next to each other in sda5. How do I get rid of 9.04 forever?
thanks

In your 9.10 installation CD ..... do you have a MANUAL option in step 4?

If so .... and to overwrite your existing 9.04:

-  Select Manual  (not side-by-side; not use entire disk)
-  A window will pop up.  On the top right, make sure you select sda (just in case you have more than 1 hard drive)
-  Look below, you will see the partitions in sda.  You are interested in sda5 which is your current 9.04 install.  Click on sda5 to highlight it
-  Now, select EDIT (one of the option/button).
-  Select USE (as you are going to use that partition)
-  Select the mountpoint which will be /  (known as root)
-  Select the filesystem (ext3 or ext4 ... whichever suits you best.  I use ext3.  Some people claim ext4 is better .... your preference)
-  Check the box FORMAT
-  Continue with the install.

For your reference, here is a guide for gparted (which is the partition editor of ubuntu).  It is good reference/reading.

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

Make sure you have a working back-up of your personal/valuable files.  There are no guarantees when it comes to partition work.

Regards,

---

### Post by kdford on 2009-10-27
As a disclaimer, I'm not very familiar with Ubuntu.

But, after reading this, I am wondering why not just use the upgrade manager to upgrade from 9.04 to 9.10?

Ubuntu states this path clearly on their 9.10 download page, at this link.
[http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)

---

### Post by cwsnyder on 2009-10-28
kdford,  In the original entry, the author stated that he cannot get on-line with Jaunty 9.04.  No upgrading possible without an Internet connection.

---

### Post by irohaphoto on 2009-10-28
> **cwsnyder said:**
> kdford,  In the original entry, the author stated that he cannot get on-line with Jaunty 9.04.  No upgrading possible without an Internet connection.

right with 9.04 I could not get on line. I did get 9.10 installed and lan is working fine
still 9.04 is there on another partition I just pushed xp over and gave 9.10 more space. still I would like to get rid of 9.04 eventually maybe I will reinstall later if necessary. for now I will close this thread.

---

