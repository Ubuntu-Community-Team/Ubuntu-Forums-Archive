---
title: "new kernel version (2.6.30)"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by thmonkey on 2009-06-16
hello all

has anyone installed the new kernel version?i am using hardy and haven't seen anywhere information on how to install version 2.6.30. in addition, there is nothing in the repositories to install... is this possible?

thanks in advance!

---

### Post by eldragon on 2009-06-16
> **thmonkey said:**
> hello all

has anyone installed the new kernel version?i am using hardy and haven't seen anywhere information on how to install version 2.6.30. in addition, there is nothing in the repositories to install... is this possible?

thanks in advance!

you will not see the new kernel as an update for hardy or intrepid or jaunty, these releases receive security updates only.

you will need to build the kernel yourself if you really need it

---

### Post by thmonkey on 2009-06-16
eldragon thanks for your quick reply, 

does this mean that the new kernel is not suitable for hardy?i think i am going to give it a try, such as one can always boot with a different version... how hard can it be?

any idea where can i find the headers' source?

---

### Post by bbnet on 2009-07-28
I am interested in this thing, Thank you.

---

### Post by stlouisubntu on 2009-08-01
Here are some helpful links for installing 2.6.30 on Jaunty.  Reports that I have read indicate that this is workable in Jaunty, but frankly I would not recommend it on Hardy (or anything pre-Jaunty for that matter) as the likelihood of breakage and instability would be excessively increased.

Issues/concerns to watch for are restricted drivers (I struggled with a patch for nvidia-180.44, but finally got it done and then video once again functioned properly) and resume following a suspend to disk / hibernate (link #4 below address and give the fix/workaround for this.) 

Relevant Links follow here:

[http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824/comments/169](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824/comments/169)

[http://www.nvnews.net/vbulletin/showthread.php?t=131597](http://www.nvnews.net/vbulletin/showthread.php?t=131597)

[http://beranger.org/v3/wordpress/2009/05/04/jaunty-kernel-2630-fixes-the-intel-video/](http://beranger.org/v3/wordpress/2009/05/04/jaunty-kernel-2630-fixes-the-intel-video/)

Again, I believe that this kernel is completely workable in Jaunty (and perhaps necessary), but I strongly recommend against installing it on Hardy (or anything Ubuntu pre-Jaunty.)

Happy Hacking!!

---

