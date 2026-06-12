---
title: "Upgrade to 9.10 problems"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by cambunctious on 2009-11-09
PLEASE HELP!

I upgraded to Ubuntu 9.10 and it seemed to work fine but when I restarted, GRUB did not show the new version.  I choose "keep current version installed" when it asked what to do with menu.lst (I did not know what I was doing and couldn't find any explanation).  When I run 9.04, the boot screen seems to switch from the old to new.  Then after it is done loading the screen turns black except for the top bar and the touch pad does not work.  Luckily, I can still boot to XP.

Do I need to edit menu.lst in recovery mode?  I am really bummed.  :???:

---

### Post by Bunnybugs on 2009-11-09
Well, if you upgrade, the grub 1.5 should still see your linux-kernels, and boot up your PC...

Grub 2 is just a renewed way of booting up, not specially a must have:s

I've booted a Jaunty PC to Karmic, and it worked fine with grub 1.5

---

### Post by cambunctious on 2009-11-09
Is this supposed to be a solution to my problem?

Perhaps it would help if I knew how to boot to the new kernel from recovery mode once.  Then I might be able to fix the problem with the Startup Manager program.

---

### Post by rygar on 2009-11-09
if you can boot to recovery mode (or a live cd), i think re-installing grub should work.  when you re-install, choose to replace your current menu.lst with the package maintainer's version.

maybe someone else has a better solution?

---

### Post by SteveHillier on 2009-11-09
> **cambunctious said:**
> Is this supposed to be a solution to my problem?

No it may not be a solution but someone had taken the time and trouble to read about your problem and make a response so don't get sarky with them.

---

### Post by cambunctious on 2009-11-09
> **SteveHillier said:**
> No it may not be a solution but someone had taken the time and trouble to read about your problem and make a response so don't get sarky with them.

;) Sorry

By reinstalling GRUB do you mean all of Ubuntu or is there away to reinstall just GRUB?

---

### Post by cambunctious on 2009-11-09
P.S.  What are beans and why doesn't my profile say "Gee! These Aren't Roasted!"?!!

---

### Post by rygar on 2009-11-09
just grub.  there is a way, although most tutorials out there are for grub, not grub2 (which i assume you have with 9.10), and i don't want to steer you wrong...

beans are the number of posts you have made.

---

### Post by cambunctious on 2009-11-09
Well somehow Ubuntu is working again with a wireless mouse.  GRUB is still messed up though.  I still don't know how to reinstall it.  Can I go back to 9.04?

---

### Post by rygar on 2009-11-09
if you do have grub2 (and not grub), try this:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

and no, sorry, there is no way to downgrade to 9.04.  if you want 9.04 back, you'll have to do a clean install.

---

### Post by cambunctious on 2009-11-09
Yippee!  I did not have GRUB 2 and I figured out how to install it.  Everything works fine now.  I like this new version of Ubuntu.  Thank you everyone for their efforts.

---

