---
title: "Keyboard shortcut for TrendNet TK-207 KVM switch - SCROLL LOCK + NUMLOCK + NUMLOCK"
date: 2022-09-23
forum: Hardware
---

### Post by rayhebert on 2022-09-23
Just wanted to make others aware of the keyboard shortcut that I stumbled upon with an old TrendNet TK-207 2 port KVM switch.

Recently I found this KVM switch at a resale shop and have been using it with my Windows laptop and my Ubuntu laptop.  Works great with the buttons on top of the switch.  But I was wondering about the possibility of a keyboard shortcut.

After doing some investigative work, I found a keyboard shortcut that works for windows (Scroll Lock + Scroll Lock), but not on Linux.  I found where others were saying to do two 'Num Lock' keystrokes back to back for Linux.  For my laptops, that was not very consistent.  Sometimes it would switch.  But most times it would not.

After trying many keystroke combinations, I ran across a keyboard shortcut that works reliably every time.

The combination is as follows:
Press the 'Scroll Lock' button.  Then press the 'Num Lock'.  Then press the 'Num Lock' again.

'Scroll Lock' + 'Num Lock' + 'Num Lock'

I can perform this keystroke slow rate of speed and switch back and forth very reliably.

This 'three key stroke' combination consistently lets this TK-207 2 port KVM switch go between these two laptops, one Windows and one Ubuntu Linux, without any issues.

Not sure if this would work on a Mac as well.  Seems like it should.  I do not have a Mac.  Otherwise, I would try it out.

Hope this helps others searching for a solution.

---

### Post by mIk3_08 on 2022-09-24
> **rayhebert said:**
> 'Scroll Lock' + 'Num Lock' + 'Num Lock'
In my case, the scroll lock in my Ubuntu System is disabled by default.  Scroll lock won't automatically work every time I boot my Ubuntu System.  What I did is to enable it using the command below: If it does not work  I booted on Wayland then perform the command again. Then it works.  Regards and cheers. 
```
xmodmap -e 'add mod3 = Scroll_Lock'
```

---

