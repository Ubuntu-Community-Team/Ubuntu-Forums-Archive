---
title: "Disabling framebuffer console in Lucid (10.04) Server"
date: 2010-10-10
forum: Hardware
---

### Post by ayqazi on 2010-10-10
Hi,

I'm running Ubuntu Lucid Server on a PC.

How do I disable the framebuffer console?  I want to use a non-fb console because it scrolls a heck of a lot faster.

I've disabled the framebuffer console for GRUB, and then tried adding the following to the kernel boot options: nofb, fb=0, vga=1.....

Unfortunately (for me anyway), during initialization, the framebuffer console gets activated anyway.

Then I tried messing with /etc/default/console-setup.... again, no go.

I looked in /lib/udev/console-setup-tty, still can't find anything that would do what I want.

Is there an easy way to do this?  I was about to blacklist the fbcon kernel module in desperation, hope there is an easy way to fix this :)  (Update: blacklisting fbcon didn't work, it gets loaded anyway..... OMGZORS, it's a stubborn one)

Thanks

---

### Post by gcbzzzz on 2012-02-13
bump.

I do know that udev is the culprit, but don't have more clues than that.

---

