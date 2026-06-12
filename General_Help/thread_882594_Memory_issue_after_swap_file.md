---
title: "Memory issue after swap file"
date: 2008-08-07
forum: General Help
---

### Post by Zalbor on 2008-08-07
I've been using the system monitor applet on my gnome panel for some time now, and I noticed that swap usage was always 0%. So I decided to replace the swap partition (which was 2GB) with a smaller swap file.

I created the swap file following the instructions from a post here that I can't find again. It was basically:
```
sudo dd if=/dev/zero of=/swapfile bs=1024 count=X
sudo mkswap /swapfile
```
where X is the size of the file in MB *1024 (I made a 768MB file)
And then added "/swapfile   swap  swap defaults 0 0" to fstab (after commenting out the line about the swap partition. I rebooted and everything was fine, the swap file being used instead of the partition.

Next I rebooted into the live CD, and used gparted to delete the swap partition and then to grow my home partition to take up its space.

I did this, the exact same thing, on two computers. One (a laptop) that has a 2GB RAM and had 1GB swap partition, and another (a desktop) on which the numbers are reversed.

**The problem:**
On the desktop PC, since I did this RAM usage has jumped up to almost 100% (usage by programs + usage as cache). Before swapping the swap partition for a swap file, these two only added up to about 50%. Still, swap usage is 0%.

I don't think that's normal, is it?

---

### Post by kerry_s on 2008-08-07
you have 1gig of ram which is enough to never have to dig into swap. you don't want to use swap unless absolutely needed as the hd is slower than physical ram. with 1 gig you could go with out swap, but swap is recommended, in fact some programs will check for swap just to make sure there's enough room to run. i have 1 gig as well and it seems to never get used, but i have seen it used when i've opened huge ppt files or book size docs.

---

### Post by Zalbor on 2008-08-07
Thanks, but I knew that already... I do want to have some swap, just to be safe, and I might even lessen it. But that wasn't my question.

How is it explained that memory usage has doubled since I made the change, and does it indicate a possible problem?

---

### Post by Zalbor on 2008-08-07
After having the computer running for hours, it's gotten worse now!
Memory is 100% filled, swap 5%. I never noticed swap being used before!

---

### Post by kerry_s on 2008-08-07
try looking in top, it will tell you how much memory each process is using.

---

### Post by Zalbor on 2008-08-07
I don't think it adds up...

The applet says 44% memory by programs, 50% as cache, 5% of swap used.
Before I made the change, swap was 0% and the memory was less than 50% both programs and cache...

EDIT: Also since I did it, during booting the graphical "Ubuntu" display disappears before fully booting and it goes on booting in a text display. When that happens, the first thing on the screen is just "sda sdb sdc" (the 3 hard drives connected to the computer). Could this be related?

---

### Post by kerry_s on 2008-08-07
it looks perfectly normal to me, perhaps when you had the swap partion it was not being used/mounted so it always read 0, but now that your using a swap file it sees the extra space and is using it. it looks like exactly what i would expect with swappiness set at default.

i have no idea about your splash screen, i doubt it's related to swap problems.

---

### Post by Zalbor on 2008-08-08
If you say it's normal, that's good. But I was pretty sure that the memory itself never got so high before...

Maybe it's explained by the difference in fstab? The line for the partition was like this:
```
#UUID=a90bbc1a-0630-4138-ac5c-05489c3ae495 none swap sw 0 0
```
While for the swap file it's:
```
/swapfile none swap defaults 0 0
```

Originally the second word was "swap" too, but I read it should be "none" so I changed it. I can't find in "man fstab" or "man mount" what "sw" does though...

---

### Post by kerry_s on 2008-08-08
i would put the "sw" back in there.

---

### Post by Zalbor on 2008-08-08
I did that. It doesn't help with the memory thing though...

---

