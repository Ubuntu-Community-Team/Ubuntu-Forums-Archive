---
title: "Boot screen does not appear at all !!"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by domain on 2007-12-07
Hi there 

:)

I'm glade that I'm using Ubuntu like you :)


I have a very small problem, when I start my laptop ( acer aspire 1690 ) the boot screen does not appear at all :

[IMG]http://decoding.files.wordpress.com/2007/04/boot-screen.jpg[/IMG]

It is just a black window for a minute approximately then the logging screen appears.

anyone have a thought ??

---

### Post by ewr2san on 2007-12-07
Let me Guess, It's a laptop?  I had the same problem, I didnt really care if it was a graphical screen, or if it was text, just as long as it wasnt blank.  I couldnt tell if it was booting or hung up.

I edited /boot/grub/menu.lst and took the "quiet" setting out of the boot line.  Viola it boots up and shows what it's doing in detail.  A bit of a more "old School" look to booting, but solves the  "blank boot screen" probelm.

---

### Post by ewr2san on 2007-12-07
Here's a more complete link to removing the splash screen...
[http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/](http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/)

---

### Post by domain on 2007-12-08
Thanks ewr2san for the link :) thank you very much 

I got rid off the boot screen for ever ! now it is like the old school as you said :D and it boots more faster than before ! that's really good. 

Thank you again.
ps: I'm using a laptop with 7.10 edition .

---

