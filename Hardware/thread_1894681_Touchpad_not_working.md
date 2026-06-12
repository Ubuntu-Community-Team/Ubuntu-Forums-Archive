---
title: "Touchpad not working"
date: 2011-12-13
forum: Hardware
---

### Post by vichor on 2011-12-13
Hi all,

I've got a Samsung NF210 netbook.I installed there Ubuntu Netbook edition which has been upgraded through time up to the last edition (Oneiric Oncelot, or whatever is written... I always forget). And I have a problem with the touchpad.

I've seen lots of other threads and webpages describing my problem, but the fix applied for them did not solve my problem. Besides, just yesterday I discovered a curious effect. Let's explain the whole thing.

After upgrading to Oneiric, the touchpad stopped working. The USB mouse works fine, but the touchpad is not working. It does not work either when disabling/enabling the touchpad through Fn+F10 key combination. 

I was most despaired and resigned to accept a non-working touchpad, but yesterday I created another user in the laptop and the touchpad works for this user! Alas, it is still not working for my user. 

So I think the problem is more related with some user configuration rather than a kernel/driver problem. I checked the applications launched at start up and both are the same (including synaptiks). As additional info, my user has administrative rights, while the new I created has not.

Any ideas? Should I delete some .whatever folder in my home directory?

Thanks
Victor

---

### Post by vichor on 2011-12-24
As I got no reply, I decided to go on and just create a new user for me. Copy all the files and change user/group ownership. Then, delete the old user with non-working touchpad and reconfigure my new one all again.

It worked, but I would have like knowing what happened there... another time, perhaps.

---

