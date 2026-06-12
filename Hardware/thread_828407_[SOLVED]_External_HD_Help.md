---
title: "[SOLVED] External HD Help"
date: 2008-06-13
forum: Hardware
---

### Post by daisyfoofpoof on 2008-06-13
Looking for a good External HD to install ubuntu on, i don't need a huge 500 gb one, so i looked around and found this:


[http://www.amazon.com/Western-Digital-Passport-External-WDXMS600TN/dp/B000HZD2XK/ref=sr_1_1?ie=UTF8&s=electronics&qid=1213395554&sr=1-1]("http://www.amazon.com/Western-Digital-Passport-External-WDXMS600TN/dp/B000HZD2XK/ref=sr_1_1?ie=UTF8&s=electronics&qid=1213395554&sr=1-1")

would you say that would be a good one?
thanks for the help everyone

BTW i already know how to install it on the ext. HD, you know, installing GRUB in the right place and stuff

---

### Post by The Cosmic Hobo on 2008-06-13
I'd be wary of that. I don't see a power cord in there, and if you're using a laptop that would add to power drain.
I'm not sure what your MBR (or Grub) would do about booting from a removable drive. You would need a BIOS that supports boot-from-USB, though.

---

### Post by daisyfoofpoof on 2008-06-13
well, in the description it doesn't need a power cable, just a usb cable, and i'll be using a desktop, not a laptop, so i should be fine on power...as for the bios, i'll check weather mine supports usb, and if it does, i've looked at forums galore, and they all say the same thing:at the last step in the installation go to advanced and say where to install GRUB, so I think i'll be good, but do you think this is a good one?

---

### Post by The Cosmic Hobo on 2008-06-13
> **daisyfoofpoof said:**
> well, in the description it doesn't need a power cable, just a usb cable, and i'll be using a desktop, not a laptop, so i should be fine on power...as for the bios, i'll check weather mine supports usb
Well you'll be fine with a desktop, then, and if it's fairly modern, it should boot OK. I have a laptop that's about two years old that, if you interrupt the startup, can be told to boot from USB.

As for the rest - I'm afraid that's outside my experience. I'm not even sure if Grub supports booting from removeable media. Hopefully someone else who does know will come along in a moment :)

---

### Post by daisyfoofpoof on 2008-06-13
I found an excellent guide, [Installing Ubuntu on an External Hard Drive]("http://ubuntukids.org/blog/?p=69"), and grub does support removable drive booting, i have a very modern computer, so i think the bios should be fine, but i will check later, before i buy.  thanks for all the help then.:)

---

