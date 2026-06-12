---
title: "Can NOT partition my existing drive"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by Genecide on 2009-04-04
Hey there, just starting to get into all this, so please bear with me.  I have a 120gig HD on my laptop.  10 of it came partitioned for recovery, the rest is used by Vista.

I just tried installing Ubuntu via Wubi.  I got it to work, but it would only go ON my Windows Partition.  Once in Ubuntu, I wanted to see my Windows files, and took the necessary steps to do so, but could only see my Recovery Partition.  I assume I couldn't see my windows partition because that's what I was running off of.  Please correct me if I'm wrong

So to remedy this, I thought I would shrink the windows partition and create a new one for Ubuntu.

I tried the Disk Management service in Vista.  The only option available was Shrink, and it told me there was no free space to available to shrink it.  I tried diskpart.exe and got the same message.  I got and tried the latest version of Partition Magic and just got some error code.  And I tried the Ubuntu installation CD, and again, was just told that the partition was unable to be completed.

Does anyone have any advice on why I can't shrink my partition?

---

### Post by Partyboi2 on 2009-04-04
Try defraging vista before trying to use vista's shrink option.

---

### Post by tlois on 2009-04-04
A couple of questions.  When you say you installed using Wubi, do you mean you installed it as you would a program- did you do it from your Windows desktop?

When you are trying to install via cd, when it gets to the fist part, right after it asks you language, are you selecting "try ubuntu" or install ubuntu?  we had a problem with disk partition on a new dell laptop when we tried via the option "try ubuntu," but when we used the "install option" it worked.


(i have also had a strange thing happen twice where it shows 0% progress as it partitions, but was actually working. )

---

### Post by adalal on 2009-04-04
Try looking under the /host folder. I think that's where the vista partition was present....

Let me know if that works...

Also, windows does give problems shrinking, this is because there will be data written on both ends of the partition, leaving no space on either end to shrink.... all i can say is try google and look for better defrag tools rather than vista's own defragging program, and then try shrinking. I backed up my data, and reinstalled vista...

---

### Post by Mark Phelps on 2009-04-04
Genecide:

Try this link, has some tips when Vista refuses to shrink the partition:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

### Post by Genecide on 2009-04-04
to Mark Phelps
I tried that.  I freed up a ton of space on my HD, which is great.  Now somethings taking up to much memory for me to use programs.  I can't even run firefox... so I gotta get fixing that now.

adalal
I removed Ubuntu for the time being, so I can't really check, but if I can't fix my memory issue, I'll probably just do a fresh windows install

tlois
Yes I installed Wubi as I would a program, from Windows.  It asks what partition I want to use, but the one with Windows is the only one I have.

I chose install at first, and now I've used "try" then install once I'm in the try. 


Thanks for your reponses, and your continued help

---

### Post by Genecide on 2009-04-04
forgot to mention I managed to get Windows Disk Management to see 5 gigs worth of space free for a partition, but I need more.  I deleted a bunch of files, but the number wouldn't go up.

---

### Post by Mark Phelps on 2009-04-04
Deleting files isn't enough.  That frees up space but it's scattered across the partition.  You need to do a defrag afterward.

---

### Post by Genecide on 2009-04-04
Yeah.  I used both defragmenting tools given in your post, after I deleted files.  No difference was shown

---

### Post by Mark Phelps on 2009-04-06
Sorry to hear that ...

I know the Vista tool is all but useless for shrinking partitions, but unfortunately, it's the only tool today that doesn't run the risk of corrupting the Vista OS in the process.  

Just checked the very latest GParted version and it still mentions specifically NOT working properly in shrinking Vista partitions.

Also, just read a couple of other posts from folks that used Partition Magic to shrink their Vista partitions, and got unbootable systems as a result.  So, even Partition Magic can corrupt Vista OS partitions.

Only way I know to force Vista into a smaller space at this point would be to remove it, expand the Ubuntu partition to the size you want, reinstall Vista in the smaller unallocated space.

---

### Post by ronparent on 2009-04-06
There is a package available online for a price called Casper. I believe this would be safe for vista if you are really in a pinch (I have used it myself primarily for ghosting my win installs on backup devices).

Please, hermann et al, this is hopefully a helpful suggestion and not an endorsement of any and all things windows,

---

### Post by Mark Phelps on 2009-04-06
ronparent:

Can Casper handle the situation where the disk space for the restoration is smaller than it was when the imaging was done?  That's basically what the OP needs to do: back off Vista, remove the Vista partition, resize the other partitions to take more space, restore Vista -- to a smaller space.

If it can't handle a smaller space, it will either fail or it will corrupt adjacent partitions when it rewrites the partition table to enlarge the Vista partition back to its earlier size.

---

### Post by ronparent on 2009-04-06
Mark Phelps:

Yes. It can compact and write to a smaller space, as long as the space will accomodate all the data already on the drive (ie drop vacant space in the source drive).

---

