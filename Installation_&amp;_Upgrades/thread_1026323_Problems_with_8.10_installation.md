---
title: "Problems with 8.10 installation"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by sconnie on 2008-12-31
Hey, total noob at linux here. I finally decided to try it out since I have an old computer to work with. Here's what I have done in the past few days.

I downloaded the 8.10 Live CD and installed it onto my (6 or so year old) emachines t2240, 384MB of RAM, onboard graphics, 40 GB HDD, Intel Celeron 2.2 Ghz processor. I decided to let ubuntu set up my partitions and wipe over my Windows XP (it was riddled with viruses and I had no more need for it). After the install finished, nothing worked when I rebooted. I popped the disk back in, did the CD check, and found that I had an error. So I decided to redownload the Live CD from a different location. This time I checked it before I tried to install and it didn't find any errors so I continued on with the install. This time when I rebooted, it never quite made it to the login screen. At this point I started to get a little frustrated. I decided to try the Live part of the CD to make sure that this would even work on my comp. I made it to the login, but then my screen just started to do funny things like a bunch of horizontal squiggly different colored lines. A box eventually popped up that said something to the effect of "Graphics card cannot be configured. Now converting to safe graphics mode" or something like that. So I let it do its thing but still nothing. Black screen. And that's where I'm at now. I just downloaded the alternate CD and will try to install tomorrow. Are there any suggestions as to what I'm doing wrong or what else I could do? I haven't tried any other distros or versions, so does anybody have any suggestions as to which to try for a slightly older computer?

Thanks much

---

### Post by tommcd on 2008-12-31
Go ahead and try the alternate CD. 
According to this page:
[http://emachines.com/support/product_support.html?cat=Desktops&subcat=T%20Series&model=T2240](http://emachines.com/support/product_support.html?cat=Desktops&subcat=T%20Series&model=T2240)
your computer has Intel 845GL chipset with Intel graphics and should work fine with Ubuntu. With 384mb RAM, your machine may be a little short on memory for the live CD install. If you get Ubuntu up and running ok, consider putting more RAM in that machine. It will greatly improve performance.

Be sure to burn the alternate CD at a very slow speed. If you are burning the CD from a Windows computer use Iso Recorder or Infra Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
and check the md5sums of the disc after you burn it:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Or run the option to check the CD for defects when you boot up the alternate CD.

Write back if you need more help.

If Ubuntu runs too slow on that computer you could try Xubuntu. It is Ubuntu with XFCE desktop instead of Gnome. Other distros you could try are [http://zenwalk.org/](http://zenwalk.org/) or [http://tinymelinux.com/doku.php](http://tinymelinux.com/doku.php). I've never tried Tiny-ME, but Zenwalk is excellent and would run faster on your computer than Ubuntu. But give Ubuntu or Xubuntu a try first.

And welcome to the Ubuntu forums!

---

