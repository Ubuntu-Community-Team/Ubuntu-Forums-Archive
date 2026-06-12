---
title: "ubuntu installed 2 times?"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by bravemenrun333 on 2007-08-19
After having installed ubuntu 7.04 on my Lenovo Thinkpad R60, when I start the notebook in the boot options dialog there is two times the ubuntu options. How can I edit this and correct it?

---

### Post by merlinus on 2007-08-19
There are probably entries for two different kernels.  You can comment out the lines for the old one:

```

gksudo gedit /boot/grub/menu.lst

```

if it bothers you.

I would keep the old one on hand, however, just in case something goes wrong and you need to revert.

-merlin

---

### Post by bravemenrun333 on 2007-08-19
Thanks, but how do I do that? Sorry, I'm a real newbie... can you please give me the exact steps?

---

### Post by merlinus on 2007-08-19
Use the terminal command in my last post, and place a # in front of the lines referring to the -15 kernel in that file.

-merlin

---

### Post by bravemenrun333 on 2007-08-19
Thanks alot, it worked!

---

