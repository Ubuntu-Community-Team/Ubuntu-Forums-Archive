---
title: "MacBook problems with sleep/suspend using Ubuntu Edgy"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by jsilve1 on 2006-12-01
Hey, all. Mucho thanks to Stefan D Swartz's excellent HowTo to get Edgy running on my MacBook.

It works! Yay!

Now, I have a very strange problem, regarding Sleep (Suspend). The MacBook goes into Sleep (or "Suspend to RAM") perfectly fine.  A little inconsistent sometimes, but it pretty much Just Works(TM).

EXCEPT

I created a second user, and Sleep sotpped working!

Steps to recreate problem:

1) System->Administration->Users and Groups
2) Create user, username "fred", user id 1100

Now, try sleeping. Either right-click on the Gnome Power Manager icon and choose "Suspend" or close the lid. Sleep no longer works!!

Steps to get Sleep working again:

1) Open terminal
2) sudo userdel -r fred

Might have to reboot, i dunno, (as in not confirmed), but after deleting this second user, Sleep works again.

Can anyone else verify this problem?

I have actually reinstalled Edgy twice after losing the ability to Sleep and I have kept fairly careful logs of things I've installed, assuming that extra software might affect sleep (for example, the "macbook-backlight-hal" package definitely does).  But I was able to confirm that no other extra software I installed affected Sleep.

Argh. So frustrating.

Okay, thanks. Later...

---

