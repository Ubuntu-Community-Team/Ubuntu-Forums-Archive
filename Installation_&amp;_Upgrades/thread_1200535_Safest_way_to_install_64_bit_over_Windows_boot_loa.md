---
title: "Safest way to install 64 bit over Windows boot loader?"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by starbase1 on 2009-06-30
I'm looking to install 64 bit Ubuntu as another boot option on my big PC, but I am very nervous about possibly losing the boot options that are currently on it.

From what I can see it is using 'Windows Boot Loader' to choose between XP64, and Vista.

What are the options for this? I like the idea of Wubi etc, but my most important requirement is that I want to be 100% sure of a painless way to get back to what I have now.

So how do I tell what install methods are compatible with what I have now?

All clues very gratefully received!

Thanks,
Nick

---

### Post by Sef on 2009-06-30
> From what I can see it is using 'Windows Boot Loader' to choose between XP64, and Vista.

That is correct.  MIcrosoft's boot loaders only see Windows products.

> What are the options for this? I like the idea of Wubi etc, but my most important requirement is that I want to be 100% sure of a painless way to get back to what I have now.

Ubuntu will install GRUB.  All of your oses should be read, and the option to choose the others that are not the default.

> So how do I tell what install methods are compatible with what I have now?


Ubuntu should install just fine, and you should be able to boot into the nondefault os of your choice.

Best thing to do is run the Live CD to make sure that your hardware is compatible with Ubuntu.

---

### Post by starbase1 on 2009-06-30
Thanks, that sounds reassuring.

Do I have the option of that 'install as a windows application' for the 64 bit version?

(Wubi?)
Nick

---

### Post by starbase1 on 2009-07-01
For anyone else who is wondering...

I tried the Wubi route, and it worked, adding extra options to the existing boot menu.

The only slightly confusing thing is that it added Ubuntu as a choice on the first menu, but also after I pick 'older version of windows' when it comes up as an alternative to XP64.

But U64 is running, and feels like I have had a hardware upgrade when compared to the other options!

Thanks, Nick

---

### Post by presence1960 on 2009-07-01
Ubuntu will utilize your hardware way better than windows could ever dream to do. Your machine should be snappier and more responsive.

---

