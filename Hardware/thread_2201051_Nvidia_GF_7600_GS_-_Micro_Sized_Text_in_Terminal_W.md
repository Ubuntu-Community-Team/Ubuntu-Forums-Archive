---
title: "Nvidia GF 7600 GS - Micro Sized Text in Terminal Window"
date: 2014-01-22
forum: Hardware
---

### Post by kj6eo2 on 2014-01-22
Thanks for reading my post.  I'm running 12.04 LTS on a 3.8.0-29 Generic Kernel.  I recently installed an Nvidia GF 7600 GS and now when I open up a terminal window (CTRL-ALT-F1), the text size is "super small" (micro sized).  I'm running Nvidia Driver Version 304.88.  Another thing that could be conributing to the problem is that X doesn't know what kind of monitor I have.  This is because the system can't probe it because it's going through a KVM and a KVM extender.  If I had to, guess I could take the monitor out to the garage and hook it up directly to the server long enough
for it to sense it.

Any suggestions you might have would be appreciated!

Regards,

Bill - KJ6EO

---

### Post by kj6eo2 on 2014-01-23
Ok, I figured this problem out on my own by searching around on the web.  Here is the solution:

Open /etc/default/grub with your favorite editor as root.

Locate the line that says "GRUB_GFXMODE=" and change it to whatever resolution you want.

EXAMPLE:

GRUB_GFXMODE=1024x768x32

Save and exit.

Still as root, refresh grub with

update-grub2

REBOOT

Regards,

Bill - KJ6EO

---

