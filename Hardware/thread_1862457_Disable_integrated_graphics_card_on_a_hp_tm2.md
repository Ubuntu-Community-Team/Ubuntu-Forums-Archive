---
title: "Disable integrated graphics card on a hp tm2"
date: 2011-10-16
forum: Hardware
---

### Post by dhjohn on 2011-10-16
I have a hp tm2 with a hybrid intel/ati graphics setup.
I want to run only the integrated graphics card and then install the proprietary drivers from "Hardware Drivers". I am attempting to run Ubuntu 11.10.

Any help would be greatly appreciated.

Thanks,
dhjohn

---

### Post by dhjohn on 2011-10-17
Bump? Anyone have any suggestions?

---

### Post by vedovatti on 2011-11-10
Hi there,

Check this: [http://ubuntuforums.org/showthread.php?t=1744188&page=5](http://ubuntuforums.org/showthread.php?t=1744188&page=5)

I have your same computer, using Ubuntu 11.10.

So recommendations about the switchable graphics. Seems property ATI does not support switchable graphics anymore and the only option is open-source drivers using vgswitcheroo.

On that forum do whats on the comment 14. It really works on the HP tm2. And then use the comment 27 to shutdown the computer without trouble.

For the clickpad check this forum: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809)

To make it work properly comment 275

And finally for the fingerprint we started developing a driver, let see if we can make it work 100%: [https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/744310](https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/744310) 

Bye

---

