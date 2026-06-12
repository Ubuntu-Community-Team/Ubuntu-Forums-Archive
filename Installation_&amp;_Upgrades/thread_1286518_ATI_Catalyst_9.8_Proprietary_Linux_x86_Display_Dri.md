---
title: "ATI Catalyst 9.8 Proprietary Linux x86 Display Driver (ERROR ISSUE I need help)"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by TuLesto on 2009-10-09
Okay, I have Ubuntu Jaunty Jackalope... so I downloaded the  ATI Catalyst 9.8 Proprietary Linux x86 Display Driver and uninstalled the ATI propriety driver with this line copied off of another thread: brian@brian:~$ sudo apt-get remove --purge xorg-driver-fglrx

I then restarted the computer and hoped for the best.

Once I was signed in I commenced with the installation of Catalyst 9.8 I was immediately thrown off by the system bar and its title as well as it's install options: "ATI Proprietary Linux Driver 8.65 Setup" and Install Driver 8.65 on X.Org 7.4 and later releases"... I have X.Org 7.4 but the Driver I downloaded was unmistakably the ATI Catalyst 9.8 Proprietary Linux x86 Display Driver. I even saved the installation instructions to harddrive and looked at the title. See here: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat99-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat99-inst.pdf)   and attatchment.

After a while of confusion I decided to install it anyway so I went on and did all the steps I was told to follow and restarted

What bothers me most is what happened after the restart... I was unable to start Catalyst Control Center. The error message has been attatched.

I've been digging through webpages and so far I've had no luck in finding an answer that will fix my issue. I will keep digging tomorrow but my hope is fading.


I'll keep you posted. Thanks.

---

### Post by Mark Phelps on 2009-10-10
If you're concerned about version number differences, 9.8 is the version of Catalyst, 8.65 is the version of the ATI drivers -- they are intentionally NOT the same version number.

What model is your card/chip?  ATI dropped support for all but their newer HD 3x, HD4x, and now, HD5x cards. IF your's is an older card, it won't work with any version of the ATI drivers and Ubuntu 9.04.

---

