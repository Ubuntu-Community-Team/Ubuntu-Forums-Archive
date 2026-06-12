---
title: "Where's my GRUB?"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by wangsuda on 2009-11-03
Just did a clean install of Karmic 64 bit. Everything works great, except for the GRUB. I can't see it, or it doesn't appear. After the BIOS screed loads, I get one word - "GRUB" - and then a black screen and then the Ubuntu symbol. Is this normal? If it isn't how do I get the GRUB to show?

---

### Post by Revolutionary101 on 2009-11-03
You can view and edit your GRUB menu if you look in /boot/grub/menu.lst

---

### Post by Rhubarb on 2009-11-03
Don't worry this is normal.

Karmic is using Grub2 now which is a nice step-up from grub1.x

If you wish to see the grub menu, press and hold down **shift** while your computer boots up.

If you want to read a bit more on grub2, have a read here:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Essentially if your computer boots up into ubuntu fine, and you're not dual-booting, then by default you won't see grub unless you've got your finger on the shift button on your keyboard.

Grub2 takes a little to learn, but it's really quite a nice improvement from Grub1.x :)

Edit: Revolutionary101, you are referring to Grub 1.x which is vastly different to Grub2, the configuration file is actually in /etc/default/grub
Once you've made changes, you'll need to run **sudo update-grub** to make the changes apply

---

### Post by wangsuda on 2009-11-03
> **Rhubarb said:**
> Don't worry this is normal.

Karmic is using Grub2 now which is a nice step-up from grub1.x

If you wish to see the grub menu, press and hold down **shift** while your computer boots up.

If you want to read a bit more on grub2, have a read here:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Essentially if your computer boots up into ubuntu fine, and you're not dual-booting, then by default you won't see grub unless you've got your finger on the shift button on your keyboard.

Grub2 takes a little to learn, but it's really quite a nice improvement from Grub1.x :)

Edit: Revolutionary101, you are referring to Grub 1.x which is vastly different to Grub2, the configuration file is actually in /etc/default/grub
Once you've made changes, you'll need to run **sudo update-grub** to make the changes apply
I did the shift key trick and it worked. Thanks! I am using grub 1.x. How do I update to GRUB 2?

---

### Post by Rhubarb on 2009-11-04
> **wangsuda said:**
> I did the shift key trick and it worked. Thanks! I am using grub 1.x. How do I update to GRUB 2?

If the shift key trick worked, then you're using Grub2 now.
Please note that the version of Grub2 in Karmic is actually reported as being Grub version 1.97~beta4 (it could be slightly newer than that, as I can't be sure because I'm currently running upgrades from Karmic beta, which may possibly have an older version of grub2).

The version numbers are all a bit confusing, but you have to remember that grub2 has been in development for several years, and they want everything to be super-duper stable and ready before they release 2.0 - which is why it's currently 1.97

---

### Post by totfit on 2009-11-04
> **Revolutionary101 said:**
> You can view and edit your GRUB menu if you look in /boot/grub/menu.lst

Not any more. :)

---

### Post by wangsuda on 2009-11-04
Thanks for your help, Rhubarb. My mind is at ease, now!

---

