---
title: "No GUI"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by PTSnoop on 2009-03-06
I have a Samsung X22 laptop, and I've tried to install Ubuntu 8.10 using the "Install inside Windows" option on the disk. When I try to boot Ubuntu, it asks me whether I want Vista or Ubuntu, I select Ubuntu. Then I get the logo and orange scrolling thing for a while (all seems normal, from what I've seen of my mate's Linux).

Then I get a blank screen with a flashing underscore prompt in the top left hand corner. I can type things, but nothing happens.

That stays for about a minute, then I get a bit of text and a working shell (is that the word? The thing that looks like a DOS prompt). Snag is, I can't figure out how to get anything that looks like a window or a mouse cursor.

Can anyone help?

---

### Post by PTSnoop on 2009-03-06
Hello? Anyone?

...on another forum, I'm told that "it's a graphics card problem". Should I be worried? Is my laptop doomed to Windows forever?

By the way, the specs are at [http://www.saveonsamsung.com/Samsung_X22_423510.html](http://www.saveonsamsung.com/Samsung_X22_423510.html) . Just if you need 'em.

---

### Post by LegendofTom on 2009-03-06
Install inside windows can sometimes cause problems.  Try installing using the partition manager when you boot from the install disk.  For starters though, try "dpkg-reconfigure xserver-xorg" when you get to the terminal.

---

### Post by Vince4Amy on 2009-03-06
If you can log in on the command line then try typing startx and it will give you some information if it cannot start.

---

### Post by PTSnoop on 2009-03-06
Thanks for the replies, guys.

I tried running the dpkg-reconfigure xserver-xorg thing. It asked me a bunch of questions about keyboard configurations, then sent me back to the command line. No change after rebooting.

After a bit of Googling, I also tried [http://linuxtipsandtricks.com/ubuntu/ubuntu-ibex-810-with-ati-radeon-hd-2400-xt/](http://linuxtipsandtricks.com/ubuntu/ubuntu-ibex-810-with-ati-radeon-hd-2400-xt/) , and got a "couldn't find package xorg-driver-flgrx" message on the first and third lines. No change.

I'll try the startx command now...

---

### Post by perpetualcacophany on 2009-03-06
I'm not too familiar with that install type, but I've had a similar problem before. Try this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo startx
```

That fixed it when I had that problem. Sorry if this doesn't help.

---

### Post by PTSnoop on 2009-03-06
Okay, I tried running startx (thanks, Vince4Amy), and got something like:

{long list of filenames something like:
9: /usr/lib/xorg/mobiles/drivers//radeon_drv.so [0xb7n376c1]
...with numbers from 6 to 19; 1 to 5 were probably chopped off the top of the screen}
Saw signal 11. Server aborting.
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Enable CRTC 0 success
Unblank CRTC 0 success
giving up.
xinit: connection refused (erno 111): unable to connect to x server
xinit: no such process (erno 3): Server error

...then back to the command line.

I'll give the "sudo dpkg-reconfigure -phigh xserver-xorg; sudo startx" a go now. Thanks for the quick responses, guys!

---

### Post by PTSnoop on 2009-03-06
I tried the 

sudo dpkg-reconfigure -phigh xserver-xorg
sudo startx

and got the same results as the startx before.

---

### Post by Ang89 on 2009-03-10
Same problem with my laptop. Toshiba Satellite M200 with ATI radeon.
I attach the startx ouput here.

---

