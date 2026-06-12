---
title: "[SOLVED] apt-build with distcc"
date: 2008-10-27
forum: General Help
---

### Post by walmartshopper67 on 2008-10-27
I put Ubuntu (Hardy) on an old Pentium 3. It's pretty slow for the work we're doing (running vmware to test code), so i figured i would try 'apt-build world' to recompile the system with some optimization settings. Being a Pentium 3, it would take forever. So I found the "[dstcc]("http://en.wikipedia.org/wiki/Distcc")" application to spread the compiling around our network. For the life of me i cant get distcc and apt-build to work together. I tried googling it, but came up empty. Is there a setting or a command line argument i'm missing?

---

### Post by shjoity on 2008-11-21
i was having the same problem and have no idea how to fix it, with the new distcc it is suppose to use avahi but it stil does not work

---

### Post by walmartshopper67 on 2008-11-22
I got it to work! Finally! 

shjoity (and anyone else looking):

Check out the bottom post on this archive thread: [http://ubuntuforums.org/archive/index.php/t-247416.html](http://ubuntuforums.org/archive/index.php/t-247416.html)


Now, when running it, the key seemed to be running it with the --nowrapper option, I *think* the default wrapper is what is screwing us up, maybe it calls gcc directly or something. 

If you still can't get it, let me know, i can post config files or whatever you need.

---

