---
title: "Nothing works! :O. Jaunty failing to install from any media."
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by au_vagabond on 2009-04-20
Ok, so I pretty much hate life right now. 

I have been a ubuntu user for quite some time, but went away for a bit. Basically, I saw 9.04 RC and was like "sweet!" and downloaded the graphical installer...... which failed.

This CD, when booting, just came up with busy box. All of the searches I have done have come up with the suggestions of turning on quiet splash, which I cannot find.

I then attempted it using unetbootin and a live usb - which didn't boot.

So, I gave up. After a fairly large chunk of time crying, I decided to download the alternate installer. It booted, hurrah, but with one issue - it cannot detect my cd drive. Crushed once more, I though "wait - what about unetbootin" (again). Hence, I used that to put the alternate installer on the usb and, once more, it refused to boot.

Basically: nothing works, I am grumpy and stressed, and I don't want to wait 3 days until the actual installer comes out in case it doesn't work either. Halp! A resolution to any of the above problems would really make my day.

Cheers.

*edit for actual information that might be important*
While bitching and moaning, I realised it might be helpful to actually provide information:

From windows, I can see my DVD Drive is an ATAPI - if this helps.

I have successfully installed every version of ubuntu (via CD) from Feisty - 8.10, so it seems to be an issue of this version. I am using the i386 installer on an intel C2D with 1.5gb of ram.

Also - this has been discussed here ([http://ubuntuforums.org/showthread.php?t=1011190&highlight=detect+CD+drive+alternate+installer](http://ubuntuforums.org/showthread.php?t=1011190&highlight=detect+CD+drive+alternate+installer)) and no-one has answered in nearly 6 months. Is there any solution???

---

### Post by ptn107 on 2009-04-20
Did you check the md5sum* of the downloaded iso before you burned it?  Did you use the option on the CDs boot menu to check it for defects?

*_[Jaunty RC MD5SUMs]("http://releases.ubuntu.com/jaunty/MD5SUMS")_

---

### Post by slystad810 on 2009-04-20
I had the same problem.

Try typing exit about 5 or 6 times, then there should be about a 30 second delay and the installer will load.

At least this worked for me!

---

