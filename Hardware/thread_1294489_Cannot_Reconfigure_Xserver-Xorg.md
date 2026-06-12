---
title: "Cannot Reconfigure Xserver-Xorg"
date: 2009-10-18
forum: Hardware
---

### Post by Cappoman on 2009-10-18
I've been using Ubuntu for a few weeks now, and have been very unhappy with the way web pages are displaying. I have to adjust the font size on nearly all web pages.
 I have tried using different setting within the browser (firefox.) I changed screen resolutions preferences > display, and when I changed resolutions there the screen would go black and several verticle bars of color would display. I tried google and the forums, and did not find a way to change the setting back, so I just reinstalled. 

I upgraded from Jaunty to Karmic hoping that would solve things. I get the same results as above.
I can only get the computer to boot into shell prompt with or without networking via kernel recovery. 
I have removed the fglrx drivers and reinstalled them using sudo command at the prompt. Nothing seems to work. I have also tried using a live cd and have met with any success there. 

My only dislike of ubuntu is the way web pages display, I was quite frustrated getting everything else working VLC, Amarok. I did get things going and was happy.
I am running Karmic 64 bit on a Dell Vostro 1000, ATI 200M graphics,  amd turion tl 56 64 bit processor. Bios is v 2.6.3

Is there any way to recover  without reinstalling?

---

### Post by ROY.G.BIV on 2009-10-18
> **Cappoman said:**
> I've been using Ubuntu for a few weeks now, and have been very unhappy with the way web pages are displaying. I have to adjust the font size on nearly all web pages.
 I have tried using different setting within the browser (firefox.) I changed screen resolutions preferences > display, and when I changed resolutions there the screen would go black and several verticle bars of color would display. I tried google and the forums, and did not find a way to change the setting back, so I just reinstalled. 

I upgraded from Jaunty to Karmic hoping that would solve things. I get the same results as above.
I can only get the computer to boot into shell prompt with or without networking via kernel recovery. 
I have removed the fglrx drivers and reinstalled them using sudo command at the prompt. Nothing seems to work. I have also tried using a live cd and have met with any success there. 

My only dislike of ubuntu is the way web pages display, I was quite frustrated getting everything else working VLC, Amarok. I did get things going and was happy.
I am running Karmic 64 bit on a Dell Vostro 1000, **ATI 200M graphics**,  amd turion tl 56 64 bit processor. Bios is v 2.6.3

There's your problem. ATI and built in... linux doesn't like that... I recommend you get yourself an after market Nvidia.

---

### Post by Cappoman on 2009-10-18
> **ROY.G.BIV said:**
> There's your problem. ATI and built in... linux doesn't like that... I recommend you get yourself an after market Nvidia.


Not sure that is possible, I looked and found this... [http://en.community.dell.com/forums/p/19270964/19473216.aspx](http://en.community.dell.com/forums/p/19270964/19473216.aspx)

I'm not sure if mine is a chipset or a card, being a laptop I think it would be integrated.

---

### Post by photographerHU on 2009-10-18
Hi,
Unfortunately I have Vostro 1000 with ati 200m (the worst).
I`m still on 9.04. I already tested a few things:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7733415](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7733415)
            [http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/](http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/)  
[http://ubuntuforums.org/showthread.php?t=1137467&highlight=Radeon+Xpress+200M&page=5](http://ubuntuforums.org/showthread.php?t=1137467&highlight=Radeon+Xpress+200M&page=5)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1174943&highlight=Installing+ATI+Radeon+x1100&page=4](http://ubuntuforums.org/showthread.php?t=1174943&highlight=Installing+ATI+Radeon+x1100&page=4)
None of them is the perfect solution, but I hope you will find it!
Maybe in Karmic......

---

### Post by photographerHU on 2009-10-18
sorry, posted 2 times

---

### Post by Cappoman on 2009-10-18
> **photographerHU said:**
> Hi,
Unfortunately I have Vostro 1000 with ati 200m (the worst).
I`m still on 9.04. I already tested a few things:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7733415](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7733415)
            [http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/](http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/)  
[http://ubuntuforums.org/showthread.php?t=1137467&highlight=Radeon+Xpress+200M&page=5](http://ubuntuforums.org/showthread.php?t=1137467&highlight=Radeon+Xpress+200M&page=5)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1174943&highlight=Installing+ATI+Radeon+x1100&page=4](http://ubuntuforums.org/showthread.php?t=1174943&highlight=Installing+ATI+Radeon+x1100&page=4)
None of them is the perfect solution, but I hope you will find it!
Maybe in Karmic......

Thanks for the info, I'll check it out. I had Karmic installed when I screwed everything up. I reinstalled Jaunty. I reinstalled Karmic, and it did not have the broadcom driver. If you upgrade from Jaunty to Karmic everything works.

---

### Post by photographerHU on 2009-10-19
Maybe you need this too: [http://ubuntuforums.org/showthread.php?t=1204986](http://ubuntuforums.org/showthread.php?t=1204986)
What do you mean "upgrade from Jaunty to Karmic everything works"? The wireless? 
Anyway, I will see 10 more days...

---

### Post by Cappoman on 2009-10-19
Yes the wireless worked, I used the "update-manager -d" command to upgrade to kramic. no broadcom driver included, but I'm having trouble getting VLC to play dvds now.

---

### Post by ublintu on 2009-10-20
Sounds better. At least I will have normal wireless in Karmic...
Hopefully soon, something like this will happen with ati 200m too.

---

### Post by lidex on 2009-11-03
> **Cappoman said:**
> Yes the wireless worked, I used the "update-manager -d" command to upgrade to kramic. no broadcom driver included, but I'm having trouble getting VLC to play dvds now.

Try using xine for dvds -- it supports dvd menus. I gave up on vlc.

---

