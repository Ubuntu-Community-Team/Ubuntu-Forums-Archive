---
title: "/usr on my SSD?"
date: 2014-04-29
forum: Hardware
---

### Post by maxinstuff2 on 2014-04-29
So I am building a new machine (primarily for gaming) and am probably going to run with a 120GB SSD and a 1TB HDD. 
RAM will start at 8GB but will definitely be upgrading this machine later - to how much I don't know, probably 16GB. The 50GB swap partition is really just a round arbitrary number. 

This has been written about a lot and I am seeing a lot of conflicting information - so I am looking for some feedback on the install/partitioning set-up I am looking at.

First, my assumption is that if I do not specify that a directory should go somewhere it will go wherever root is (in this case on the SSD). If this is wrong please correct me.

My main query is regarding whether I should put /usr on the HDD instead of the SSD. As this is where most apps go I would have thought it would benefit from being on the SSD - and steam appears to install actual games into /home so space shouldn't fill up with my games library.  

I have read that the SSD for games ONLY affects load times and not actual performance - whereas having root on the SSD does affect performance because that is where all the important system libraries are that apps call upon?


My install plan at the moment is -
on the 250GB SSD:
/
no partitions

1 TB HDD:
Partition 1 (500GB)
/home
/var
/temp
Partition 2 (50GB)
/swap
Partition 3 (450GB)
blank - I'll use this partition to experiment with steamOS a bit later. If it is an option I will have it utilize the same swap partition (I don't THINK this would cause a problem?).

tl;dr - what do you think of my SSD/HDD plan? And am I making any noob errors here?

---

### Post by bapoumba on 2014-04-29
> **maxinstuff2 said:**
> So I am building a new machine (primarily for gaming) and am probably going to run with a 120GB SSD and a 1TB HDD. 
RAM will start at 8GB but will definitely be upgrading this machine later - to how much I don't know, probably 16GB. The 50GB swap partition is really just a round arbitrary number. 

I'm just going to answer that part, 50GB swap is a little (or a large amount) over the top : [http://ubuntuforums.org/showthread.php?t=2211150](http://ubuntuforums.org/showthread.php?t=2211150)
So 9 GB to start with, if you are going to use hibernation, is way enough.

---

### Post by maxinstuff2 on 2014-09-15
> **bapoumba said:**
> I'm just going to answer that part, 50GB swap is a little (or a large amount) over the top : [http://ubuntuforums.org/showthread.php?t=2211150](http://ubuntuforums.org/showthread.php?t=2211150)
So 9 GB to start with, if you are going to use hibernation, is way enough.

I know it's been a while, but thankyou - your advice was very helpful.

I finally got my build past the "minister for finance"  - ended up getting a decent deal on a single 1TB SSD, and went with 8GB for swap (this is with 8GB RAM).

---

### Post by bapoumba on 2014-09-15
Glad to see you worked it out, including the financial considerations :)

---

