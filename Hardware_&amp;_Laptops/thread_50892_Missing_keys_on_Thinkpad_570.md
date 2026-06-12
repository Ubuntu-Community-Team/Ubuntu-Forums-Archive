---
title: "Missing keys on Thinkpad 570"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by Milambar on 2005-07-21
I love installing Linux on old laptops that people throw out as worthless, only to see them green with envy when they see it working better than their new WindowsXP loaded laptop, don't you? ;)

Anyway, I installed the latest version of Ubuntu on an old IBM Thinkpad 570. The keyboard is missing a couple of keys, but most problematic is the | and \ key. There is a blank key where that key should be, but its not mapped to anything.

Is there a way that I can use to map that key to get my | and \'s back?

Many thanks,

Milambar

---

### Post by Milambar on 2005-07-21
Ok, no matter, I've solved this myself.

First, I hate working in sudo, so I had to force myself a proper root prompt. I won't say how, but I did it. Then I ran xev to find the scancode of the key in question, the scancode turned out to be 131.

Then I made a custom keymap file. In it it says:

keycode 131 = backslash bar

Then I saved it as ~/.custom.map

Then I altered .bash_profile to run:

xmodmap ~/.custom.map

So every time I open a terminal, it alters the keymap to include that key.
Job done.

If it wasn't for my previous linux experience, mainly on debian and mandrivia, I would have never figured this out. There is that much either confusing information on the web, or none at all. So, maybe this posting will be of use to others.

I just need to find out how to modify the global keymap, so the change is permanent, and not just for X.

---

### Post by s_p_a_r_k_y on 2005-07-22
[QUOTE=Milambar]Ok, no matter, I've solved this myself.

First, I hate working in sudo, so I had to force myself a proper root prompt. I won't say how, but I did it. Then I ran xev to find the scancode of the key in question, the scancode turned out to be 131.

Then I made a custom keymap file. In it it says:

keycode 131 = backslash bar

Then I saved it as ~/.custom.map

Then I altered .bash_profile to run:

xmodmap ~/.custom.map

So every time I open a terminal, it alters the keymap to include that key.
Job done.

If it wasn't for my previous linux experience, mainly on debian and mandrivia, I would have never figured this out. There is that much either confusing information on the web, or none at all. So, maybe this posting will be of use to others.

I just need to find out how to modify the global keymap, so the change is permanent, and not just for X.[/QUOTE]

the easiest way to get root is
sudo passwd root
then just su  and enter the password...Just makes you think about giving friends and other people sudo access. I use sudo when I only thing I have a few commands, but if I am doing real system maintanance where ever command will need root I just su and become root, sudo wastes time then.

Don't give anyone sudo access if they dont need it. I would rather take 20 minutes and install something for them than let them play around with the system.

---

