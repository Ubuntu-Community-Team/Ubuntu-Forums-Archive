---
title: "No more ipw3945 wireless after kernel update"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by needhelpplease on 2007-06-03
As a good Kubuntu user, I usually run the updater whenever new updates are available.  "What could go wrong!  This stuff is perfect!"  And it usually is.  Except this time.

I'm now at Linux 2.6.20, and since the update, my Intel EtherPro ipw3945 connection is no longer working.  The eth1 device doesn't even exist.

This seems totally ridiculous.  If I can't fix this I will have to completely re-install the system and stay at an older version.  Is there some quick fix for this that anyone knows?

I'm not sure if it matters, but this is on a Sony Vaio.

Also during the upgrade, my NVidia driver broke, so I had to take it out of the xconfig.  I'm pretty sure I can just reinstall the NVidia driver and it will be fine, so that's a much less important issue than the wireless.

Any ideas would be much appreciated.

Thanks,

"Posting with help from an Ethernet cable"

---

### Post by rapolas on 2007-06-03
You should update kernel-restricted-modules as well. And do not upgrade your kernel if you don't see update for restricted modules, cause it gonna happen everytime.:)

---

### Post by needhelpplease on 2007-06-03
Ah, thank you.  That makes sense.  Please excuse the cluelessness of this question, but how do I do that?  I'm using Kubuntu, with the adept manager.  I'm also totally fine with command-line things.  Should I somehow uninstall this newer kernel?

In future I'm not going to do kernel updates unless I confirm all this.

---

### Post by rapolas on 2007-06-03
You can boot your old version of kernel by pressing esc button while you pc is starting to boot to enter the grub menu, it still should be there. Anyway, both kernel and restricted modules usually comes together, difference between these two updates might be hour or couple, not longer. And to install it you should do: ```
sudo apt-get install linux-restricted-modules-generic
```

---

### Post by needhelpplease on 2007-06-04
Cool, thank you!  That worked perfectly.  Note to Ubuntu developers, it would be cool if there were some notification or more information about this when kernel updates come out, because this thing is not at all obvious (to me at least).

All in all, my #1 reason for switching from Suse to Ubuntu was that Ubuntu's (Debian's) package management system is so good.  This little thing is the only time I have had  a difficulty.

---

### Post by IntuitiveNipple on 2007-06-04
From what I've been reading in the Launchpad bug listings, this new 2.6.20-16 kernel update has caused a whole host of major problems in unrelated but important areas which prevent Feisty even completing the boot process if the PC has an Intel ICH5/5 IDE controller.

If you're reading this, and haven't yet allowed the auto-update, then it might be wise to hold off unless you really need some of the functionality that the kernel update provides.

---

