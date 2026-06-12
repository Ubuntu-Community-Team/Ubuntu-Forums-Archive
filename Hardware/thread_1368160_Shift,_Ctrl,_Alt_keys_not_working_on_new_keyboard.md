---
title: "Shift, Ctrl, Alt keys not working on new keyboard"
date: 2009-12-30
forum: Hardware
---

### Post by quip on 2009-12-30
I purchased a new wireless (via bluetooth) keyboard yesterday.  I have a laptop that I want it to work with.  I plugged in the bluetooth adapter that came with the keyboard/mouse combo, and it was recognized just fine.  I added the mouse and keyboard just fine, and they both work, with one caveat:  the Shift, Ctrl, Alt, and other "meta" keys (like the Windows key) do not work.  

If I run xev in a terminal, events occur and seem to be properly detected (i.e., if I press the left shift button, an event is written to screen that detects the keystroke as L_Shift), but I don't get any of the actual consequences I should get, like capitalization, or Ctrl-C copy, paste, etc.

I haven't messed with xorg.conf by hand in quite some time, although I am not sure if that will help.  The keyboard is a Rocketfish, model RF-BTCMBO2 from Best Buy.  I would appreciate any suggestions, or pointers to good walk-throughs/documentation on mapping keys to actions, although I am not sure that is the solution, since the keystrokes seem to be recognized, but are not being carried out.

---

### Post by quip on 2009-12-30
UPDATE:  While trying different things out and poking around, I found that the Shift and Ctrl (and therefore probably the others, too) actually _do_ work, but only _after_ I press the other key in the combination.

For instance, I have to press and hold "S", then press the Shift key to get a capital S; I also can press and hold A, then press Ctrl, and I can select all.

This is a bit illuminating, but obviously not acceptable.  Does anyone have any idea as to why this might be happening?

---

### Post by quip on 2009-12-30
Well, I think I might have solved it, but I'm not entirely sure, so I won't yet mark this as solved.

I started looking into the Accessibility Tab after my last post, and I am almost sure that it had "Simulate Simultaneous Keypresses" unchecked, and "Disable Sticky Keys if two keys are pressed together" checked.  I reversed that (checked the former, unchecked the latter), and things still seem to not be completely there, but for the most part seem to be working correctly (I cannot rule out some typing errors, since it is a new keyboard ;)  )

Anyway, if it is solved, I will come back and mark it as so.  Any comments are welcome, whether to say it makes sense or give a different thing to think about.

---

### Post by quip on 2009-12-30
I am marking this as solved, as things are working per my previous post.  The only thing I can tell that is not working as expected (and I still might be able to fix) is repeated strokes of the Shift, Ctrl, or Alt buttons.  For example, I can begin a word with a capital letter, and I can capitalize everything with Caps Lock, but if I hold down on the Shift key, I get one capital letter followed by all lowercase.  Once I release the key, I can then press down again to get another capital letter.  

Minor inconvenience, and I'm not getting any ideas, so I'm letting it go.  Thanks to all that viewed.

---

### Post by gwdragon on 2010-02-22
I wanted to let people know this is also a work around for another similar problem I had.  I am using krfb on gnome (2.6.31-19-generic kernel) and could not type caps with the shift key. I found the same was true as quip and holding down the key I wanted then pressing shift would capitalize it.  I went into the accessibility options and made the changes and it worked as a single use shift key.

The strange thing was this only happened in krfb.  I would sit at the console and have no problems what so ever.  I am still not sure what the problem is and would like it fixed, but at least now I can type in my password and work on utilities remotely.

---

### Post by markfaine on 2010-06-10
Were you able to get the lights for Caps Lock, Scroll Lock, Num Lock, etc working?

---

### Post by daniel.hartman on 2011-04-10
Thank you, quip, for your multiple follow-ups.

I am experiencing the same problem with a Lenovo A300 and Ubuntu 10.04 LTS. 

Currently, after making the adjustment in Keyboard Accessibility (System->Preferences->Assistive Technologies) the Ctrl, Alt, and Shift work for the first character, but as you correctly point out the system is still ignoring the additional characters.

---

### Post by ndstate on 2011-04-27
I filed a bug report for this: [https://bugs.launchpad.net/ubuntu/+bug/772116](https://bugs.launchpad.net/ubuntu/+bug/772116)

---

### Post by esanmartin on 2011-05-03
Can any one move this topic from solved to open? the bug is from 2007 and in the 2011 it's not fixed, any one now any solution for this?

Regards, and long live to Ubuntu.

---

### Post by daniel.hartman on 2011-06-06
This link seems to indicate that it has been fixed in a newer version of console-setup:

[http://lists.debian.org/debian-kernel/2011/02/msg00601.html]("http://lists.debian.org/debian-kernel/2011/02/msg00601.html")

I upgraded to version 1.73:

[http://packages.debian.org/sid/console-setup]("http://packages.debian.org/sid/console-setup")

and no luck.  Same problems as before.

---

### Post by sadokbjk on 2011-09-13
this problem still exists while using krfb. (2.6.32-33-generic kernel)

---

### Post by aleksandrrakov on 2012-08-23
Hello!
A have Lenovo Ideacentre A320 and same problems with keyboard.
 I wrote linux driver and it works good in ubuntu 12.04
Here is driver source code and install instructions
[https://github.com/aleksandr-rakov/hid-a320](https://github.com/aleksandr-rakov/hid-a320)
It may help you to solve problem

---

