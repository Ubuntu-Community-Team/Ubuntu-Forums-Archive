---
title: "HP XG843: Ubuntu or recycle?"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by soulhunter on 2007-04-27
I want to make use of this old P3 HP XG843. So far I have been unsuccessful with installing either Ubuntu 6.10 or Edubuntu. Part of the problem could be the available RAM (128MB, but I can increase that to 512MB). The HP site says it only supports Windows ME, but I'm not willing to accept that as a final answer. 

Basics: It's an 800-mhz P3, currently with 128MB of PC100 RAM. No hardware issues. As far as software, I refuse to let anything with Windows ME on my network, and resent it's very existance. 

Spec sheet: [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=ca&docname=bph06430#N1978](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=ca&docname=bph06430#N1978)

I've formatted the harddrive for the installation successfully, and performed the memory test successfully before that, but it hangs up on the installation of the kernel. 

Strip and recycle, or are there other routes I could take with this machine? 

-soulhunter

---

### Post by newlinux on 2007-04-27
If you struggle with installing ubuntu you could try a different distro... I had an old pentium HP omnibook that I was able to put debian on... (with only 64MB RAM)

---

### Post by soulhunter on 2007-04-27
That's the kind of advice I need. I am new to the linux word, but very enthusiastic. Debian as a potential.

---

### Post by newlinux on 2007-04-27
An old computer is good for learning about other distros, especially if you aren't necessarily worried about it being stable or having to work right away. Heck, you may find you really like something in a new distro and either adopt it as your primary distro, or find out how to do it in Ubuntu. I know I've done that...

---

### Post by agurk on 2007-04-27
Perhaps you've tried this already, but I recommend using the alternate CD, as I've never had much luck using the desktop CD - other than as a live CD. The alternate CD has lower memory requirements for installation and also contains linux-restricted-modules, in case you need to use that (which by the look of the spec, you actually don't).

---

### Post by John the train on 2007-04-27
I've just installed Xubuntu Dapper LTS on a Dell Latitude laptop, 300Mhz P2, 192MB RAM, and it runs well. I'd agree with Agurk about the alternate CD. If you decide to try Debian there's a ' net-install ' CD which is a lot quicker to download and you get the latest versions of everything without having to update. Although Gnome runs reasonably well with 256MB RAM I'd suggest opting for Xfce, as it's less RAM hungry.

---

### Post by jpatton on 2007-04-27
> **soulhunter said:**
> I want to make use of this old P3 HP XG843. So far I have been unsuccessful with installing either Ubuntu 6.10 or Edubuntu. Part of the problem could be the available RAM (128MB, but I can increase that to 512MB). The HP site says it only supports Windows ME, but I'm not willing to accept that as a final answer. 

Basics: It's an 800-mhz P3, currently with 128MB of PC100 RAM. No hardware issues. As far as software, I refuse to let anything with Windows ME on my network, and resent it's very existance. 

Spec sheet: [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=ca&docname=bph06430#N1978](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=ca&docname=bph06430#N1978)

I've formatted the harddrive for the installation successfully, and performed the memory test successfully before that, but it hangs up on the installation of the kernel. 

Strip and recycle, or are there other routes I could take with this machine? 

-soulhunter

Have you tired the much touted alternative boot cd? I believe it allows for less memory?

---

### Post by soulhunter on 2007-04-27
I have not tried the alternate CD boot. I will. 
What are the linux-restricted modules?

---

### Post by agurk on 2007-04-27
linux-restricted-modules is a package containing non-free drivers. Though you shouldn't need it, since the spec says that your laptop has the Intel 810 chipset, for which there are drivers available in the main kernel. Me, I need linux-restricted-modules for my Intel ipw3945 wireless chip, because it contains the non-free firmware that the driver needs to load for my wireless to function.

---

### Post by JLAudioFan on 2007-04-27
Did you try the "Live" Ubuntu Feisty Fawn 7.04 cd?  I used it the other day to change some partitions on a 4 year old sony laptop (256mb pc100 ram), and it did take a while to load up but worked after booting. 

The "Start or Install Ubuntu" option is what you pick when booting from the cd to get it to load up ubuntu.


Good luck!

---

