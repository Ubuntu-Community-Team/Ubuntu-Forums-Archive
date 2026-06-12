---
title: "reformat ntfs drive but fdisk"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by gaillard on 2007-02-18
I have read a couple threads on this subject and I want to make sure this is all safe because the data I have on these two drives I am reformatting is critical.  I have 2 300 gig sata drives with redundant data.  I want to reformat one to ext3 and copy the contents of the ntfs one to it and then do the same to the other but I keep reading people's fdisk is showing wrong or not updated info after they use mke2fs.  

As I understand it I should
sudo umount /dev/sdd[partition number]
sudo mke2fs -j /dev/sdd1 (or 2...)

and then reboot.

Do I need to do anything else?

and is it safe?

---

### Post by taurus on 2007-02-18
You still need to mount the new ext3 partition before you can use it though.  Just make sure you get the right partition or else bye-bye data.

---

### Post by gaillard on 2007-02-18
hahahha you made me laugh out loud.  Your sincerity of disparity between our feelings against my data is amusing :lolflag: 

But thanks for the warning! =)

---

### Post by gaillard on 2007-02-18
Hey take a look at this, it has me perplexed.

In this screen shot for some reason in the open window you notice the path says one thing and the title says another when its supposed to be just the path!!

---

### Post by taurus on 2007-02-18
Not sure exactly what you mean but you mount that partition to /media/cisuM so it shows up as an cisuM.

---

### Post by gaillard on 2007-02-18
exactly, BUT if you look at the title bar of that window it says Music! and if I go to that folders properties it shows  /media/Music when clearly I am browsing cisuM as that path bar shows in the window... what the heck

---

### Post by gaillard on 2007-02-18
Is this just something silly that I am missing? I mean it is 3 in the morning...

---

### Post by taurus on 2007-02-18
> **gaillard said:**
> Is this just something silly that I am missing? I mean it is 3 in the morning...

Where did you mount that partition?  Could be the name of the volume of the drive?  

And since you just reminded me about the time, I am outta here...

---

