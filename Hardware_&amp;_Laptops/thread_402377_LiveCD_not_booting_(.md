---
title: "LiveCD not booting :("
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by Scorpio123 on 2007-04-05
Hi there,

I'm trying to revive an old PC of mine, because it won't take Windows Vista (it has 256MB RAM) and i'm sick of Windows XP. So i thought i'd migrate to Linux.

From what i can see after some research, Ubuntu seems like an awesome option to jump ship.

So i downloaded 6.10, and burnt it to a CD. 

My PC booted the LiveCD, but when i selected the option to boot the LiveCD, it did its thing before giving me an I/O error and killing the load :( :confused: 

I know that disk is fine, because i'm typing this message from the Ubuntu LiveCD on my laptop, lol

System specs of PC: Intel Pentium 4 1.7Ghz, 256MB RAM, nVidia GeForce 2 64MB GFX card.

Any help is appreciated!

---

### Post by tommcd on 2007-04-05
From your specs you should be fine. A few things to try to make sure the disc is good.
1) check the md5sum of the disc if you have not already. The live CD has an option to "check disc for defects". Try that, and also see this:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Also, be sure to burn the disc at a very slow speed if you did not already. Here is a good iso burning tool for windows:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) you may want to try the alternate (text based) install CD. 
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
Choose a mirror near you, then choose the alternate CD.
Hope this helps. And welcome to the forums.

---

### Post by Sef on 2007-04-05
Found [this post]("https://answers.launchpad.net/ubuntu/+ticket/3451"):

> 1. Press F6 when the liveCD boot menu comes up to alter the boot options.
2. Add the following at the end (before the '--'):
pci=noacpi ide=nodma ide=reverse
3. Boot

Let us know if it works or not.

---

