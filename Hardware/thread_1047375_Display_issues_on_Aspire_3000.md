---
title: "Display issues on Aspire 3000"
date: 2009-01-22
forum: Hardware
---

### Post by EmanuelHei on 2009-01-22
I'm a brand new Ubuntu user - just got sick of windows and would like to make the switch. I installed Ubuntu 8.1 and everything seemed to be working fine for about an hour. But now when I boot up, after 5 minutes or so, I get blue dots all over my screen. I suspect it has something to do with incompatible display diver or a incorrect gamma setting? Any input on this problem is greatly appreciated - I'd hate to have resign myself to Windows again. Thanks.

---

### Post by overdrank on 2009-01-22
> **EmanuelHei said:**
> I'm a brand new Ubuntu user - just got sick of windows and would like to make the switch. I installed Ubuntu 8.1 and everything seemed to be working fine for about an hour. But now when I boot up, after 5 minutes or so, I get blue dots all over my screen. I suspect it has something to do with incompatible display diver or a incorrect gamma setting? Any input on this problem is greatly appreciated - I'd hate to have resign myself to Windows again. Thanks.

Hi and welcome, could you give us some specs on the system. Have you installed the graphics drivers, under system, administration, hardware if any is needed?

---

### Post by EmanuelHei on 2009-01-31
Hi and thank you for your reply. My Acer Aspire 3000 uses a SIS VGA Driver 6.14.10.3654. I've searched for a Linux compatible version of this driver but to no avail. I'm pretty sure this is the cause of the problem. I'm not exactly sure how to go about installing a graphics driver. I tried your suggestion of System-administration-hardware drivers but couldn't find a driver. Attached is a screen shot. Again, thank you for your advice. Please let me know if any further information is needed.

---

### Post by ubu_dynamite on 2009-02-23
I had th same problem with my laptop acer aspire 5002WLMI in Intrepid couldn,t find a solution so i used vesa.

I just instalt Arch linux yesterday and after installing xorg and the sis driver same problem static
but after lots of searching i found this [http://wiki.archlinux.org/index.php/Xf86-video-sis](http://wiki.archlinux.org/index.php/Xf86-video-sis)

after adding sisfb to the modules and changing my xorg.conf i restarted the x server and have no more static.

maybe the info on that page can help you too.

---

