---
title: "Micro Innovations Wireless Keyboard KB985W"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by PradeepArya on 2007-09-14
I just picked this pack (Model KB985W) containing a wireless keyboard and mouse. It also has a small USB station with indicator lights (Num Lock, Caps Lock, Scroll Lock) to receive wireless signals.

It's got a mini-CD with drivers, but only for Windows.

On Ubuntu 7.04 (Feisty), I plugged it in and it seemed to be working great.

The mouse works great, it's a little over-accelerated for my taste, but it seems to work without a hitch, including all buttons and the scroll-wheel.

The keyboard however has a little bit of trouble. At first, the easy access keys weren't working, but this solved that problem:

sudo aptitude install lineakd

The other problem I can't resolve is that the keyboard doesn't function fully. If I hit the Left Shift button, it will also send a capital Y character. If I hit the Right Shift button, it will send a capital J character. And some characters it will suppress, such as trying to type a capital letter U; just won't work at all. It also capitalizes all Y characters.

Here's a sample from the keyboard:

YThe other p YI can't resolve is that the keYboard doesn't function fullY. YIf YI hit the YLeft YShift button, it will also send a captial Y character. YIf YI hit the YRight YShift button, it will send a capital J character. YAnd some characters it will suppress, such as trYing to tYPe a captial letter Y; Just won't work at all. YIt also capitalizes all Y characters.

Anybody have any ideas on how to make it work properly?

---

### Post by rlykens on 2007-12-27
having same problem on my a105-s2081.  Mouse works great w/ a little accel threshold tweaking, but the keyboard doesn't function properly.  I tried changing the keyboard layout, but couldn't find the correct one to work with xubuntu 7.10.  I'm still working on the prob.  I'll comment back when I find a solution.

---

### Post by Nesman on 2008-01-24
I know this post is fairly old, but since it's not going anywhere, I'll add my 2 cents for the next person that finds it.

I got the same wireless keyboard and mouse (Model KB985W) from a Windows user that declared it broken.

It would work fine if you plugged it in while Windows was running, but it would never work if you left it plugged in while the computer rebooted.  You'd always have to reseat the usb.  

I plugged it into Ubuntu 7.10 and it worked.  Rebooted, and it still worked.  It does seem to act a little bit oddly with a few key combos. Ctrl+tab and alt+f4 don't always work, but several of the "internet keys" do, such as the calculator and email icons.  The media keys work as well, except the one on the far right, which is supposed to launch the media player.

---

### Post by seandiggity on 2008-03-07
Just to add in my experience...

I bought the KB985W and hooked it up with Gutsy but had exactly the problems you described.  I still had the receipt for it, so I brought it back and bought model KB1045LSR instead, which is a "laser" keyboard and not "optical" (anyone know the difference?  I know so little about this stuff).  Anyway, that model works fine without any configuration and also worked for at least one other user: [http://ubuntuforums.org/showthread.php?t=665129]("http://ubuntuforums.org/showthread.php?t=665129")

---

