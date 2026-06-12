---
title: "Does this mean I could use (need) more RAM?"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by ahstaphus on 2007-11-28
PC slowing down a good bit when under normal (heavy) usage. I am running Ubuntu 7.10 32 bit. I have 2GB of memory and I am debating adding another 1GB. I might... MIGHT jump in to 64bit and go with 4-8GB memory if I need to. Its a relatively new dual-core Xeon based machine.

Seems like temporarily I may need to make a larger swap partition? I am pretty new to Linux so not sure if there are issues going with a Swap larger then 2GB or if it would help...

I ran "free -m" several times and the below seems to be pretty average output when I am in full work mode.

```
*****:~$ free -m
                  total       used       free     shared    buffers     cached
Mem:          2025       1975         50          0          3          141
-/+ buffers/cache:       1829        195
Swap:         1859       1514        344
```

I would rather do some tweaking if I don't have things set up optimally then purchase more hardware.

The system is pretty unresponsive when I load it down heavily. The processors are hovering around 90-100% usage for extended amounts of time, The Mobo will take a second CPU so that might be in the future as well.

If your wondering I ware many hats in a small IT department and am often doing graphics, video, database, and admin work all at the same time. I am also taking over some application development roles. O I am the Web department as well (from server admin to developer to design) No, I don't claim to be a guru we just don't have anyone else :) 

O I also normally have VirtualBox going with an XP guest for PhotoShop and Illistrator as well as a test box for compatability testing on MS. (512MB memory dedicated to the VM is my best performance trade off it seems)

---

### Post by SeanHodges on 2007-11-28
It sounds to me that you are running some pretty decent hardware. I would suggest that purchasing new hardware is probably adding a spoiler to a Ferrari.

It's worth remembering that Linux operating systems like Ubuntu are optimised to use all the available memory wherever possible, so finding that nearly all your memory is being used up after a short time of usage is to be expected. This does not mean that you should expect a performance hit, the O/S does a very efficient job of swapping out routine tasks and prioritising when needed.

My computer can run a couple of VirtualBox VM's, along with a number of applications at the same time without breaking a sweat. I think our computer spec's are fairly similar, I definitely have the same amount of RAM as you. I would recommend NOT installing 64bit Ubuntu, at least until the next release, as there is no decent substitute for the Adobe Flash player, and you might find a few other problems crop up.

More often than not, you find it's some misbehaving hardware (like a wireless card) or the use of Compiz (which is a REAL memory hog at times) that is slowing your computer down. The first thing is to try turning off the 3D desktop effects if you have enabled them, to make sure that's not the problem...

If you are still having problems, post up your dmesg log (ask if you don't know how to do this), and we can take a look at any unusual hardware activity.

Cheers,

Sean

---

### Post by ahstaphus on 2007-11-29
Yeah, I am a little familiar with the way Linux handles free memory. I wasn't worried about the small amount for reported free memory. The parts that worried me was the relatively small ratio reported in cache and the large amount of swap in use.

Oddly enough when I booted up today everything has worked GREAT. No slow downs at all. I have the XP VM going I am working with several large images (4K x 3K pixels) converting a mid sized video to SWF and doing some dev work and the computer is breezing along. 

I do have Compiz running. I tried disabling it and noticed no change in performance. However, as I said its running really fast today anyway. I don't think I would notice it speeding up at all unless I timed the video conversion.

Yesterday was not the first day things were going slowly. I did have a few updates for Ubuntu I installed yesterday, I don't remember the exact files, but it was just the regular updates offered. Maybe those fixed my issue...

---

### Post by SeanHodges on 2007-11-29
Glad things are working for you now ahstaphus, sorry if it sounded like I was talking down at you in the memory explanation, its often difficult to determine how much someone already knows about this stuff. You're right that the cache level is quite low in the report you posted, it would be interesting to know if this is still the case since the performance has improved...

If you're interested to know what updates might have fixed your problem, you could open the Synaptic package manager and open File->History to see what upgrades occured recently. Many of them even include a changelog of what fixes were included.

By the way, this all-in-one job that you have right now sounds quite exciting! :)

---

### Post by ahstaphus on 2007-12-01
No offense taken. I am glad for the help. I did a few more "free -m" and the cached mem was very low just after boot and went up to around 300-500MB after a bit of usage. Just about what I expected if my system was healthy. The Swap usage stayed under 350MB. Even the free mem stayed around 150-175MB. Those numbers stayed pretty steady for the rest of a full days work. 

I will take a look through the history from Synaptic, thanks for the suggestion.

---

