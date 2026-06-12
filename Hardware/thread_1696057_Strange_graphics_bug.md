---
title: "Strange graphics bug"
date: 2011-02-26
forum: Hardware
---

### Post by aristotle2600 on 2011-02-26
I'm trying to install  Ubuntu 10.04 on a laptop for a friend, but when I booted up the install  CD and tried the standard install procedure, something bizarre was going  on with the graphics that made it unusable.  I thought if I went ahead  and just installed it in text mode I could see what was wrong, or maybe  it would fix itself after being actually installed.
  

No such luck.  The effect is still there after the initial boot up,  and it's also present on all virtual consoles (!).  The effect is hard  to describe, so I have attached two [pictures]("http://imgur.com/a/DP9Mp")  of the GUI login screen and the virtual console after logging in.  It  sorta looks like there are "multiple copies" of what should be on the  screen, but they are overlapping; but, there is only one cursor.  Parts  are also flashing in a staticy way.  In the first picture, you can see  the Ubuntu login window in the lower right corner of the screen, cut off  by the borders of the screen.  There are also cut up images of it in  the lower middle and lower right of the screen; I know it's hard to see,  I will try taking pictures in the daytime if needed.
  

I just tried typing, and then backspacing, and it seems like when I  BS all the way, it beeps at me, and most of the flashing lines (this is  on the GUI login screen) disappear for a few seconds, and then return.


  I tried googling for a hall of mirrors effect, but got zilch.  I read some about the framebuffer, but nothing I have tried has had any effect.  Booting into recovery mode from the CD works fine, which is the only way I have been able to try anything.  The laptop is an HP Pavilion dv6000 with an AMD Turion 64 x2 processor.  One thing I tried was taking the steps on this page: [http://superuser.com/questions/66428/how-can-i-change-console-shells-resolution-in-ubuntu-9-10/73116#73116](http://superuser.com/questions/66428/how-can-i-change-console-shells-resolution-in-ubuntu-9-10/73116#73116)  I also tried adding the kernel option vga=755 in grub, and then I tried vga=775.  Like I said though, nothing has worked, or had any effect.  Any ideas?

---

