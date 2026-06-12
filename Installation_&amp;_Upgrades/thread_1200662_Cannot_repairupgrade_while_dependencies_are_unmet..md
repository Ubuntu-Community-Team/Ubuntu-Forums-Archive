---
title: "Cannot repair/upgrade while dependencies are unmet. How to fix?"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by Redsandro on 2009-06-30
Hi,

I have Ubuntu 8.04 running for a long time now on my server. When I wanted to update the old *Gnome Planner* from the repo to the latest *0.14.4* one, I had one *"unsatisfied dependency"* for **libgconf2-4**.

I had this probably stupid idea that a new libgconf was backwars compatible so I upgraded that. Suddenly I had many problems and the terminal told me to run *"apt-get install -f"*

This command gave many more problems and quit with a message *"too many errors, quitting."*



The target computer is a hidden away server without monitor or keyboard and I'm doing everything through **putty** or **vnc**. Ever since the first dependency problem it won't boot into gui anymore (probably my session won't start) so I can only use the terminal through putty.

I just want it back to normal, or upgraded. I don't really care because it worked perfectly for what it was supposed to do.

I don't just want to do a reinstall, because there's a LOT of data spread out in /var, a lot of scripts running in my main autologin session, and probably a lot of customizations I am forgetting right now. A reinstall causes all partitions except /home to be reformatted.



I figured a dist-upgrade might as well fix the problems, so I tried one. Errors suggested to run **dpkg --configure -a**. But when I do, a few hundred packages get parsed each with this output:
```

Removing [whatever] ...
gconftool-2: symbol lookup error: /usr/lib/libgconf-2.so.4: undefined symbol: g_dgettext
dpkg: error processing [whatever] (--remove):
 subprocess pre-removal script returned error exit status 127

```

There you have it, all errors based on the package that was unmet in the first place and is now bad because I messed with it, and I don't know what is all messed because of the -f and -a fixes I tried.



Can I still fix this?

---

