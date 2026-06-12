---
title: "Swiftweasel does not start even after .deb is installed/ tar.gz file is extracted+ran"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by Happy-Dude on 2009-04-04
Hiya guys!!

Since I am on a Pentium3 machine with 384MB, I decided that I should be running an optimized build for my machine. Not necessarily for the benchmarks, but rather for the responsiveness and the feel of starting up/ browsing with the browser. (I have an optimized build on Windows XP for SSE2 Pentium4, and let me tell you, the difference is responsiveness is phenomenal.)

Originally, I was running Swiftfox 3.0.4pre, and it worked nicely, and some performance improvements were observed. However, I've uninstalled it in favor of Swiftweasel, which is more opensource and as of now, updated to Firefox 3.0.8.

My problem now is that Swiftweasel won't run. I got the INTEL PGO tarball builds from [http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473) , and running ./swiftweasel doesn't not work. I thought I was doing something wrong, so I tried a .deb file from [http://ompolicy.altervista.org/ubuntu/index.php?dir=intrepid/](http://ompolicy.altervista.org/ubuntu/index.php?dir=intrepid/) .

The .deb installed correctly, icons on app menu, etc. However, when I click Swiftweasel and wait for it to start, I only see "Starting Swiftweasel 3..." on the panel, and then after like 5 seconds, it disappears and apparently terminates. (ps -A shows no swiftweasel process.)

So something is definitely wrong, more specifically, with my machine and how its running the scripts/programs. I know others have been successful with running the tarballs, and I wonder why mine doesn't start at all...

It would be a great help to me if someone can help diagnose this issue with me. I'm wondering a great deal why my machine won't run Swiftweasel, even when the folders/profiles/icons/installation seems to be alright.

Thanks very much, guys :) !! I will provide as many system details as you would need; I disabled a bunch of services and such (in order to make Ubuntu run faster)-- so feel free to ask what I'm running/ my system setup.

I have: 
Linux Ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
Intel Pentium3 Coppermine 1.0GHz
384MB RAM

PS--
Here is what I get when running swiftweasel3 from the terminal (after ompolicy's .deb install):
c@Ubuntu:~$ swiftweasel3 
/usr/local/swiftweasel3/swiftweasel-bin: Symbol `SSL_ImplementedCiphers' has different size in shared object, consider re-linking
Illegal instruction
c@Ubuntu:~$ 
And that's about it-- no browser starting at all (>.>)....

Thanks guys!! I really appreciate it :) !!

---

### Post by prohna on 2009-04-05
i just installed and im getting the same error.

---

### Post by Happy-Dude on 2009-04-05
Thing is, does the browser even start for you?

I was on IRC support, and someone was able to run it even with the error. I apparently am running into a problem even starting the thing...

---

### Post by d_yat on 2009-09-05
Hello!
I too have this problem! Stupid "Illegal Instruction"
although, I have a few machines. and this is what I have discovered so far.
my parents' 9.04 Jaunty machine will not run SwiftWeasel, however, my laptop with Hardy (8.04) does, with no "Illegal Instruction". What have you guys been running it on?
Also, both machines I've used are AMD processors. but as Happy-Dude is using a pentium, I don't think that is the problem. What do you guys think?

weirdness...

---

