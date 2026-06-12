---
title: "No more drivers"
date: 2012-02-14
forum: Hardware
---

### Post by Puroko on 2012-02-14
So, here is my problem, maybe someone is able to help with that:

I am using ubuntu 11.10. Everything worked fine so far
When I booted my laptop this weekend, it didn't seem to boot properly. But it did, it only happened the actual desktop environment didn't start.

After using startx I can at least access that one now. But so far I realized some other problems with that: I can't mount external drives, the sound didn't work and I can't change anything about the users.

Now, I fixed the sound with
chmod -R a+rwX /dev/snd
after noticing that aplay -l does not work, but sudo aplay -l does.

So, all my drivers are here, but they don't seem to get connected with my account anymore. I have no idea how that happened or what to do about it. The last thing before the last proper shut down was to change the automatic login of my account to on.

Has anyone an idea about this? Help is very much appreciated.
(Or need some additional information?)

---

