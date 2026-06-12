---
title: "problem after enabling laptop_mode"
date: 2008-11-25
forum: Hardware
---

### Post by Ryan2009 on 2008-11-25
Running fresh install of Ubuntu 8.10.  I notice with laptop_mode enabled that my hard drive is spinning up and down quite a lot.

Just simple browsing whenever I go from one page to another it spins up then down again.

Anyone have any ideas on how to fix this so it doesn't power on and off so much?

I also notice that when the hdd does spin up, the computer stops responding for about half a second.

Using a Dell Latitude D620.

---

### Post by Ryan2009 on 2008-11-25
anyone?

---

### Post by iggykoopa on 2008-11-25
If your using firefox (you said browsing) it's probably the cache, you can try turning off the cache if you want. Go to about:config and set this network.http.use-cache = false or you can try out a python script I wrote(if your willing to test it out, I know it works on my machine) [http://www.planetwatt.com/index.php?name=PNphpBB2&file=viewtopic&t=51](http://www.planetwatt.com/index.php?name=PNphpBB2&file=viewtopic&t=51) here. It loads the firefox cache into a ramdisk then copies it back when you close firefox. Just follow the instructions on that page.

---

### Post by Ryan2009 on 2008-11-26
I disabled the network.http.use-cache (set to false) and the hdd still spins up and spins down when I am browsing.  I don't have any other programs running. 

not sure how to find out what is polling the hdd.

is there any way to increase the duration before the hdd goes idle?

---

### Post by jpkotta on 2008-11-26
This will start logging all the processes that hit the hard drive.
```
echo 1 | sudo tee /proc/sys/vm/block_dump
tail -f /var/log/messages
```

There are tips at lesswatts.org about how to minimize hdd activity.

---

