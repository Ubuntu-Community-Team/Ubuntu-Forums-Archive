---
title: "Thinkpad won't suspend after installing ssd"
date: 2010-02-21
forum: Hardware
---

### Post by scottbot84 on 2010-02-21
Hi all,

Just got a new thinkpad sl510, and added an SSD (intel g1 x-18m from newegg). 

Everything works great except for suspend to ram. I had used it previuosly before installing the ssd, and everything worked fine.

I did make a few optimizations for the ssd, mostly laid out 

[here]("http://en.dogeno.us/2010/01/karmic-with-solid-state-disk-how-to-optimize-ubuntu-for-ssd/")

I'm thinking it has to do w/ using a ramdisk for temp files, or with the ssd itself.

Boot time right now is about 20s, so its not a huge issue, but I like being able to use all of my laptops's functionality if I choose to.

---

### Post by IcarusR on 2010-02-21
> I'm thinking it has to do w/ using a ramdisk for temp files
Could revert back to temp files on ssd to possibly eliminate this as a cause.

---

### Post by scottbot84 on 2010-02-21
Nope, its not the tmpfs

I reverted everything I could to pre-ssd, no dice. Maybe it wasn't working before I'm not sure now.

Also I learned its a bad idea to remove folders in /var , like / var/cache. Sometimes I have no common sense.

looking at the logs that were generated, I didn't see any error messages, however.

Oh well, maybe it will be fixed in Lucid. Its not a deal breaker for me.

---

