---
title: "New drives for my Raid 10 rig"
date: 2009-04-15
forum: Hardware
---

### Post by kaffemonster on 2009-04-15
Well here's a funny one for you all...

I dug up a retired server at work. IBM eServer, Pentium 4, 2.8 Ghz with 512mb of ram, nothing too fancy. But lo and behold, it had a PCIX gbit lan card sitting right beside a PCIX Adaptec SATA raid controller. Hello file server!

I had 4 250gb sata hard drives so I configured them as a raid 10 array and installed Ubuntu 9.04. It is running smoothly in my basement now, serving files like there's no tomorrow.

But here comes the funny part: I'm currently using about 260gb of the 500gb I have available. I'd love to switch from the 4 x 250gb setup to 4 x 1tb drives. How do I do that the smart way?

If I just exchange the drives one by one and let the raid rebuild itself, I'm afraid I'll just end up with a 500gb array on 4 tb of drives.

If I start from scratch, I'll need to configure the server from scratch. Doable, but kinda boring.

Could something like Symantec Ghost handle the whole thing? A ghost image of the current setup loaded onto a new 4 x 1tb raid?

Is there a fancy backup killer app I should know about that will let me take a backup of the entire system, do a fresh install of Ubuntu and then reload said backup onto the new install?

---

