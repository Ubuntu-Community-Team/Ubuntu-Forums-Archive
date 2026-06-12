---
title: "Ubuntu @ Dell inspiron e1505/6400"
date: 2007-03-23
forum: Hardware &amp; Laptops
---

### Post by jandaba on 2007-03-23
ok, so my urge to experiment with linux led me to a lil problem, so i desperately need your help. so here's what i did (i hope im posting this at the right place)

i read a few installation guides and decided to try linux. i downloaded the latest one and burned it to a cd, then i created 9gb of unpartitioned free space with partition manager. i booted from the ubuntu cd and began installing, everything went smoothly until the installation was complete and the computer restarted, when i tried to start ubuntu it froze at the exactly same time, and in the recovery mode startup it said something about freezing and cpu#0. i have an intel core duo 1.8ghz processor and i didn't really think it could be a compatibility issue, as i know a few people who have installed ubuntu on the exact same laptop. 

now, seeing that it didn't work, i (for some strange reason) decided to delete the whole thing and wait for a friend who's been using linux for a while who'll be coming over in a few days. so i logged on to windows and deleted the partition used by linux through the same paragon partition manager. i did this without  doublechecking on the net, tho, so it ended up with this 'grub' thing being deleted as well, so now i cannot boot windows as well. i can only log on through the ubuntu cd, and the partition program there shows 60 gigs of unpartitioned space (my hdd is 60gigs).... 

so now i can't install ubuntu and neither can i log on to windows. how can i reverse this? will installing grub help and if so, how exactly do i do this? oh and one more thing, does this '60 gigs of unpartitioned space' mean that everything on my drive has been lost?? if not, is there any way of backing up my data from this situation?


quite a load of questions, i know, but im kinda desperate :) help would be appreciated !


cheers

---

### Post by veloce on 2007-03-23
> **jandaba said:**
> how can i reverse this? 


To reverse this, re-install windows from cd.  It should recognise your existing installation and let you repair it.

Back to the problem with linux, does your laptop have wireless?  I occasionally got a similar error and the fix was to turn off the wireless (in bios).  Once it had booted once, I could turn it back on and set it up.  (I later broke it when changing some settings and had to go through that routine again.)

---

### Post by jandaba on 2007-03-23
yes i have wireless and i'll try doing that, but at this point it's useless cause when i try to install ubuntu, i can't see the partition anymore, so i cant install it in the unpartitioned space, as the only thing that it sees is the whole hard drive, labeled as unpartitioned..... and yes, i tried repairing windows from the cd, and the installation was recognized and repaired, but i still get the same error message during boot.... i looked it up by the way, and this is what the error message corresponds to:

5 : Partition table invalid or corrupt
    This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign. 


i saw a topic here about this kind of scenario, but they said that grub can be restored by reinstalling linux.... however i cant do that, as in that case my whole drive will be formatted, as the partitions arent visible anymore, for some reason....

---

### Post by veloce on 2007-03-25
If the partition table is stuffed you may be out of luck.  

Only suggestion I can think of, and I would only recommend this as a last resort) is to attempt to repair the partition table using a partition table editor.  I would try creating a live CD that includes a partition editor.  (I use "Slax" for this type of thing as it's really easy to create your own live cd with the modules you want.)

---

### Post by weijie90 on 2007-03-26
Hi,

Do you have a MediaDirect installation CD? Boot from that and use it to wipe your drive, partition table and MBR. (Select the option which uses the whole drive) A word of caution, though- it will wipe your Synaptic System Restore image. (But you can use Ghost for Linux instead.)

Good luck!

---

