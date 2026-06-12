---
title: "Umax Astra 2000P Scanner"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by xmastree on 2005-10-19
Someone just gave me one of these, and I can't get it to work with hoary. :( 

Looking in /etc/sane.d/ appears promising, as there's umax_pp.conf containing this line:```
# model number
#
# valid values are 610, 1220, 1600 and 2000
```But although I've tried various settings in that file (like specifying the model rather than auto-detecting it) I always get this error:```
root@ubuntu:/home/chris # scanimage -d umax_pp
[umax_pp_low] sendWord failed  got 0xE8 instead of 0xC0 or 0xD0 (umax_pp_low.c:4552)
[umax_pp_low] Blindly going on .....
[umax_pp_low] sendData failed  got 0xE8 instead of 0xC0 or 0xD0 (umax_pp_low.c:5402)
[umax_pp_low] Blindly going on .....
[umax_pp_low] sendWord failed  got 0xE8 instead of 0xC0 or 0xD0 (umax_pp_low.c:4552)
[umax_pp_low] Blindly going on .....
[umax_pp_low] sendData failed  got 0xE8 instead of 0xC0 or 0xD0 (umax_pp_low.c:5402)
[umax_pp_low] Blindly going on .....
[umax_pp_low] sendWord failed  got 0xE8 instead of 0xC0 or 0xD0 (umax_pp_low.c:4552)
[umax_pp_low] Blindly going on .....
[umax_pp_low] Unexpected reg19: 0xE8 instead of 0xC0 or 0xD0 (umax_pp_low.c:5449)
[umax_pp_low] cmdSetDataBuffer(initbuf) failed ! (umax_pp_low.c:7677)
scanimage: open of device umax_pp failed: Invalid argument
root@ubuntu:/home/chris #
```I know it's using the correct port, coz if I unplug the power I get:```
[umax_pp_low] Register 0x0F=0x1B, scanner powered off ! (umax_pp_low.c:7384)
```which is to be expected.

If I run xsane (as root) it appeared to work but then I realised that it was using my TV tuner card rather than the scanner... :confused: 

Strangely, xsane does seem to go through the same 0xE8 stuff before settling on the TV card, so it appears to be looking at the scanner first.

**It just doesn't work.** ](*,)

Any ideas?

---

### Post by xmastree on 2005-10-19
At this point, I haven't ruled out hardware problems. I can't get it working under XP either, but searching for drivers reveals that this is a common problem.

I'm thinking of installing 98 on a spare drive just to test the scanner...

Edit: I did, and it works.

---

### Post by xmastree on 2005-10-22
Well, I got it working with XP, :)  but I still have no joy in linux.

C'mon guys, **someone** out there must have the answer... :( 

I really dislike having to reboot into windows just to perform one small task.

---

### Post by xmastree on 2005-10-27
**[COLOR="Red"]BUMP![/COLOR]**

 :-({|=  It's lonely here in this thread all by myself... :cry:

---

### Post by pristoid on 2005-10-29
Yes! I also have the same problem running it in hoary. It would be a joy to scan  
by not loging to Windoz anymore. 

Is there anyone here having solution ?

---

### Post by LostBear on 2005-12-27
maybe this helps...

[http://umax1220p.sourceforge.net/](http://umax1220p.sourceforge.net/)

---

