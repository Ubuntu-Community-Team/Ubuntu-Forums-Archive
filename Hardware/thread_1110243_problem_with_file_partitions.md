---
title: "problem with file partitions"
date: 2009-03-29
forum: Hardware
---

### Post by shahin on 2009-03-29
Greetings-
   I am not sure what is the etiquette for posting to more than one group.  I posted this to the General Help group also as I think it is relevant.  I apologize for repeated post, and please do let me know if there is a better way to handle this.  I have the following question please:

Greetings-
Recently I keep getting an error message about my tmp directory being full. I tried deleting some files, which messed up firefox a little, but it is ok now. I then used an old desktop cd and using GParted, I see that /dev/sda2 is full. But I can not resize the partitions. I have three partitions on my system:
/dev/sda1 which has 40G and I have my xp stuff on it. Next is /dev/sda2 which is full and only has 7.45 G of space. then /dev/sda3 with 64.33G. Out of which 62.16 GiB is dedicated to /dev/sda6 and rest is used by swap.
Now I can shrink the /dev/sda6 from one side ie. from the right hand side. But I can not add the unallocated space to /dev/sda2 as I want to. What should I do?

---

### Post by logos34 on 2009-03-29
> **shahin said:**
> I then used an old desktop cd and using GParted...

Now I can shrink the /dev/sda6 from one side ie. from the right hand side. But I can not add the unallocated space to /dev/sda2 as I want to. What should I do?

right, because the unallocated space is INSIDE the extended partition...you need to also shrink the extended (sda3) so the space is left outside.  If it won't let you it may be because you're using an older version of gparted on that old (how old?) ubuntu cd that doesn't support resizing from the left side.  In which case download a newer version.

---

### Post by shahin on 2009-03-29
I was using 6.10 cd.  Wow that is a good solution.  I do have a newer cd, ie. 8.04. But it has some graphics issues.  But I think I can get around that.  Thanks, I'll let you know how it goes.

---

### Post by shahin on 2009-03-29
ok I am looking that new Gparted interface.  Now I am running into another issue.  I still can not changed the size of /dev/sda3.  I think it is because swap is busy / mounted.  I see the picture of a set of keys next to swap and /dev/sda3 which swap is part of. But you are right about being able to shrink from the left using the new Gparted:-) Thanks for that.  But is there a way to get around this new problem?

---

### Post by shahin on 2009-03-30
When I right click on /dev/sda3 and select the information, the status section says: Busy ( at least one logical partition is mounted ) What should I do please?  Is this why I can not resize /dev/sda3?  I did try what you suggested.  I shrank the logical partition within /dev/sda3.  It is called /dev/sda6.  But I still can not resize /dev/sda3.  Where can I learn what is mounting?  I do not understand why /dev/sda6 is not mounted, or how it can have data in it if it is not.

---

### Post by shahin on 2009-03-31
Greetings-
    Ubuntu Cummunity and Google are two things that have been a big help in me learning Linux platform.  The problem with Gparted was that swap was active.  Gparted automatically uses / activated swap, and as swap was part of my /dev/sda3 partition, I could not resize it.  The fix was to inactivate swap by issuing the command:
```
 
swapoff /dev/whatever

```

If you want to verify that your swap partition is active you need to run the command:
```

swapon -s

```

After that gparted did an excellent job of changing the size of my partition.  I just tested it and it worked like a charm.  BTW, I found this information at:

[http://ubuntuforums.org/archive/index.php/t-111281.html](http://ubuntuforums.org/archive/index.php/t-111281.html)

The link has really good information about this problem, similar issues, and excellent feedback on how to use fdisk.

---

### Post by logos34 on 2009-03-31
> **shahin said:**
> The problem with Gparted was that swap was active.  Gparted automatically uses / activated swap

yep, it automatically activates it, locking up all the logical partitions.  Annoying.

---

