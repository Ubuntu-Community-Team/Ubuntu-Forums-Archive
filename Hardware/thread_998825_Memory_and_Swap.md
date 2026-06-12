---
title: "Memory and Swap"
date: 2008-12-01
forum: Hardware
---

### Post by Sprut1 on 2008-12-01
I just installed 2x1 gigs of ram in my laptop, now "free -m" outputs:

```

             total       used       free     shared    buffers     cached
Mem:           946        864         82          0         21        470
-/+ buffers/cache:        371        574
Swap:         1286         31       1255

```

Does that mean that I have 1gig memory total? Meaning that one of my RAM chips aren't been used? Or is the memory total mem+swap? Which will be over 2gig combined, this is a bit confusing.

---

### Post by albandy on 2008-12-01
For some reason your system is not detecting the module. Enter the BIOS and verify it.

Ensure you're using the correct module: speed, latency ...

---

### Post by Sprut1 on 2008-12-01
Okay I will check it out and report back, thanks! :)

---

### Post by linux_tech on 2008-12-01
According to output 946 you have 1 gb total; other 1 GB is not being detected.  1st look in bios to see if is recognized there, turn off (remove battery and unplug) then try reseating RAM.  Also make sure it is the correct type of RAM for your laptop.

---

### Post by Sprut1 on 2008-12-01
> **linux_tech said:**
> According to output 946 you have 1 gb total; other 1 GB is not being detected.  1st look in bios to see if is recognized there, turn off (remove battery and unplug) then try reseating RAM.  Also make sure it is the correct type of RAM for your laptop.

I checked bios and it states the same thing as my Kubuntu, 1gig. I did reseat the RAM, swapped the 2 chips' places and booted system, same thing. It has to be correct type since 1 chip is working while the other isnt? Is this a BIOS problem? The laptop support 2gig of ram out of the box.

Thanks for the help so far:)

---

### Post by taurus on 2008-12-01
If one is working and the other doesn't, then you have a dead RAM.

---

### Post by Sprut1 on 2008-12-01
> **taurus said:**
> If one is working and the other doesn't, then you have a dead RAM.

Ye I did fear that 1 might be dead, I'll try with 1 at the time and see what happens, thanks for the help all.

---

