---
title: "ATI x1600 + tuts = fail!"
date: 2008-11-24
forum: Hardware
---

### Post by mrincubus88 on 2008-11-24
So I have done every configuration possible... well not possible or it would work, but I have followed several guides ... sometimes two at a time to try and get my x1600 working with the Ubuntu box. This is my first time using this installed last night so don't kill or attack me for being stupid on this subject.

I have the latest install of 32 bit Ubuntu... here are the guides I've followed

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
[http://ubuntuforums.org/showthread.php?p=2533550](http://ubuntuforums.org/showthread.php?p=2533550)

Those are the top two.. now when I try to start the computer it gives me an error 
(EE) Failed to load /usr/lib/xorg/modules/drivers/fglrx_drv.so
(EE) Failed to load module "fglrx" (loader failed, 7)
(EE) No drivers available

Oh great ones please help me.

---

### Post by mrincubus88 on 2008-11-24
anyone having same issues? maybe guide to install? help? :(

---

### Post by magnus0 on 2008-11-24
I have the same card and I don't have any problems with it.

---

### Post by mrincubus88 on 2008-11-24
... Which drivers do you have installed? I've tried 8-4 8-11... I've let ubuntu get the drivers but everytime I restart when Ubuntu does it hangs after the boot screen... all black.

---

### Post by magnus0 on 2008-11-24
I have 8.543 installed. Intrepid default repos

---

### Post by pfdevil on 2008-11-24
hey i've also struggled with the install, I also have the x1600. Please follow the instructions here to the letter. Trust met it works. If you have any questions post them and i'll help you through it.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by mrincubus88 on 2008-11-24
Cool Ill read through and do this, im reinstalling it ubuntu just to start fresh so ill be back tonight at 9 est. thanks

---

### Post by mrincubus88 on 2008-11-24
magnus how would i go about download that particular driver? and installing it?

---

### Post by magnus0 on 2008-11-24
Here's a bunch of versions of xorg-driver-fglrx [https://launchpad.net/ubuntu/intrepid/i386/xorg-driver-fglrx](https://launchpad.net/ubuntu/intrepid/i386/xorg-driver-fglrx)

You could try the newest version (same as me) first [http://launchpadlibrarian.net/18844776/xorg-driver-fglrx_8.543-0ubuntu4_i386.deb](http://launchpadlibrarian.net/18844776/xorg-driver-fglrx_8.543-0ubuntu4_i386.deb)

---

### Post by mrincubus88 on 2008-11-24
how am I suppose to know if it is running correctly? I mean I still cannot change the visual effects to normal or extra b/c it tells me to install new drivers that will cause me to get the black screen of fail or bsof

---

### Post by mrincubus88 on 2008-11-24
would this be a good guide to follow... im kinda scared to see b/c i don't know hwo to reverse what i did and I don't want to reinstall again for the 3rd time.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by ddiger on 2008-11-25
What I found that finally did the trick..was to deactivate the proprietary driver & goto ATI's website & download the version for your distro & install it. ATI's website also has the install instructions there.

It's painfull untill you get all the kinks out, but once you do it's well worth it! Good Luck.

---

### Post by mrincubus88 on 2008-11-25
yea i've installed the latest one.. its odd after the load screen i just get a black screen... i've tried the open source and all... anyone have some more ideas?

---

### Post by mrincubus88 on 2008-11-25
Is there any other open source drivers for the ati radeon x1600 agp 512mb card? If so please let me know so I can try it.

---

### Post by mrincubus88 on 2008-11-25
Finally some actual "error" codes for everyone. This is what I get for start up after I have installed the latest drivers from ATI.
```

(EE) module ABI major version (0) doesn't match the server's version (1)
(EE) Failed to load module "dri" (module requirement mismatch, 0)
(EE) Failed to load /usr/lib/xorg/modules/drivers//fglrx_drv.so
(EE) Failed to load module "fglrx" (loader failed, 7)
(EE) No drivers available.
```

That is my little error log. I am not sure what is going on... thanks guys for the help thus far.

---

### Post by mrincubus88 on 2008-11-25
ANyone?

---

