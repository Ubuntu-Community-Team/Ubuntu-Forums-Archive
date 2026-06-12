---
title: "Abrupt loss of keyboard function"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by torquill on 2007-04-16
I've seen any number of posts about loss of keyboard functionality, but none where it happens in the middle of a session, for no apparent reason.  I'm on a laptop running Edgy/Gnome.

I'll be doing something -- browsing, listening to music, typing on IM -- and suddenly the keyboard goes dead.  I can use the special-function keys, like power, sound, etc., but none of the main keys work.  The touchpad is fine, and the system responds properly to clicks and mouseovers.

I can ssh into the machine, but anything which requires sudo just wedges.  su gets me into the root account, and I can run some commands that way, but others wedge as well (the last time I tried was weeks ago, so I can't bring specific commands to mind).  If I try to exit X or reboot in a controlled fashion, it gets halfway through and stalls (with a black screen, so I can't even tell what it's stopping on).  CPU and memory usage show normal.

I just tried to do an incremental upgrade to version 12.2 of xserver-xorg-core, and after a restart the machine started losing the keyboard every ten to fifteen minutes.  I downgraded it to 12.0 again and it seems to be back to the way it was, which is that it would do it once every couple of weeks.  That suggests, as I've started to suspect, that it's an X problem, but my ability to diagnose it is limited when some of the diagnostic commands don't work.

Suggestions for what to try, and analysis of the results, are welcome.  I'm of moderate skill, so I understand a lot of concepts but I lack specific commands and much ability to interpret their output.

Thanks!

---

### Post by ixela on 2007-04-17
I am having similar issues as well. This is on a Dell Latitude D505. Keyboard loss occurs randomly, sometimes while typing. There is no rhyme or reason to the keyboard loss, with all symptoms described by you occurring here too.

---

### Post by ixela on 2007-04-19
I have been able to narrow down the problem to using network-manager. Immediatly upon disabling my wireless through it, I lose all use of my keyboard. I ran dmesg and there is nothing special going on when it happens. My wireless card is a broadcom 94306 card in a dell latitude d505. This problem had not occured until the last kernel change to 2.6.20-15-generic on feisty fawn. I can reproduce this error many times. Once I lose keyboard, I cannot open anymore programs nor remote into the box. The mouse is still usable, however even issuing a halt as root does not allow it to shut off. If I can provide any more info let me know,as this is a most limiting problem for me.

---

### Post by torquill on 2007-04-20
Sounds like your problems are somewhat different than mine, as I can still remote into the box with SSH, and it doesn't seem to matter what state the network manager is in.  dmesg doesn't show anything for me, either.  The fact that it won't shut down for me seems to be due to something wedging, waiting for I/O that just isn't coming, but I don't know what process it is.

Good luck.

---

### Post by ixela on 2007-04-21
Thanks. Your post is the closest thing I've seen to my problem so far. I atleast have it narrowed down to my wireless networking card/network manager. Ive had the laptop up and usable for 3 days as long as I dont touch wireless. If I do the entire machine grinds to a halt.

---

### Post by Bero on 2007-04-21
network-manager on 7.04 is buggy, when I start to configure manual config in network-manager the keyboard stop working!

What about this: [http://librarian.launchpad.net/7391175/GDM-RESTART-WHEN-KEY-PRESS.3GP]("http://librarian.launchpad.net/7391175/GDM-RESTART-WHEN-KEY-PRESS.3GP")

---

### Post by salih on 2007-06-11
I have very similar problem. All of a sudden my USB keyboard stop functioning. Mouse is working properly but not even caps lock / Num Lock keys are turning on.  When I log in as a different user (non-root), keyboard works fine, when I switch to the root user (not root, but the user who has admin rights, ie. the one installed Ubuntu) keyboard does not work again.

I can ssh to it, everything else seems to work fine and I don't see any error in the "/var/log/messages".  Anybody has any clue?

These are some information about my system:

2.6.20-16-generic #2 SMP 
i686 GNU/Linux

There are 2 Intel(R) Pentium(R) 4 CPU 3.80GHz processors.

This is a desktop. No wireless, no bluetooth etc.

---

