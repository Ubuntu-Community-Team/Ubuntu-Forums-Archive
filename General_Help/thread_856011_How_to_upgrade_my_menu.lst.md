---
title: "How to upgrade my menu.lst"
date: 2008-07-11
forum: General Help
---

### Post by hahanv on 2008-07-11
I upgrade my ubuntu7.10 to 8.04 two weeks ago and I found my menu.lst is the verson of 7.10. Now I have a ubuntu8.04 with a menu.lst 7.10, what can I do?? Pleeeeeeeeeeeeeese help me!!!!:)

---

### Post by iaculallad on 2008-07-11
> **hahanv said:**
> I upgrade my ubuntu7.10 to 8.04 two weeks ago and I found my menu.lst is the verson of 7.10. Now I have a ubuntu8.04 with a menu.lst 7.10, what can I do?? Pleeeeeeeeeeeeeese help me!!!!:)

Had you tried to boot using 7.10 on your GRUB menu? Does it still load Gutsy? or When booting with 8.04, does it load Hardy?

Could you post your /boot/grub/menu.lst file.

---

### Post by Elfy on 2008-07-11
> Could you post your /boot/grub/menu.lst file.and if you don't know how run this from aterminal

```
cat /boot/grub/menu.lst
```

---

### Post by hahanv on 2008-07-11
my menu.lst can load ubuntu8.04, but it loads the old kernel

---

### Post by iaculallad on 2008-07-11
> **hahanv said:**
> my menu.lst can load ubuntu8.04, but it loads the old kernel

That's would be fine, you can try to upgrade you're kernel once booted on Hardy.

*Could you post your /boot/grub/menu.lst file:

```
cat /boot/grub/menu.lst
```

---

### Post by hahanv on 2008-07-11
> **hahanv said:**
> I upgrade my ubuntu7.10 to 8.04 two weeks ago and I found my menu.lst is the verson of 7.10. Now I have a ubuntu8.04 with a menu.lst 7.10, what can I do?? Pleeeeeeeeeeeeeese help me!!!!:)

aha!!!!!!!
I've got it.
I use "upgrade" to solve this problem.
many thanks for you.

---

