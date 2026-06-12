---
title: "Must hold down key to boot"
date: 2008-11-08
forum: General Help
---

### Post by Totenglocke on 2008-11-08
I've used a few different versions of Ubuntu and just reformatted my new laptop to ditch Vista and I installed XP and Intrepid.  When I boot into Intrepid, I have to hold down a key (any key) to get the progress bar to move.  If I don't, it just sits there and never boots.  Any ideas how to fix this?

---

### Post by gkrules on 2008-11-08
I have the same problem on a Compaq F756NR notebook.
It is dualbooting Vista and Intrepid.
In Intrepid, I have to hold down a button for it to boot.
It worked fine when I was dualbooting Hardy and Vista.
I format my harddrive every 6 months for the new release of Ubuntu, so it was a clean install.

Another laptop I have, a Dell B130 doesn't have the problem, it boots fine, but I am not dual booting on this one.

---

### Post by Totenglocke on 2008-11-08
Mine is a Compaq 767NR, so maybe it's a Compaq issue?

---

### Post by maxovride on 2008-11-08
i have a similar issue with my laptop. 8.10 with a upgrade install will not butt unless i hold down a key but then i start getting readonly errors and i cant go any further.  i cant even get the install disk to boot so i can install it from the cd.  here is a link to a post i made about this [http://ubuntuforums.org/showthread.php?t=974324](http://ubuntuforums.org/showthread.php?t=974324) i am continueing to work on this, and if anyone else figures this out please let me know.

---

### Post by Dillon on 2008-11-09
i have the same issue on an HP dv6500.  I have to hold enter to get it to boot. Problem is occuring with Kubuntu 8.10 that is fully upgraded

---

### Post by teddks on 2008-11-09
Same issue with me, on an HP dv9500. The problem starts just before the system prompts me for my encryption password, and from then on, I have to hold a key down to boot.

other info:

[list]
[*] This happens with or without usplash, however, without usplash, I only seem to need to hold a key during early boot processes. When the system starts running init scripts, I'm fine.
[*] I can see if there is activity by looking at the HD activity LED. It seems that I only need to hold a key during transitioning periods of the boot, between certain procedures.
[/list]

I'd really love to file a bug for this; but I have no idea if it's known or what package to put it in.

---

### Post by Anarxi on 2008-11-23
same with presario F7XX

kernel bug

---

### Post by cloudpjff7 on 2008-11-27
Hello, I have an hp dv6748us model laptop, and I also have this problem.  It would be nice to see some kind of fix.

---

### Post by Drooling_Sheep on 2008-12-23
I just started having this problem today.  I'm not sure if it's the new packages from the latest update or if it's because I booted it on battery, which I don't normally do.

---

### Post by toydolls0101 on 2009-01-16
I am having the same problem with the latest version of openSUSE 11.1

I have done some research and this is a cross-distro problem with all the latest versions of each. I'll let you know if I find a solution.

---

### Post by SoCalChris on 2009-01-16
It's fixed in kernel 2.6.28, which is in the Jaunty alpha, but has not been back ported to Intrepid yet.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247)

---

