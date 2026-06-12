---
title: "Hard drive reading issue, &quot;blacklist&quot; a section"
date: 2008-08-23
forum: Hardware
---

### Post by Diabolis on 2008-08-23
My drive used to look like this:
[COLOR="Red"]7gB[/COLOR] | **22 gB** | 7gB | 1gB

A couple of days ago I dropped my computer by accident. Seemed like everything was ok for a while, but suddenly it locked up (the screen was frozen) and I couldn't boot up.

I used a live-cd to reinstall ubuntu, and everything went smooth and easy as usual. It didn't complete about anything. Still, I couldn't boot up.

Then I plugged in a external drive and booted from it, I installed Ubuntu in it a while a go as a rescue drive. The good thing is that from that installation I can access all my files on the "broken" drive.

I figured that just a small part of my drive is broken/scratched. What I did then was to partition my drive like this:

[COLOR="Red"]7gB[/COLOR] | **7gB | 15gB** | 7gB | 1gB

I installed Ubuntu on the newly created 7gB partition and now I was able to boot up, everything works perfectly.

So actually my question is:

**Is it possible to find out exactly which are the parts of the drive that don't work anymore? If so, is there a way to "blacklist" them?**

I have run fsck a couple of times over the 7gB partition, but seems like is not enough. Also all the partitioning has been done with gparted, which, to my understanding, also checks the partitions every time they are modified or resized.

---

