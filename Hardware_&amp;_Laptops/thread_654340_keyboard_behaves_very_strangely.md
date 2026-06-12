---
title: "keyboard behaves very strangely"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by cnbiz850 on 2007-12-31
I have a HP Pavilion ze5155 and just installed Ubuntu 7.10 on it.

When I type, the keyboard randomly adds extras keys (mostly ~).  For instance, in xterm when I type "top", I could get "t~op", or "to~p", or "t~op~", etc.  In Firefox, I can't even finish typing this post.  The page keeps refreshing itself while I was typing.  I had to change to another machine to do this.  It's basically unusable.

I searched on this forum, but didn't seem to find any similar reports.  I also tried to change keyboard layout, but it didn't help.  I don't think the HW has problems, as it just worked OK under Edgy.

Anyone please help.

---

### Post by Sef on 2007-12-31
> I searched on this forum, but didn't seem to find any similar reports. I also tried to change keyboard layout, but it didn't help. I don't think the HW has problems, as it just worked OK under Edgy.

Have you tried the keyboard in another computer or another keyboard in your computer?  That way you could eliminate any doubt as to hardware or software.  (Most likely software, but never hurts to make sure 100%.)

---

### Post by cnbiz850 on 2007-12-31
> **Sef said:**
> Have you tried the keyboard in another computer or another keyboard in your computer?  That way you could eliminate any doubt as to hardware or software.  (Most likely software, but never hurts to make sure 100%.)

No, I haven't,as 1) the suspect to me is still the SW, and 2) an extra keyboard is not handy for a laptop.

---

### Post by cnbiz850 on 2007-12-31
OK guys, I did some further tests.

It seems the extra ~'s only randomly appear in terminal windows.  If I type in gedit, no problem.  If I type in firefox (as in posting), the texts are correct as I typed, but for some reason firefox keeps reloading the page after a few letters are typed.

Then I tested it with xev, it seems OK when I type normally -- I seem a press event and a release event on the key I typed, nothing wrong.  BUT, if I type in a key and hold it a little longer like a second or two (I had key-repeat turned off), I get extra press/release events on F5 key for some reason.  Does that indicate something?  Could anyone please enlighten me?  xev results for press-hold-release single letter g are quoted below.

> KeyPress event, serial 30, synthetic NO, window 0x2a00001,
    root 0x56, subw 0x0, time 829831839, (164,164), root:(169,212),
    state 0x0, keycode 42 (keysym 0x67, g), same_screen YES,
    XLookupString gives 1 bytes: (67) "g"
    XmbLookupString gives 1 bytes: (67) "g"
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x2a00001,
    root 0x56, subw 0x0, time 829831927, (164,164), root:(169,212),
    state 0x0, keycode 71 (keysym 0xffc2, F5), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x2a00001,
    root 0x56, subw 0x0, time 829831961, (164,164), root:(169,212),
    state 0x0, keycode 71 (keysym 0xffc2, F5), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x2a00001,
    root 0x56, subw 0x0, time 829832347, (164,164), root:(169,212),
    state 0x0, keycode 42 (keysym 0x67, g), same_screen YES,
    XLookupString gives 1 bytes: (67) "g"
    XFilterEvent returns: False



---

### Post by cnbiz850 on 2008-01-01
Anyone can help please?

---

### Post by cnbiz850 on 2008-01-02
Could anyone help please?

---

### Post by cnbiz850 on 2008-01-04
Hey, come on!

---

### Post by cnbiz850 on 2008-01-05
OK, guys, worked around it.
I don't know why the keyboard randomly generates F5 event while I am typing, but I did the following to totally ignore F5 key.  This worked around the problem.

put
> xmodmap -e "keycode 71 = NoSymbol"
in session preferences.

---

