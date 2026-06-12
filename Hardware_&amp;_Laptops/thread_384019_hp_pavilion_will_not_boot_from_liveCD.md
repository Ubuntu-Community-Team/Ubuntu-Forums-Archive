---
title: "hp pavilion will not boot from liveCD"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by scradock on 2007-03-13
I have downloaded the edgy eft release for i386, burnt the CD, checked the .iso unpacked correctly, checked the MD5 sum. The live CD begins to boot, then stops at the second l>r pass of the animated slider bar. Trying the "safe mode" option does the same. Trying the "check the CD" option does the same.

The machine is a laptop, hp pavilion zv6000, running Windows XP SP2.

There is a very rapid flash of an error message before the Ubuntu logo appears - I can only  catch that there is a problem with a device before it vanishes.

Does this mean I can't even try Ubuntu, or is there a way to work out what is happening?

Thanks,

Stephen Cradock

---

### Post by syko21 on 2007-03-14
Sometimes when booting from the CD I also receive some error messages however if I just let the disc alone for a few minutes it continues to boot up normally. I have the dv6000t pavilion.

---

### Post by explemonk on 2007-03-14
Perhaps you are having the same problem I had--for some reason my DVD drive was failing to mount when booting the live CD.  This was on a Compaq Presario R4000 series.

You can hit F6 at the menu to add additional boot parameters--in my case I had to add 

ide=nodma

Also, if you delete the options "quiet" and "splash" using F6 you can get a clearer picture of exactly where the boot process is hanging.

I learned all this with the wonderful help of this forum community.  I've only been using the Ubuntu for a few days now but I love it.

---

