---
title: "After second restart blank screen"
date: 2005-08-22
forum: Hardware &amp; Laptops
---

### Post by zorkerz on 2005-08-22
I have a gateway m680 laptop with a 256Mb Nvidia Go 6800 graphics card.  I installed Haory Hedgehog 5.04 with no problems from a downloaded cd iso.  Then performed the system restart as part of the installation and Ubuntu started just fine.  Later after updateing packages i restarted the computer again.  The grub boot loader comes up and starts ubuntu.  Then the screen goes blank except for one line of pixels at the top of the screen.  I can hear ubuntu login because i set it to auto login after 100 seconds but there is nothing on the screen.  If i press ctrl F1 i can bring up a command line but have no idea what is wrong or what to do.  My only previus linux experience is briefly with Mandrake about a year ago.  Any ideas Id appreciate it greatly

---

### Post by ryanr on 2005-08-23
I had a similar problem on my Dell Insperon 7500. Chek out this post it helped me.
Cheers.
[http://www.ubuntuforums.org/showthread.php?p=314365#post314365](http://www.ubuntuforums.org/showthread.php?p=314365#post314365)

---

### Post by pierslauder on 2005-10-02
I also get this problem. I have a Dell Inspiron 5000 with a PCMCIA ethernet card, and a
1400x1050 LCD panel.

I noticed after the update that the ethernet failed with a message saying: SIOCGIFFLAGS error: No such device
so I suspect that the updates are downloading some buggy library/programs
that then cause the ethernet and/or X to fail on reboot.

Interestingly, this happens both for Ubuntu 5.04 and 5.10 beta.

I'm now re-installing intending to avoid any updates - but this clearly isn't a good long term strategy :-)

Be delighted if someone knows of a fix...

---

