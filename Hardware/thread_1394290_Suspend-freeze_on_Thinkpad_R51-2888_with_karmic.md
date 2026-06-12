---
title: "Suspend-freeze on Thinkpad R51-2888 with karmic"
date: 2010-01-30
forum: Hardware
---

### Post by BurgerKing on 2010-01-30
Well, in the german Ubuntuforums I didn't find an answer like I didn't in the web, so the forum here is my last chance:

On my Thinkpad R51 with 9.10 karmic the suspend-function doesn't work.
This means both, suspend-to-ram and suspend-to-disk.
What happens, hm, hard to explain. I start suspending with closing the laptop-lid or with the keycombo Fn+F4 the moon-LED begins to blink and nothing happens the screen is frozen, I can't do anything, mouse doesn't move, ctrl+alt+F1 or anything else doesn't work, just a hard-reboot helps (shutting down the laptop with holding the power-button 4 secs).
One thing that may help finding the error's source, with an old Hardy-Live-CD both suspend-types work perfectly like they should.
Please, if anybody knows how to fix this let me know :/
If you need any log or similar let me know what and where to find..

Thank you in advance

p.s. sorry for may bad language I'm from Germany :D

*edit* Hm, just installed from the kernel.ubuntu.com-PPA the old 2.6.29 kernel and suspend and hibernate work again (but a lot of other things not so it isn't a possibility to continue using the old kernel)
*edit 2* okay, 2.6.30 and suspend keeps on working but a lot of things not, so I'm quite sure it's a kernel-bug/problem.

---

### Post by paulib on 2010-02-02
I have exactly the same problem on my Thinkpad r51 with karmic. With Ubuntu 9.04 suspend and hibernate worked fine. I have no idea how to fix it.

---

### Post by BurgerKing on 2010-02-04
Well, for a temporary solution because I need my Notebook working (and the suspend-mode) I installed Jaunty again in which suspend and hibernate works flawlessly, but e.g. the Intel GPU's performance isn't even close that the performance on Karmic so it's just a temporary solution.
What I'm frightened from, I installed for test-proposes Lucid on a seperate partition but even there the suspend-bug still remains and the development is, for what I know, already in the state that there won't be any big changes in the kernel until Lucid's release...I fear with the final Lucid it won't work either :x
Like I read on launchpad and in forums there's quite a lot of people who are affected by this bug for a long time and there's still no solution, so what's going on? :/

---

### Post by timosha on 2010-02-04
This works for my Thinkpad R51 - 2887 in Karmic.

Put this line in /etc/default/grub (or replace the existing line):
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0 nomodeset"

Then run in a terminal sudo update-grub.

It does not work in Lucid (10.04). If you try it you will not be able to boot anymore.

---

