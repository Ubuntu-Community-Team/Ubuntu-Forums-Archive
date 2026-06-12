---
title: "Left shift key stops working in Gutsy"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by eksatx on 2007-12-12
I am using a Thinkpad X20 -- the same machine I have used for testing Ubuntu since its first release.

I recently started using Gutsy and I am experiencing a problem I have not seen before.

When I first start the machine everything works fine, but after a while the left shift key stops working.

When I run xev it does not register a KeyPress event when I press the left shift key.

If I restart the machine it goes back to working for a little while.

Any ideas?

---

### Post by UnsafeData on 2008-01-21
I'm having the same problem. My left shift key doesn't work.

(In addition, my up and down arrow keys don't work either.)

(I know this is a month old. This just saved time creating a thread ;))

---

### Post by GrumpyBob on 2008-01-26
interesting.  neither of my shift keys work under gnome, but do under kde and failsafe terminal.  this persists after reboot, and after selecting a different keyboard layout.  it's a bit annoying as i have to use caps lock, and cannot get to the symbols above the numeric key...my laptop is unusable with gnome.  only tweaks i've done today have been with xrandr.

robert

it reminds me of don marquis' archy and mehitabel.

---

### Post by GrumpyBob on 2008-01-26
OK, narrowed it down to Compiz - as soon as I enable Desktop effects, the Shift key stops working (actually, Shift-letter gives nothing).

Robert

Edit - turned out to be SCIM - now sorted - does this help fix the OP's problem as well?

---

### Post by BassKozz on 2008-03-19
> **GrumpyBob said:**
> Edit - turned out to be SCIM - now sorted - does this help fix the OP's problem as well?
I am having similar issues, how did you fix SCIM?

---

### Post by BassKozz on 2008-03-24
> **B/-\ssKozz said:**
> I am having similar issues, how did you fix SCIM?

Solved: [http://ubuntuforums.org/showthread.php?t=729510](http://ubuntuforums.org/showthread.php?t=729510)

---

