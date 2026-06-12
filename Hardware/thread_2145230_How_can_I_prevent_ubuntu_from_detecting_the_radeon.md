---
title: "How can I prevent ubuntu from detecting the radeon card"
date: 2013-05-14
forum: Hardware
---

### Post by jmatta on 2013-05-14
Hello there,

Here's my problem, my laptop won't boot ubuntu, not anymore anyway.

I know the problem is with the discrete card (ATI 6770m) I believe there's a hardware failure in it, windows too hangs when I switch to it.

My workaround was to set the switch to 'Fixed' from the BIOS, then in the rc.local turn off the AMD at startup and use the integrated intel.

It used to work fine, but now it hangs after running the init-bottom script (it says done, so I guess the next thing kills the boot but it doesn't log it)

When I boot with nomodeset it opens the failsafe graphics with 1024*768.

So what can I do to prevent linux from pinging (or whatever term it is) the discrete card at boot?

---

### Post by tgalati4 on 2013-05-14
You could put "radeon" in the /etc/modprobe.d/blacklist.conf.

Verify what you are running for a video driver:

Open a terminal:

```
lsmod
```

---

