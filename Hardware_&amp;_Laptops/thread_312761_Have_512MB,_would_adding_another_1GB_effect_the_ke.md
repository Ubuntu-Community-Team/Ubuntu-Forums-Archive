---
title: "Have 512MB, would adding another 1GB effect the kernel?"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by hotplainrice on 2006-12-04
Hi there,

yes, simple one, would adding another 1GB stick to a 512MB RAM setup hurt ubuntu in any way? I don't understand what this 1GB lowmem or 4G highmem means.

Cheers.
Zak

---

### Post by hod139 on 2006-12-04
Adding 1GB will not hurt anything, it will only help.  The 4GB limit is because a 32 bit processor can only address 2^32 bits (4 GB) of ram without extra work.

---

### Post by hotplainrice on 2006-12-04
Do I to do any changes like change of kernel?

---

### Post by hod139 on 2006-12-04
Nope, just insert the RAM and reboot.

---

### Post by hotplainrice on 2006-12-04
Thanks hod139.

---

### Post by nisarg on 2008-03-21
Same question really - just to get a clearer picture.

I am running Ubuntu 7.10 on "Hynix 512 MB DDR333 SO-DIMM-PC2700" RAM. 
I only have 1 extra slot (empty, at the moment). Now I would like to upgrade the RAM and get better performance out of my machine.
Just wondering if there is any harm if buying a new 1GB module? that would make my machine run on 1GB + 512MB, Will this have any drain on performance or cause any mismatch and hence not allowing my machine to leverage best out of my RAM? I would want to make sure my system will be able to make the best use of this new 1GB module despite having a 512 MB in the other slot.
 
Or would it only help?  

Thanks for all your inputs

---

### Post by oldsmobile_mike on 2008-03-21
> **nisarg said:**
> Same question really - just to get a clearer picture.

I am running Ubuntu 7.10 on "Hynix 512 MB DDR333 SO-DIMM-PC2700" RAM. 
I only have 1 extra slot (empty, at the moment). Now I would like to upgrade the RAM and get better performance out of my machine.
Just wondering if there is any harm if buying a new 1GB module? that would make my machine run on 1GB + 512MB, Will this have any drain on performance or cause any mismatch and hence not allowing my machine to leverage best out of my RAM? I would want to make sure my system will be able to make the best use of this new 1GB module despite having a 512 MB in the other slot.
 
Or would it only help?  

Thanks for all your inputs

If you're buying one you might as well buy two, and put a 1 gig stick in each slot, just to avoid any (very slight possibility) issues, related to different speed of the chips, etc.  Memory is usually best installed in matching pairs.  You may want to confirm that your motherboard can handle more than 1 gig, first, however (some manufacturers only support 1 gig total, hardware limitation)

---

### Post by nisarg on 2008-03-21
Hey. 

Thanks for your response.
Yes - I believe my IBM T40 (Type 2374) supports upto 2 gigs. 
OK - So I guess slipping in another 1gb module shouldn't do any harm, although matching pairs would make the best option. 

Another question that springs up to my mind is - how much performance gain would I gain have comparing (512MB+1GB AND 512MB+512MB)? Does it make a lot of difference having 512MB more and obviously with a mismatch in 2 RAM modules? Afterall whats the point in paying for 1GB when its not going to give me the benefits of it.

Cheers.

> **oldsmobile_mike said:**
> If you're buying one you might as well buy two, and put a 1 gig stick in each slot, just to avoid any (very slight possibility) issues, related to different speed of the chips, etc.  Memory is usually best installed in matching pairs.  You may want to confirm that your motherboard can handle more than 1 gig, first, however (some manufacturers only support 1 gig total, hardware limitation)

---

### Post by oldsmobile_mike on 2008-03-21
> **nisarg said:**
> Hey. 

Thanks for your response.
Yes - I believe my IBM T40 (Type 2374) supports upto 2 gigs. 
OK - So I guess slipping in another 1gb module shouldn't do any harm, although matching pairs would make the best option. 

Another question that springs up to my mind is - how much performance gain would I gain have comparing (512MB+1GB AND 512MB+512MB)? Does it make a lot of difference having 512MB more and obviously with a mismatch in 2 RAM modules? Afterall whats the point in paying for 1GB when its not going to give me the benefits of it.

Cheers.

Hi there,

As far as how much performance you will gain, that all depends on what you use the system for.  If all you're doing is looking at a couple web pages and checking your email, you might not even need it at all.  Don't forget, Ubuntu is infinitely more efficient at managing memory than Windows is, and can do a lot with just 512MB.  However, if you're running a lot of apps at once or doing graphic work, definitely more is better.

I would suggest using some of the system monitoring utilities to view how much ram % you're using at any given time.  If you're near the limit, and it's having to hit the page file frequently, then definitely add as much as you can afford ( [www.newegg.com](www.newegg.com) has the best prices for this sort of stuff).  And once you add the ram, check those system monitors again - what I did on mine after I upgraded was to change the frequency by which the laptop uses the page file (I forget how I did this, but found instructions here in the forums...  I'm sure I have a copy saved at home) down to like 1%, so that it always uses the main memory, and never uses the page file unless absolutely necessary, which works very well.

Hope this helps!

---

### Post by nisarg on 2008-03-21
Thanks again.
The machine in concern is my home laptop. I do have another machine from work, that I use for doing more technical work-related stuff. So yes majority of time I view web pages, chat, check email, etc - pretty much usual stuff. But often I run WINE, and can have around good 25 tabs running in my firefox, and good few other apps.

Now - I guess when you say page file you actually mean SWAP? I usually do a run the System Monitor 2.20.0 applet sitting on my panel. And it seems to be a good indicator - it  shows mainly two colored % graphs of "in use by programs" and "in use by cache". In total (programs + cache) it usually seems to hit 95% plus mark all the time. Generally speaking running programs roughly seem to use up anything between 40% to 60%. But thats usually when I have my system running under moderate load (a good few apps, messengers, Wine OO etc..). 

Now this is all when I ain't running Compiz or anything fancy in that lines. I did use to have Compiz, it seemed all bit too sluggish and so I turned off the visual effects and uninstalled and purged all Compiz packages. And I am sure that can use up a good chunk. No doubt that has speeded things up to a good amount. However, Gnome still seems a little sluggish. For eg. when I hit the minimize button on any program it trails black borders while going down on the panel, and thats hell of the graphics I am getting without asking :). 

So question here is - what should I be concerned with "memory used by programs"? If so, I almost never really go too close to 100% there. Does that mean I really am not short of RAM at all? 
Heres the output of the 'free' command. I am not really too sure how to monitor the "page file hits" as you say in Linux. Any pointers will be a great deal of help. Also, you might notice below at the moment SWAP is not used at all. But I am sure I have seen a good amount of SWAP being used up, but havent got a proper stats. Might be well worth monitoring it for a few days I guess. 
Any help fine tuning Gnome or memory for that matter will indeed be a great help.
 
```

             total       used       free     shared    buffers     cached
Mem:        515264     465440      49824          0      20044     258660
-/+ buffers/cache:     186736     328528
Swap:       859436          0     859436


```

Thanks again. Your responses are appreciated.

> **oldsmobile_mike said:**
> Hi there,

As far as how much performance you will gain, that all depends on what you use the system for.  If all you're doing is looking at a couple web pages and checking your email, you might not even need it at all.  Don't forget, Ubuntu is infinitely more efficient at managing memory than Windows is, and can do a lot with just 512MB.  However, if you're running a lot of apps at once or doing graphic work, definitely more is better.

I would suggest using some of the system monitoring utilities to view how much ram % you're using at any given time.  If you're near the limit, and it's having to hit the page file frequently, then definitely add as much as you can afford ( [www.newegg.com](www.newegg.com) has the best prices for this sort of stuff).  And once you add the ram, check those system monitors again - what I did on mine after I upgraded was to change the frequency by which the laptop uses the page file (I forget how I did this, but found instructions here in the forums...  I'm sure I have a copy saved at home) down to like 1%, so that it always uses the main memory, and never uses the page file unless absolutely necessary, which works very well.

Hope this helps!

---

