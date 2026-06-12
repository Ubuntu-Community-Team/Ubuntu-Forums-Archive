---
title: "powersave vs kpowersave?"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by hizaguchi on 2006-08-25
Ok, I'm a little confused on something.  In other distros (Arch and Suse), I am able to suspend to ram without any problems using "powersave -u".  In Suse (and probably Arch, but it won't compile), I'm able to also suspend using kpowersave, and it appears to be using the same command because it switches me to a console and says "stopping tasks..."  However, in Ubuntu I am not able to suspend using kpowersave... it doesn't even act like it is using the same command as kpowersave in Suse.

This is where you come in.  I've replaced my Ubuntu install with Arch for the sole purpose of having a working suspend.  It was during my Arch configuration that I learned that different suspend commands even existed, and that the one that I need is "powersave -u".  Since Ubuntu is already gone, I can't test that command for myself without reinstalling, so I'm wondering if somebody could give it a try for me.

If you have installed powersave and kpowersave, could you please try suspending by doing "powersave -u" (or "sudo powersave -u") and compare that to the behavior of suspend to ram through kpowersave?  Or even better, does anybody know for sure what method kpowersave uses to suspend?

Thanks!

---

### Post by hizaguchi on 2006-08-27
Shameless bump.  Am I the only one who needs powersave for suspend to work?

---

### Post by ltmon on 2006-08-27
I'm not much of an expert in this, and i've just been randomly playing with options to get my suspend to ram to work.

Kpowersave is a front end to the powersave daemon, which I think can use multiple backends for doing stuff.

I am using the "s2ram" backend, which I got by compiling and installing it.  I think it usually just uses the powersave method.

But to get more in-depth information look at /usr/share/doc/powersaved/html/Suspend2Ram.html

It has some information for debugging.

I also got help from: [http://en.opensuse.org/Projects_Powersave](http://en.opensuse.org/Projects_Powersave) and [http://en.opensuse.org/Powersave_s2ram](http://en.opensuse.org/Powersave_s2ram)

L.

---

### Post by hizaguchi on 2006-08-28
Thanks.  Do I need to do anything to tell powersave to use the s2ram backend, other than just installing it?

---

### Post by ltmon on 2006-08-28
I think that it is used as long as it exists in /usr/sbin/s2ram.

You can configure it's behaviour somewhat in the file /etc/powersave/sleep.

L.

---

