---
title: "i want to delete my swap partition..."
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by zero7404 on 2009-05-11
i don't see any real need for this 1GB partition i installed when i added ubuntu to my system....

every time i check my files free the swap partition is showing zero used....

i have 4GB of physical ram and at the moment i don't use any intensive software on the OS, just browsing, a little openoffice use, etc...

will i have any problems if i remove the swap partition ?

---

### Post by MysticGold04 on 2009-05-11
If you put your computer to sleep or hibernate it, it uses the swap space to do so... so if you remove your swap partition, it will break sleep and hibernation.  I've noticed this also, my laptop has 4GB of ram, and I rarely see any swap used, but I have plenty of free space so it does not bother me to have about 8gb dedicated to swap.. very overkill I know, but... 

 Every so often I see the swap being used a little... maybe 200mb or so when I'm running alot of apps, but I still have alot of RAM left at the time.

---

### Post by zero7404 on 2009-05-11
that didn't occur to me....thanks for the insight....

now i am thinking, do i have a large enough swap space ? been experiencing issues with resuming after suspend, but i think that is related to nvidia drivers in general. i never use hibernate, because ubuntu loads so quickly on bootup....

i figured that i have 4GB of ram, but maybe i need a larger swap partition to store more, maybe it would reduce the chances of seeing a problem with suspend....

i assume gparted would do a resize effortlessly.

---

### Post by logos34 on 2009-05-11
yes, gparted can handle the resize.

swap size shouldn't be a factor in your suspend-to-ram problems (which, as its name implies, stores the data in the memory rather than on disk)

---

### Post by Artemis3 on 2009-05-12
I have 4gb of ram and don't use any swap partition. I never hibernate or suspend either, and the same is applied to my (now with 2gb ram) eeepc.

So yes, go ahead and delete it.

---

### Post by MysticGold04 on 2009-05-12
I don't know where I picked up the reccomendation to have your swap partition 2x the size of your ram, but that's how I've always set mine up.  When I had my Eee, I had a 4gb swap and 2gb ram.

---

### Post by zero7404 on 2009-05-12
thanks for the posts....

i chose 1GB for the swap partition simply because i did not forsee doing anything really intensive in the OS so that it would need a large swap area.

with windows, the rules i've followed in the past for virtual memory were:

1GB ram --> 2048MB fixed pagefile
2GB ram --> 1024MB fixed pagefile
3&4GB ram --> 512MB fixed pagefile

i assigned 1GB to the swap area during ubuntu install just in case 512 turns out not to be enough....

---

### Post by logos34 on 2009-05-12
Here's the [swap reqs]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?") in linux.

Based on my personal experience, my own rule of thumb for swap size:

2 x RAM (up to 512 MB RAM)
1.5 x RAM (up to 768 MB RAM)
1 x RAM (1 GB RAM or more)

Like they said above, you should be fine with 1 GB if you never use hibernate.  With all that disk space I'd just keep the swap.  Maybe you'll need it sometime.

---

