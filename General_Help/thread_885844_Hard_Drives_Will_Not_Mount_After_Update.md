---
title: "Hard Drives Will Not Mount After Update"
date: 2008-08-10
forum: General Help
---

### Post by FrankP on 2008-08-10
I just updated Ubuntu having not used it for a while, and I find on the reboot I can not mount either of my two hard drives. Strange this, because Ubuntu is running off one of them! :D So I don\\\'t get how that is working.

I have a look at the /mnt/ directory and there are no devices listed (the only two that should show are not there, I do not have a DVD drive anymore). When I try to access either of the drives, it says:

\\\"
Cannot mount volume.
You are not privileged to mount this volume.
\\\"

Which is a damn pain seeing as I am using the root user.

Any ideas? Because I have none!

---

### Post by Twig E. Pottox on 2008-08-10
Are you running a dual boot system (XP /8.o4)? I had a similar problem and it was caused by not shutting down windows properly. When I started 8.04 it saw the windows drives as being in use and refused permission. oopening windows again and shutting it down properly should fix the problem.

---

