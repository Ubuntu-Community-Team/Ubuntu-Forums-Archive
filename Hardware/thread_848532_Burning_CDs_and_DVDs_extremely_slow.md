---
title: "Burning CDs and DVDs *extremely* slow"
date: 2008-07-03
forum: Hardware
---

### Post by jipis on 2008-07-03
I recently (last week?) upgraded to hardy from either edgy or feisty. Can't remember which. Ever since, burning a disc -- cd or dvd -- is extremely slow and seemingly processor-intensive. 

[LIST]
[*]Speed: I used to be able to burn a dvd-rw 4GB in about 10 minutes. Now it takes about 40. Similar speed problem with burning CDs, but I don't have the exact numbers.
[*]Processor (or memory??): It's so slow that I can't use my machine while burning. (The mouse stutters, screen is sluggish, etc.) I also haven't thought to take a look at top while burning. I'll try that later this evening if someone thinks it might be insightful.
[/LIST]
I'm fairly desperate on this. I haven't been able to find anyone else (my google-fu is pretty good, IISSM) who seems to have this problem.

Shot in the dark: could it be related to the SCSIfication of the IDE drives in hardy?

Let me know what kind of diagnostic data to provide and I will.

Thanks for your help!

-J

---

### Post by lukjad on 2008-07-03
Try a different burning application like k3b instead of the default burner. Also look for a CL burner.

---

### Post by stchman on 2008-07-03
> **jipis said:**
> I recently (last week?) upgraded to hardy from either edgy or feisty. Can't remember which. Ever since, burning a disc -- cd or dvd -- is extremely slow and seemingly processor-intensive. 

[LIST]
[*]Speed: I used to be able to burn a dvd-rw 4GB in about 10 minutes. Now it takes about 40. Similar speed problem with burning CDs, but I don't have the exact numbers.
[*]Processor (or memory??): It's so slow that I can't use my machine while burning. (The mouse stutters, screen is sluggish, etc.) I also haven't thought to take a look at top while burning. I'll try that later this evening if someone thinks it might be insightful.
[/LIST]
I'm fairly desperate on this. I haven't been able to find anyone else (my google-fu is pretty good, IISSM) who seems to have this problem.

Shot in the dark: could it be related to the SCSIfication of the IDE drives in hardy?

Let me know what kind of diagnostic data to provide and I will.

Thanks for your help!

-J

Did you do a clean install or go the upgrade route?  The clean install is faster and works better.

---

### Post by jipis on 2008-07-03
> **stchman said:**
> Did you do a clean install or go the upgrade route?  The clean install is faster and works better.

It was a clean install. Installed / and /boot right over the old partitions. Don't trust updates. Call it a MS-inspired fear.

As for applications, it doesn't matter. I've used k3b and gnomebaker. Both exhibit the same problem. Which leads me to believe it's a driver issue. Or, a general kernel issue. Or something. Makes me wish I had actually done the kernel-hacking assignments in the OS class I sat in on in grad school....

-J

---

### Post by jipis on 2008-07-03
So, apparently my google-fu isn't as good as I thought. I just found [this post]("http://ubuntuforums.org/showpost.php?p=4749779&postcount=2") talking about DMA. Apparently DMA wasn't on/working/whatever for the dvd drive. It seems to be now. I'm off to test. :)

---

