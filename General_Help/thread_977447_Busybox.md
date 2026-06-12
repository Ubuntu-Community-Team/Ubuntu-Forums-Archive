---
title: "Busybox"
date: 2008-11-10
forum: General Help
---

### Post by broonsparrow on 2008-11-10
Hi,

I've installed 8.10 on a third HD in a PC with windows on the first HD. It failed to boot fine, I was getting a ERROR 17. Tried starting it with the LIVE CD to check the grub file etc and it started busybox, wouldn't let me exit.

Tried running from 8.04 LIVE CD and still getting busybox. Now disconnected HD with 8.10 installed on and it still won't boot from LIVE CD just goes to busybox. Any ideas?

Thanks

---

### Post by yt_l9 on 2008-11-10
I had a similar issue with 8.04;
when you get to the loader with options; i.e.
Start Ubunut without changing the Hard Drive
Install Ubuntu
etc...

there should be a list of options at the bottom; highlight the first one (start Ubuntu Live CD Mode)and I think press F6 or F4, the one that lets you edit the boot parameters.  

I don't know if they have since fixed the issues with a SATA hard drives with the last Kenel release, which is what caused mine to go to busybox but the fix is to insert 

all_generic_ide 

just before the -- and after the quiet splash so it should look like

... quiet splash all_generic_ide-- 

and if that doesn't work it might be your monitor... there are a few other things you can try instead of the all_generic_ide such as noapci (or is it noacpi? I always mess that up but it is turning off the power management or automatic sleep which had also been troublesome with linux) or vga=771.  
I hope this helps but it definitely is a boot parameter that you need to edit to be able to launch into the system.  BusyBox from what I understand is sort of the base shell of the kenel.

Hope this helps; if not it might help to list your hardware to see if something isn't compatible?

I'm going to go ahead and guess that you have a mix of sata and ide/pata hdds and you had Ubuntu on the ide/pata and windows on the sata? if you got it running on the ide then the rest of your hardware should be compatible but your trying to boot off hd0,0 I'm guessing.

Here is a site documenting most of the GRUB
[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

Alternatively here is a walkthrough for reinstalling the bootloader with the live cd (you will have to edit the boot paramaters for the live cd everytime you use it to log on...
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

and finally a walk through for editing your grub bootloader permanently
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

Hope this all works out for you!

edit:
This also might be the issue. I recently installed 8.10 via cd using the Install option from the load menu but it was defective despite the checksum being correct.  I could only get it to load via the live session and install that way.

---

### Post by yt_l9 on 2008-11-17
Just following up... Did this help?

---

### Post by broonsparrow on 2008-11-17
Hi,

thank for that, I haven't had a chance to check but'll give it a shot this evening. Yep have ubuntu installed on IDE and Windows on SATA. I think I'm gonna re-install 8.04 on the IDE drive as I've messed around with the GRUB file, so I'll just start from scratch....

---

