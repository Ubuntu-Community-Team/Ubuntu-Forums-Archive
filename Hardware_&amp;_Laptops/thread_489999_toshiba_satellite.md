---
title: "toshiba satellite"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by pacco on 2007-07-02
i have a toshiba satellite a105-s2236 laptop just bought it at walmart 1 month ago it works great with vista home:(, which i cant stand microsoft
my sound card doesn't seem to work in in ubuntu 7.04/fiesty, any ideas?


Also i can't seem to get beryl to work in it either,i wish i could get this to work,what do i need to do?
i have an intergrated ati xpress 200m graphics card.


Thanks In Advance
Pacco

---

### Post by lisati on 2007-07-02
I have a Toshiba Satellite A100, which didn't have sound after installing Ubuntu 7.04

Using the update manager to install the recommended security updates (you'll need a working internet connection), rebooting, and re-setting the volume control fixed it for me.

The update manager often flashes a notification at the top of the screen when there are updates. If you can't find it there, have a look at System->Administration

I haven't tried Beryl yet, so I might bump this on to someone else.....

---

### Post by pacco on 2007-07-02
ok i'll try something, thanks

---

### Post by Praill on 2007-07-02
Updating is a good idea. Unfortunately a common reason can also be muted sound.
Run the command:
```
alsamixer
```
and make sure nothing's muted.

After that I would direct you here:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

If its fixable (which it almost certainly is) this post will have the answer.

---

