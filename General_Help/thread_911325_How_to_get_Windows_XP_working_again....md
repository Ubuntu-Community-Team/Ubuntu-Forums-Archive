---
title: "How to get Windows XP working again..."
date: 2008-09-05
forum: General Help
---

### Post by shgadwa on 2008-09-05
I installed Xubuntu on my Dell Laptop, here...

I then installed Windows XP Professional. I found that it did not load linux, but it automatically loads XP....

So, I installed the GRUB bootloader which made Xubuntu Linux work, but now Windows XP does not work.... 

Any help would be appreciated.

---

### Post by Bruce M. on 2008-09-06
> **shgadwa said:**
> I installed Xubuntu on my Dell Laptop, here...

I then installed Windows XP Professional. I found that it did not load linux, but it automatically loads XP....

So, I installed the GRUB bootloader which made Xubuntu Linux work, but now Windows XP does not work.... 

Any help would be appreciated.

There may be an easier way but you can try this, in this order:

[LIST=1]
[*]Backup everything you want to keep.
[*]Re-install XP and in the process create a partition for Ubuntu.
[*]Now re-install Ubuntu on that partition.
[/LIST]

Ubuntu will see XP and set grub up to use it, whereas Windows doesn't see other OS's.

Why GRUB didn't see XP I can't say, it should have.

---

### Post by Sycron on 2008-09-06
Bill Gates, Microsoft love's alot open-source. That's why Fred's life goes hard when installs first (x)Ubuntu and then XP ...

---

