---
title: "Virtual Memory"
date: 2008-07-28
forum: General Help
---

### Post by kpi9616 on 2008-07-28
Sorry if this is the wrong thread to put this in. Wasn't really sure on where to put it.

I have 256MB of memory. Is there a way that I can assign more virtual memory to hopefully speed up the computer a bit? I bet there is, just I can't find it.

---

### Post by jonian_g on 2008-07-28
"Virtual memory" is the swap partition. You already have and it's big enough. I don't think you need more.
But if you feel that you want to do it, boot with your live cd and use Partition Editor (System>Admin) and make the swap partion biger, but first you have to make one of your other partitions smaller to get free space.

---

### Post by mikewhatever on 2008-07-28
Virtual memory is called swap, a fixed sized partition, so, no, you can't add to it, at least not without resizing. How larg is you swap?
> free -m

---

### Post by kpi9616 on 2008-07-28
Ok well I did one big partition. I didn't create any other ones. So your telling me there is a "swap partition" automaticly installed?
Its probably slow cuse its a old computer and its PC133 memory. lol
Got it free. Decided it might be a good one to use for ubuntu to play with.
Thanks for the help jonian_G.

---

### Post by kpi9616 on 2008-07-28
Its saying my swap is 721 (I'm guessing MB.. right) it says 39 is used and that leaves 681 free. I would like to try and make this bigger if possible. Worth a try to see if it helps at all.

---

### Post by jonian_g on 2008-07-28
You can try it but I don't think you will see a difference.
As I said, if you like to do it, do it. You will learn something more.

---

### Post by kpi9616 on 2008-07-28
Ok so I have to put in the live CD and I will be able to do it from there? Mind giving me insturctions on how? Thanks.

---

### Post by northern lights on 2008-07-28
> **kpi9616 said:**
> it says 39 is used and that leaves 681 free
681/721x100%=94.5%
19 twentieth of your swap space are free.

> **kpi9616 said:**
> I would like to try and make this bigger if possible. Worth a try to see if it helps at all.
How would that "help"?

If ```
free -m
``` would ever show the opposite (95% swap space used, 5% free) you might need more swap space, but it still wouldn't make the comp run faster. SWAP is a partition on a harddrive which is a million times slower than RAM in access times (5 to 70 nanoseconds versus 5 to 10 milliseconds for a harddrive)

---

### Post by kpi9616 on 2008-07-28
What do you "how" northen lights. That is what I am wondering. How do I do it. If I can. True that most of it is not used. But still, if I could make it bigger, it may help load my programs faster. But maybe not.

Ok now you edited your post. so you explaind it a bit more.

---

### Post by jonian_g on 2008-07-28
When the live cd boots go to System>Admin>Partition Editor. The window that comes up shows all your partitions. Make shure they are all unmounted (right click on the partition and unmount).

Make one of the other partitions (exept the one that says extended) smaller by right clicking on it and chose resize/move. Let's say you made it 500MB smaller.
Then right click on the swap partition, chose resize/move and make it 500MB biger.

Click apply on the toolbar. Reboot and you're done.

---

### Post by sandeepy on 2008-07-28
northern lights is correct, you seem not to be using it enough to make unnecessary swap space expansion. BTW, there are two ways to do it :

1. at boot time you can expand/shrink your default swap parition size.
2. if you do not have any free space on the disk (to be used for swap file system), you will have to free the current paritions. I use gparted for such purposes. Next you can use gparted to tell that you want more swap space. It is GUI based so you won't have problems with understanding.

---

### Post by northern lights on 2008-07-28
> **kpi9616 said:**
> I have 256MB of memory. Is there a way that I can assign more virtual memory to hopefully speed up the computer a bit? I bet there is, just I can't find it.
Lemme also comment on the actual issue at hand:

While, at the expense of a GUI, Ubuntu can theoretically run with a CLI on a machine with 64megs RAM only, the recommended minimum for Hardy is now 384MB. With a graphical interface it will run even on 128 with a lot of fiddling, I read.

Nonetheless, the point being is, that if you want to speed up your comp you might wanna look into a more lightweight desktop environment such as xfce.

---

### Post by kpi9616 on 2008-07-28
Thanks for the directions jonian_g. I think I might give it a go.
But ya it probably won't help. I guess its the old crappy computer I put it on. :p
Thanks for the help guys.

Ya I am thinking of building a computer for linux. I got it all together for only $240 or so. But don't really have the money right now for it. I guess the current computer will have to do. I could get memory for it though. I think. But not sure how expensive it is.

---

### Post by northern lights on 2008-07-28
> **kpi9616 said:**
> 
But ya it probably won't help
Might as well do it for a learning experience. But yeah, it _definitely_ will not.

---

### Post by jonian_g on 2008-07-28
> Might as well do it for a learning experience.

That's what I said, learning experience. It's good to have the willingness to learn new things.

---

### Post by mikewhatever on 2008-07-28
> **kpi9616 said:**
> Thanks for the directions jonian_g. I think I might give it a go.

Bad idea. Adding more MBs to your swap would be a waisted space.

---

### Post by northern lights on 2008-07-28
> **mikewhatever said:**
> adding more mbs to your swap would be a wasted space.+1

---

### Post by jonian_g on 2008-07-28
> Originally Posted by **mikewhatever**  
adding more mbs to your swap would be a wasted space.

Not if you have a big HD or if you don't need a lot of space.
Actually it depends on the user what is good or bad. I have a 320GB HD with more than the half of it free and I don't use a swap partition.

---

### Post by kpi9616 on 2008-07-28
well I won't be putting anything on this. The HDD is a 30gig one. All I will use it for is messing with. But I will try it out to learn how. Again thanks for the help.

---

