---
title: "Run Hardy under older kernel?"
date: 2008-12-27
forum: Hardware
---

### Post by igeterrors on 2008-12-27
Just upgraded from Gutsy to Hardy and suspend stopped working (HP Pavilion dv1000 laptop). But when I boot into 2.6.22-16-386 (instead of the default 2.6.24-22-386) I don't have a problem. Is there any reason I shouldn't continue to do this? I need to be able to suspend my laptop.

---

### Post by Rocket2DMn on 2008-12-27
There isn't really any reason to not boot into an old kernel if it works better.  Do the -generic kernels not work for you, most people don't specifically use -386 kernels.

---

### Post by igeterrors on 2008-12-27
> **Rocket2DMn said:**
> There isn't really any reason to not boot into an old kernel if it works better.  Do the -generic kernels not work for you, most people don't specifically use -386 kernels.

Didn't try, actually. When I upgraded, the -386 version was automatically placed at the top of my menu.lst file so that's what I booted into. I'll try the generic, but as long as the 2.6.22 works, I should be ok? Mainly in terms of security or whatever. There's no danger in using 2.6.22 as long as my computer seems to be functioning ok with it?

---

### Post by Rocket2DMn on 2008-12-27
Each kernel upgrade includes various patches and improvements, but the bottom line is - use what works for you!  Gutsy Gibbon is still supported for a few months, so is its kernel.  If you run into problems down the road that you think may be related to the kernel, then you will need to try and fix the problem.  This could include trying newer kernels in Intrepid or even Jaunty testing (not a stable release!).  You should be able to test that functionality from a LiveCD of one of those versions.

You can also file a bug report on Launchpad, esp. since this a regression in functionality.  There is a link in my signature if you need help with filing bug reports.  If you do file a bug, please feel free to post a link to it in this thread.  Note that representatives from the kernel team will probably want you to test the latest kernel from Jaunty by using a LiveCD once the bug triage is complete.

---

