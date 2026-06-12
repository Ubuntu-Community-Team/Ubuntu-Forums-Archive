---
title: "Upgrade to 9.10 has caused kernel panic"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by hard2explain on 2009-11-01
I've upgraded to Ubuntu 9.10, however, when I now start my laptop (an HP dv6000) I get the following message:

[       1.213750] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)

If I press 'Esc' after it says 'GRUB loading' I can choose the options, which lead to different results:

Ubuntu 9.10, kernel 2.6.31-14 generic : causes kernel panic
Ubuntu 9.10, kernel 2.6.31-14 generic (recovery mode) : causes kernel panic with a series of 'Call Trace' messages underneath.
Ubuntu 9.10, kernel 2.6.28-16 generic : white Ubuntu logo appears, boot seems to stop after it says it has finished 'Checking battery state...'
Ubuntu 9.10, kernel 2.6.28-16 generic (recovery mode) : Loads up to the 'Recovery Menu', when I select 'Resume normal boot' I can get to a prompt which asks me for my username and password (labelled tty1)

This makes me think that perhaps I haven't lost all my files.  

Any help on this would be much appreciated!

---

### Post by hard2explain on 2009-11-03
Anyone got any ideas on what the best way of going about this is?  I'm unsure about where the best place is to start!

---

### Post by v1nsai on 2009-12-09
I solved this problem by selecting my boot option in GRUB manually.  It was automatically booting from my old menu.lst, and it was trying to boot a 9.04 kernel. Just make sure your selecting the right option in GRUB, that solved it for me.

---

