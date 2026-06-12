---
title: "CPU and RAM relationship"
date: 2012-09-30
forum: Hardware
---

### Post by uncleheinz on 2012-09-30
Hello,

I wish to increase the speed of a laptop which currently has about 1.3 GHz (or 1.5 GHz) processor and exactly 1GB RAM.

My very first thought was to add a new and much powerful memory chip, let's say 5GB or even higher.

But then a question popped out: does the amount of RAM need to have some correlation with the speed of a processor? For example: if processor itself is not very powerful, then how helpful will it actally be if I add remarkably huge amount of memory?

Sorry if this question seems a little too naive. Hardware issue is not my biggest strength.

---

### Post by lykwydchykyn on 2012-09-30
There isn't really a correlation, but there is a point of diminishing returns. 

Think of your CPU as a worker, the RAM as his office, and the Hard drive as a file room on the other side of the building.  If the worker has a small office, and has to keep running back to the file room to get or return files, then he's not working very efficiently.  The bigger the office, the less often he has to run back to the file room to get things.  But if his office is already big enough to store all the files he needs to do his work, making it bigger doesn't really speed things up any more.

The other, less abstract factor, is the fact that 32 bit processors and OS's don't deal with more than 4 GB of memory space very efficiently; they have to use a special patch called PAE, which isn't even supported by all processors.

So if you have a 32bit processor and are running 32 bit Ubuntu (or Windows), it's not really worth going beyond 4 GB unless you're doing memory-intensive stuff (like running a VM), IMHO.

---

### Post by uncleheinz on 2012-09-30
> **lykwydchykyn said:**
> ...the fact that 32 bit processors and OS's don't deal with more than 4 GB of memory space very efficiently...

As I see my suspicions were not so wrong after all. So I guess that 2GB or 3GB RAM seems to be right amount in this particular case?

---

### Post by cwsnyder on 2012-09-30
Whether you need more than 1G RAM depends on your actual application load and how you use your laptop.  If you like to keep 10+ tabs open in your browser(s), or 5+ documents open in LibreOffice, transcode videos, or similar work, definitely go with as much RAM as possible.  For single document work of less than 10 pages, light Internet browsing, etc. 1G RAM will probably suffice, and you should probably look more at the applications you are running rather than updating either your processor or RAM.  Use Gnumeric/Abiword in place of LibreOffice, unless you need the extra features/packages in LibreOffice, or other lighter weight alternatives, turn off that rotating cube desktop, turn off Compiz and go to the Xfce or LXDE desktop, and you will probably find your laptop has a new lease on life.

---

### Post by deadflowr on 2012-09-30
More RAM won't necessarily give you more speed.
It will give more space to fill up.
To increase speed you'll need to look at maximizing the RAM speed to your systems full capacity.
If your systems max RAM speed is say 667mhz, then look for RAM marked as 667mhz. 
To give an example, I had two pentium4 pcs, one had 1gb of RAM with speed of 533mhz, and the other had 2gb at 400mhz. The PC with 533mhz was much faster. And that's because the RAM was faster. However, when I exceeded the amount of RAM I needed, the system did slow down.
So in the end, I'd say, look over your systems specs to find out the highest level speed your system can run, and then get RAM that matches that.

---

### Post by j0eb0b on 2012-09-30
I have found that adding memory to old hardware is one of the best upgrades you can make, unless the memory sticks are prohibitively expensive.  If your CPU runs at 1.3 GHZ it is almost certainly a 32 bit processor.  It is unlikely the motherboard this processor is attached to will support a high speed chip like the 5GHZ you were thinking of getting so additional memory is probably the only upgrade available.  2 to 3 GB of memory should offer  improvement. Once you add memory you may want to experiment with the virtual memory size.  Here is a link to an explanation VM changes that may be beneficial.  I use the "swapiness" value of 10 on my laptop (HP NC 6400 with 2GB) and it improves the general performance.

[http://ubuntuguide.net/optimize-the-usage-of-swap-to-speed-up-response-for-ubuntu](http://ubuntuguide.net/optimize-the-usage-of-swap-to-speed-up-response-for-ubuntu)

---

