---
title: "Semi mechanical keyboard gaming failed to work on Ubuntu 13.10, 12.04"
date: 2013-12-11
forum: Hardware
---

### Post by xgenvn on 2013-12-11
Recently I have bought a new semi machanical keyboard to couple with Ubuntu and Windows 7 64bit (usb keyboard). The keyboard is currently working very well on Windows 7, but generally failed to work properly on Ubuntu 13.10 and 12.04, I have tested all recent versions of Ubuntu. Crunchbang 11 also failed to work too (and maybe I'll try to checkout Arch or Fedora later).
As I have checked carefully and in detail, when using **showkey** command to check which key invokes, the result is that **Ctrl/Alt/Win** keys** invoke Shift keycode**. And the backlight of capslock, numlock and scroll-lock didn't toggle on, but their functions are fine. The main problem is Ctrl/Alt/Win keys, I guess there're reason to this kind of matter, maybe the "rollover" or "ghost typing" feature in gaming keyboard confused the kernel/keyboard driver.
I don't know whether a way to fix this problem, by mapping to other keys or somehow, but I hope there will be a way to deal with keyboard driver.

Any suggestion would be appreciated!

Thanks.

---

### Post by xgenvn on 2013-12-12
Hi again,

I have tested with Fedora 19 but no luck, they're the same problem so I guess it would be something incompatible with latest kernel or keyboard driver.
When bootup to GRUB or command line, the keyboard just work fine, so the keyboard is regconized properly by BIOS. It's the kernel/keyboard driver matter.
I really hope that someday we can fix this, as I'm awared that many people with gaming keyboard is facing the same problem.
Well, I really want to stay in Ubuntu for most of the time, but switching over Windows is what I have to agree to deal with right now. :)

---

