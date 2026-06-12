---
title: "Which packages to install to compile drivers"
date: 2008-09-20
forum: General Help
---

### Post by 5circles on 2008-09-20
How do I figure out which packages I need to install to be able to compile a driver module from source?  I'm trying to reinstall the Realtek R8168 driver that I had working on Ubuntu 8.04 before I reloaded the operating system.  I was successful before, but I can't figure it out this time (probably been spending too much time with Windows for the past couple of months).

I'm following the instructions in [http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html), and getting errors that suggest I don't have the right things installed > "This may fail if you don’t have kernel headers and other standard features of a build environment."

But how do I figure out which of the many modules to install?  The first error I see in the output from 'make modules' is "implicit declaration of function 'SET_MODULE_OWNER'"

Thanks!
Mike

---

### Post by S.A.A on 2008-09-20
Use this:
```
sudo apt-get install build-essential
```

---

### Post by 5circles on 2008-09-20
Thanks for the speedy reply.  

When I try to run this, it looks like there are some missing pieces that would be installed, but apt-get tries to pull from the Internet rather than the CDROM.  Since Internet access isn't working (that's what I'm trying to fix) it just gets stuck.

I've looked at sources.list, and the CDROM source is there.

How can I stop apt-get trying to use the Internet?

---

### Post by 5circles on 2008-09-20
After figuring out what System | Administration | Software sources did, I unchecked all except the Cdrom.  (there were two copies of the CDrom entry for some reason).  Then I edited the sources.list file to clean up.  [apt-get update said it would clear up the problem but didn't]

I completed the apt-get install build-essential with no problem.

But the errors are still showing up.

---

### Post by oldos2er on 2008-09-20
Can you copy and paste the errors here?

---

### Post by 5circles on 2008-09-20
> **oldos2er said:**
> Can you copy and paste the errors here?

I have to manually enter because the network isn't working, so hopefully this is accurate.

I'm getting error messages when running 'make modules'. The first error shows up in r8168_n.c, in function rtl8168_init_board,

> error: implicit declaration of function 'SET_MODULE_OWNER'

This file has a bunch of include statements at the beginning, of the following form:

#include <linux/module.h>

My programming skills are really rusty, so I hope someone can just say 'aha'

Thanks!

---

