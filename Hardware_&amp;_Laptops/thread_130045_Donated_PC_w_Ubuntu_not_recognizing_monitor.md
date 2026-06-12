---
title: "Donated PC w Ubuntu not recognizing monitor"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by just_jeepin on 2006-02-15
I donated a PC w Ubuntu 5.10 to a lady who runs a foster home for mentally handycapped adults and When she got it home and hooked up to her monitor nothing shows up. Unfortunately that's all the details that I know.

Is there any set of keys to hold down when booting to have Ubuntu search for new hardware?

Thanks for any help!
Danny

---

### Post by az on 2006-02-15
No, there isn't.

I don't know if this has been addressed in Dapper.  I will try to get another monitor with a different frequency and try it out.  If it is reproduceable, I will file a bug report about it and link it here.

What you need to tell the person to do, unfortunately, is to use the command line.

Boot into recovery mode.

Type 
dpkg-reconfigure -phigh xserver-xorg

and then
init 2

That should redetect and save the new moditor settings.

---

### Post by tseliot on 2006-02-15
REMOVED -- Azz answered before me :-)

---

### Post by az on 2006-02-15
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/11155](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/11155)

This was filed a long time ago, and the problem was given a low priority.  I wonder if it has been fixed in Dapper (I cannot test right now)


Quote Matt Zimmerman:
"It occurred to me that a rather nice way to deal with this problem would be to have the gdm XKeepsCrashing script offer to re-probe, e.g.:

If you have added or removed components from your computer (such as installing a
new video card), I can attempt to reconfigure the system to use them. Would you
like to do this?"

---

