---
title: "How to regenerate boot image?"
date: 2008-10-05
forum: General Help
---

### Post by bobmct on 2008-10-05
Gentlemen;
I run Kubuntu 8.04 and recently had an issue loosing my GUI upon boot.  Someone suggested booting into recovery mode and running the "fix X server" option followed by the "continue with normal boot".  That worked.
However, now when I reboot, if I don't use the recovery option first, it boots only into tty mode and the boot screen shows "fail" on a few items.

As the recovery fix for the X server seems to correct the issue, similar to other *nixes (I'm a trained AIX guy) there must be the ability to regenerate the boot image for the currently executing configuration.  Searches through this forum, other sites and perusing my Ubuntu books turn up nothing.

While I continue to search for this answer - perhaps someone more skilled with 'buntu can guide me to the right direction to resolve this.  

Thanks for any pointers provided - Bob

---

### Post by dsm iv tr on 2008-10-05
Please clarify what you mean by "boot image".

If you mean the initramfs that is loaded by the kernel:

```

sudo update-initramfs -u -v

```

while running under the kernel configuration you want to rebuild it for.

---

### Post by bobmct on 2008-10-05
Thanks - I tried that but no luck.  Here's what happens:

I reboot (either warm or cold).  The Kubuntu splash screen appears and eventually disappears replaced by a console display that shows several things starting.  However, it states that there is no hybernation image so it resorts to the standard image which it cannot find.  It then defaults to the tty login prompt.

At this point I ctrl+alt+del to restart and at the very first screen after the bios screen I press Esc which displays the Kubuntu start menu.  I select "continue with normal boot" and it goes through its normal stuff resulting in the KDE login prompt.  From that point on everything is A-OK.

Using your suggestion from the shell prompt I ran the command you stated and it appeared to run to normal completion.  But, another reboot without using recovery and its still not working.

Any other ideas/questions???

Bob

---

### Post by dsm iv tr on 2008-10-08
Unless you hibernate, there won't be a resume image for the kernel to use - that's normal.

It sounds like kdm isn't starting at boot. You can try reinstalling it and its initscripts after logging into your tty with your normal username and password.

```

sudo aptitude purge kdm
sudo aptitude install kdm

```

Reboot and see if KDM pops up again. If that doesn't solve the problem, you can always login to tty and then run

```

startkde

```

to get your desktop running again.

---

### Post by bobmct on 2008-10-09
Thanks dsm iv tr;

Did that - NO LUCK!  Same situation.  I've never seen this before.  I know there has got to be a method to correct and repair this and that's what I'm trying to determine.

Thanks for your suggestions though.

Bob

---

