---
title: "Can't start X after installing XFree86"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by np_ on 2005-09-08
So I was trying to update my ATI Radeon 9600 drivers and I was going through [the release notes for the driver](http://www2.ati.com/drivers/linux/linux_8.16.20.html). Like a good boy, I was installing the requirements, which included "XFree86 version 4.1, 4.2, or 4.3". Went into the update manager, found it, installed it. Rebooted, and now X won't start. It complains that XF86Config-4 has to contain at least one screen. Checking that file, it's empty. With some hope, I tried to restore my backed up xorg.conf file, no effect. I tried to run dpkg-reconfigure xserver-xfree86 and got through all the steps, but X still won't start and XF86Config-4 is still empty. I read somewhere that I have to update the /var/lib/xfree86/XF86Config-4.md5sum and did so, still nothing. At this point, I'd be happy just to get everything back working the way it did before. Any ideas?

---

### Post by np_ on 2005-09-10
No one knows? Not even how just to switch back to x.org?

---

### Post by krusbjorn on 2005-09-10
Tried to just "sudo apt-get install xorg-xserver" (or is it xserver-xorg"? i never seem to remember that!)? Now, that should remove xfree86 and install the packages needed for xorg, right?

I dont know. Thats what i would have done, hoping for the best ;)

---

### Post by np_ on 2005-09-11
Yes! It worked! Thanks a bunch.

---

