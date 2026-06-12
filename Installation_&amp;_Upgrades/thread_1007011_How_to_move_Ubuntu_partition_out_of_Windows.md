---
title: "How to move Ubuntu partition out of Windows?"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by kolslorr on 2008-12-10
Hello,

Sorry about the bad title, but i just couldnt find the right sentence for what I am looking for.

Story being, I installed Ubuntu on my new shiny HP laptop via Wubi, i.e. installed Ubuntu within Windows partition. 

Now, I am thinking if its possible for me to move my whole Ubuntu OS out of the Windows partition, to 1 whole new partition of itself.

I have no particular reason of wanting to do that, my system is working fine as it is, just that I figured this might be a better structure. I have no plans to ditch the Windows Vista that came with the machine though. :)

---

### Post by iaculallad on 2008-12-10
Follow up with this previous thread:  [LVPM: Upgrades Wubi installs to dedicated-partition Ubuntu installs]("http://ubuntuforums.org/showthread.php?t=438591")

HTH

---

### Post by kolslorr on 2008-12-10
Thanks, this looks like a lot effort, but very clear!

I guess I will do it only when I have a bit more time....

---

### Post by Mark Phelps on 2008-12-10
Just make sure that you do NOT use the LiveCD installer, or any other Linux utility to "shrink" your Vista partition to make room for Ubuntu -- unless you have a Vista DVD or Vista Recovery CD handy.  Why? Because all to often, shrinking a Vista partition using GParted (or anything similar) "breaks" the Vista partition such that you have to then reboot using one of the Vista disks and do a Startup Repair to get Vista to boot again.

If you have trouble getting Vista to shrink the partition, try running a defrag and turning off hibernation (and removing the hiberfil.sys file).  That should free up space at the "end" of the Vista partition, allowing you to shrink it.

---

