---
title: "Installing Dapper on Fujitsu Lifebook N5010"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by verix on 2006-07-11
'lo everyone.

I'll start out by saying I'm pretty much a Linux newbie. I'm decent in the sense that I've got an understanding about how *some* of it works, and when I need to (or know where to look), I do read the documentation. However, one of my places in lack of knowledge is knowing exactly what configurations pull which strings when it comes to booting, so that's where I probably need help here.

Recently I downloaded an ISO of Dapper Drake and tried to install, and the first thing I did was test the disc for any errors. I noticed that when I did this, the monitor just... stayed blank, and the CD seemed to run the test, and once it finished, proceeded to reboot my laptop.

So, in an ongoing attempt to see what exactly we can do or how far I can go in installing this (since there seems to be no mention of this make-and-model on the Ubuntu website!), I'd like to ask what kind of work-around I can do to force the Ubuntu install to show up properly on my laptop's monitor. I think I read somewhere that at boot I can set something like "mode=1400x1050," but I'm not exactly sure what that was.

Anyway, thanks in advance to any and all help I get. :)

---

### Post by tturrisi on 2006-07-11
boot the cd & press F2

---

### Post by verix on 2006-07-11
I think you meant F4. F2 just changes the language. F4 changes the VGA settings, which did work, and I thank you. :)

Anyway, I got it to boot into Ubuntu without the monitor going all wacky, and it seems a lot of the laptop's features work! Haven't tested things like the Fn key or anything, but the buttons, trackpad, and scroll-buttons seem to work fine! I'll partition my drive and attempt a dual-boot install and report back.

---

### Post by verix on 2006-07-12
Well so far so good! GRUB installed just fine, and after adding XP to the list, both OSes boot fine! I don't seem to have any hardware problems, as it detects my Fn keys and such things. A small thing I noticed earlier, though, was after I tried to "Hibernate," I couldn't come back! I think it may have been a fluke on my part, though, so I'll have to test it more thoroughly when I come back tomorrow.

---

### Post by tturrisi on 2006-07-12
Try suspend instead of hibernate.  Hibernate has been full of bugs in linux & windows and has yet to be perfected.  There is always risk of data loss & hardware failures to restart when using hibernate.  I've never used it on any operating system.  Suspend has issues with some hardware w/ linux too.  Ubuntu boots so fast that I don't ever use suspend either.  If I'm use ac power the laptop is on, if use battery then I shutdown & reboot when desired.

---

### Post by verix on 2006-07-12
Yeah, suspend doesn't reactivate my monitor after coming back. Seems to be the only problem so far. Oh well, guess i just can't suspend, then.

---

