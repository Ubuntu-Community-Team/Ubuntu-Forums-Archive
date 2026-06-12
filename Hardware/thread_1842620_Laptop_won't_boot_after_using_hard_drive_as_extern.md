---
title: "Laptop won't boot after using hard drive as external mamory"
date: 2011-09-11
forum: Hardware
---

### Post by jakerman999 on 2011-09-11
I broke the screen in my laptop(Acer Aspire 5745:dual booting W7 and Ubuntu) a while ago, and while waiting for the replacement to come in I was using the hard drive in an external bay for my desktop computer(A full Ubuntu machine).  I replaced the screen and hard drive yesterday, but booting into Ubuntu hangs at a black screen.  Trying to load a previous kernel version throws the error:
```
error: couldn't read file.
error: you need to load the kernel first.

Press any key to continue...
```

And it kicks me back into grub after a short second.  Trying to load recovery mode tells me it's loading the kernel, then it hangs and requires a hard reset.  I tried editing the commands before booting, and took out "quiet" for a diagnosis, this is what it threw:
```
Loading, please wait...
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
```

What I'm thinking of doing is putting the hard drive back in the bay and loading the newest kernel and and init scripts in by hand, but I don't know how to do that, or even if it's the right course of action.  Any help getting this to boot again would be much appreciated.

---

