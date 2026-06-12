---
title: "USB KVM switch and keyboard layouts..."
date: 2008-12-31
forum: Hardware
---

### Post by vejiita on 2008-12-31
Hi everyone, here's my problem.

I have 2 PCs, 1 running Ubuntu 8.10 and the other Windows XP. I interact with them with a USB KVM switch for the keyboard and the mouse (2 LCD so I always see what happens on both OS).

Now, I have 2 keyboard setup on Ubuntu; US and French (Canada). If I use the KVM to switch to WinXP, then I go back to Linux, I can see that it lost the French layout and defaulted to the US one.

What I think happens is that when I use the KVM, Linux detects that I "disconnected" the keyboard and then "re-connected" it so it need to re-detect or to start from the beginning or something like that.

Would there be a way to "force" Ubuntu to *not* loose the layouts and to keep them whatever is the case (kb or no kb connected say ?).

Thanks in advance :)

BTW: I have no InputDevice in my xorg.conf, most likly because X auto-detect it ?

---

### Post by pjstadig on 2009-01-02
I have the same problem.  My particular situation is when using the Dvorak layout.  I have even gone into the Keyboard preference panel, added the Dvorak layout, *removed* the US layout, and when I switch away and back with the KVM my keyboard layout has changed to the US layout.

I have a Belkin Flip USB KVM.

Sorry to say that I don't have a solution for you.  I don't know exactly what is going on.

---

