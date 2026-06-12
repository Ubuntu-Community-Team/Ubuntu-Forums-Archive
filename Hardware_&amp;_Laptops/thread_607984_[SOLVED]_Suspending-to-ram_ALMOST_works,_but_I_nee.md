---
title: "[SOLVED] Suspending-to-ram ALMOST works, but I need help..."
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by TheMusicGuy on 2007-11-09
Hi,

I have a Compal HEL 80-based laptop and I am trying to get it to suspend when closing the lid or using the option in the logout menu of Gnome.

I was able to get this to work using KDE and KLaptop, but after I switched to Ubuntu it no longer can suspend or hibernate. All it does is 

When I try this command (found in another thread):
sudo hibernate -F /etc/hibernate/ram.conf

I get the following output:
/usr/sbin/hibernate: 837: arch: not found
/usr/sbin/hibernate: 888: arch: not found
Some modules failed to unload: nvidia ipw3945
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).

So I tried the --force option and it made it suspend, but in a kind of brutish way. (Eg. just before it suspends the screen freaks out like the driver just got slapped in the face)

So...I dunno. I guess what I'm asking is how do I change the Gnome built-in suspend commands (close lid, click "suspend" in logout menu) to use one of the commands that can successfully suspend my laptop?

Thank you.

---

### Post by angelofhope on 2007-12-08
HI, I had the somewhat the same problem, when I tried to hibernate, it complained about being unable to unload nvidia and ipw3945.
I started looking in /etc/hibernate/ and changed the common.conf:

UnloadBlacklistedModules no

This seemed to work just now, I hope it keeps working :)

---

### Post by TheMusicGuy on 2007-12-09
Angelofhope:
That's good to know...I found another solution, though: reformat and reinstall the OS. :lol:
Yeah...I was having so many issues after (and *during*) the upgrade to 7.10 that I decided it would be less work to just do a fresh install. It actually wasn't as big of a job as I thought to do it, and now lots of problems that I have been having for months are basically gone (though a couple new ones did show up...oh well.)

...but thanks anyway! ^_^

---

