---
title: "extra memory and kernel"
date: 2005-08-22
forum: Hardware &amp; Laptops
---

### Post by jeremytaylor on 2005-08-22
Hi there,
I've just ordered some new memory for my machine that will push it up to 2GB. I understand that the standard 386 kernel won't support this much memory and I will either need to move to the 686 kernel or compile my own with hi-mem support. 
If I switch kernel will I also have to start again with things like my fglrx kernel modules and alsa sound modules that I had to fiddle around with in the first place for get to work or is there an easier way?
thanks
Jeremy

---

### Post by skoal on 2005-08-22
The simple answer: no other intervention needed by you.  Sound & video should still work without re-configuring them again.

1. For the sound modules, no.  I don't know what you mean by "fiddle around" with, but your mixer settings (etc.) will still be preserved, since they're external driver settings anyways.

2. I cannot speak for the fglrx drivers (since I use Nvidia, and afterall, drivers can't really speak like humans anyway since they're just stored electrical signals).  I believe the kernel packages have a 'rules' (or similiar deb package script) which will just copy the binary video driver from the other kernel /lib/modules, _assuming_ it's just an update (or 386 -> 686 as in your case) but _within_ the same kernel revision.  So, you should not have to re-install anything there either.  At least I didn't while using the nvidia binary driver...

you can install the 686 kernel and see what happens.  Worst case, you'll always have the 386 kernel to boot back into from within the grub menu.

\\//_

---

### Post by jeremytaylor on 2005-08-22
thanks for that.
By fiddling around I meant that I have an intel hda sound thing and I had to build a new module thing for it including the appropriate drivers. But it sounds like it should be all okay from what you say.
thanks again
jeremy

---

