---
title: "Last major problem with laptop: cannot suspend"
date: 2011-01-05
forum: Hardware
---

### Post by Quadunit404 on 2011-01-05
When I try to suspend, I get this rather under-detailed error message:

> Computer failed to suspend.

Failure was reported as: Cannot suspend

Along with that, the options to suspend and hibernate are not in the Power menu. I wonder where they could have gone...

Laptop is, once again, a Samsung NP-RF510. I already got the issues with the keyboard, touchpad and brightness control sorted out, now I just need to fix suspending and hibernating.

And no, s2ram doesn't work. If I try it it says this:

```
tom@tom-laptop-linux:~$ sudo s2ram
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "SAMSUNG ELECTRONICS CO., LTD."
    sys_product  = "RF510/RF410/RF710          "
    sys_version  = "Not Applicable"
    bios_version = "01GB.M013.20100905.hkk"
See http://suspend.sf.net/s2ram-support.html for details.

If you report a problem, please include the complete output above.
```

---

### Post by 3602 on 2011-01-05
Seems like you're using laptop-mode-tools. Read this:
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307)
Posts #11 and #13. I have the same problem and installed the re-rolled package. A lingering problem you're going to get is that you cannot update that after installation.

---

### Post by Quadunit404 on 2011-01-05
Installed that and Update Manager still works just fine. I just finished installing six updates. One of them was the pm-utils in the repos, but since that conflicts with laptop mode, why would I want that?

Gonna test suspending now.

EDIT: Nope, still doesn't work. Performance is horrible now. Gonna try rebooting to see if this is a temporary issue... yep, performance was temporary. Restarting solved it. Now time to see if suspend works... [DUN, DUN, DUN, DUN, DUNDUNDUNDUN, **DUUUUUUN.**]("http://www.youtube.com/watch?v=3853FW88kHQ")

---

### Post by 3602 on 2011-01-05
> **Quadunit404 said:**
> Installed that and Update Manager still works just fine. I just finished installing six updates. One of them was the pm-utils in the repos _**[...]**_[]("http://www.youtube.com/watch?v=3853FW88kHQ")

Exactly what I meant. It won't work.

---

