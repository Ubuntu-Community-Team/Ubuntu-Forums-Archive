---
title: "Screwed the pooch by deleting Hostname?"
date: 2005-11-21
forum: General Help
---

### Post by JimMartin on 2005-11-21
Okay, so maybe I made a little mistake.... In trying to resolve my network isssues (see post 505955) I got to messing with my server info and for some reason deleted my hostname. 

Now I can't even get in to edit it. Can't run anything as root and can't get to networking through the gui. 

Forgive me, I have deleted. Please tell me there is a simple fix somewhat less dramatic than reinstall.

Thanks,

Jim

---

### Post by 23meg on 2005-11-21
Put the following into your /etc/hosts file:
```
127.0.0.1 localhost.localdomain localhost YOURCOMPUTERNAME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by RAOF on 2005-11-21
You're in luck.  All you need to do is boot in single-user mode, where you will be root, and then you can edit the files to your heart's content.

Now, in order to boot into single-user mode, I believe you want to reboot, and in grub (**before** it says "loading linux", etc) select one of the kernels marked "Ubuntu, kernel 2.blah.something (recovery mode)".  You'll boot into the console, in single user mode, as root.

---

### Post by everdred on 2005-11-21
I did essentially the same thing about a week ago. And while the advice the two above commenters left is sound, it might not be the easiest to follow. (In short, first follow RAOF's advice, then 23meg's.)

Or, for a complete walkthrough re: editing your hosts file from the command line, see [my post]("http://ubuntuforums.org/forumdisplay.php?f=90") from last week.

---

### Post by JimMartin on 2005-11-21
Thanks guys I'll give it another try this evening.

Cheers,

Jim

---

