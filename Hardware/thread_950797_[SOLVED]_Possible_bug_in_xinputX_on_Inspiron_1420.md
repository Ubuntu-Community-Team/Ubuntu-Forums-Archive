---
title: "[SOLVED] Possible bug in xinput/X on Inspiron 1420?"
date: 2008-10-17
forum: Hardware
---

### Post by derrick81787 on 2008-10-17
I'm running Intrepid, and I'm trying to disable tapping on my touchpad.  With the new Xorg, I've found that you're supposed to do this either through HAL, or by using xinput.  The HAL method doesn't seem to work (my thread about disabling tapping is [http://ubuntuforums.org/showthread.php?t=949976](http://ubuntuforums.org/showthread.php?t=949976)) so I thought I'd use xinput.

I've found, through some Googling around, that xinput lists my touchpad as "AlpsPS/2 ALPS GlidePoint".  However, when I run `xinput list-props "AlpsPS/2 ALPS GlidePoint"`, I get the following output:

```
derrick@hammer:~$ xinput list-props 4
Device 'AlpsPS/2 ALPS GlidePoint':
Segmentation fault

```

There's definitely something wrong here.  Is anyone else having problems like I am?

Thanks,
Derrick

***** Edit:**
There was an update released today that fixed this issue.

---

### Post by derrick81787 on 2008-10-19
Man, what's been up with the lack of responses lately?  I'm 0 for 2...

*****Edit:**
Actually, I guess this belongs in the Intrepid Ibex section of the forums, but I didn't see that section when I posted it.  It could still be relevant here, I guess, but mods can feel free to move this thread if they see fit.

---

