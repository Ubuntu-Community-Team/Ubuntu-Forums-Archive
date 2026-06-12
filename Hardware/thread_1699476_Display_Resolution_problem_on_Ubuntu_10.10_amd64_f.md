---
title: "Display Resolution problem on Ubuntu 10.10 amd64 for Fujistu Simens Esprimo 5535"
date: 2011-03-03
forum: Hardware
---

### Post by sephiroth_slash on 2011-03-03
Hi guys

I installed Ubuntu 10.10  for a friend who had Fujitsu  Siemens Esprimo v5535, I had a problem with the resolution ( 800x600 ) ,  I downloaded the sis driver ( attachment )

and did the following commands : 

- Extract the content of the archive to home directory


>>> IF YOU HAVE INSTALLED UBUNTU 10.10 i386 do this : 

                [FONT=Courier New]- $ sudo cp 32-bit/xorg.conf /etc/X11
         - $ sudo cp 32-bit/sis671_drv.so /usr/lib/xorg/modules/drivers

[/FONT]>>> IF YOU HAVE INSTALLED UBUNTU 10.10 amd64 do this : 

                [FONT=Courier New]- $ sudo cp 64-bit/xorg.conf /etc/X11
         - $ sudo cp 64-bit/sis671_drv.so /usr/lib/xorg/modules/drivers
    
   [/FONT]
>>>  Reboot

then it worked !! the resolution now is : 1280x800 !! thank you very much ajoliveira !

Hope it helps !!

---

### Post by BadGene on 2011-04-21
Greetings sephiroth_slash. I had already given up on this issue, due to all of the unsuccessful methods I've tried. But know I found this unbelievably simple method (which I sincerely had deep doubts)! 
Congrats on solving this! 
Many thanks!

---

