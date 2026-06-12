---
title: "&quot;Enable mouse clicks with touchpad&quot; does nothing"
date: 2010-05-10
forum: Hardware
---

### Post by tstack77 on 2010-05-10
I have an "AlpsPS/2 ALPS GlidePoint" touchpad on an HP Mini 311 netbook. I noticed that unchecking mouse clicks with the touchpad did nothing, tapping on the touchpad still emulated a left-click.

Is there a way to fully disable this feature from the terminal?

---

### Post by JustBeforeSleep on 2010-05-11
I am having this problem as well.  I am using an Acer Aspire One netbook model 532h-2326 and I can not disable touchpad clicks, even on my administrative account.  Any help would be appreciated!  :)

---

### Post by FireNoodle on 2010-05-15
This is a known problem:
[http://ubuntuforums.org/showthread.php?t=1316361&highlight=hp+mini+311](http://ubuntuforums.org/showthread.php?t=1316361&highlight=hp+mini+311)

No solution so far as I've found. Problem seems to be that this touchpad is a new model that isn't supported yet... in 9.10 the touchpad tab didn't show up at all, now it shows up but doesn't function.

Out of curiousity, does vertical scrolling on the touchpad work?

---

### Post by MarjaE on 2011-05-28
Not an expert, but I read that the drivers treat the ALPS touchpad as a PS/2 mouse, which is why none of the touchpad-specific options work. Supposedly, in some versions, the drivers register taps as button4 clicks, but on my machine they registered taps as button1 clicks.

If the drivers merge the signals from the tap and from the left button, it's going to be very hard for proposed fixes like the grub (i8042) suggestion or the xorg.conf.d (maximum tap time "0") suggestion to do anything. And neither did anything for me.

I don't know who ever thought tap-to-click was a good idea, but there ought to be some way to disable it to enable normal typing and cursor movement w/o the interference.

If there was an option to disable the mouse while typing - without needing every user to program their own version, mess about with keyboard settings, etc. - it would add least minimize the hassle of tap-to-click.

---

