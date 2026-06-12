---
title: "Toshiba Tegra AC100 Hardware enablement"
date: 2012-01-18
forum: Hardware
---

### Post by Adameke on 2012-01-18
I'm attempting to make Ubuntu 11.10 work (well) on the AC100. I've done pretty well desite my newness to linux.

Couldn't believe my luck when I found:
[https://launchpad.net/~ac100/+archive/ppa]("https://launchpad.net/~ac100/+archive/ppa")

However, when I do
```
sudo apt-get update
```
I get errors like
```
W: Failed to fetch http://ppa.launchpad.net/ac100/ppa/ubuntu/dists/oneric/main/source/sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ac100/ppa/ubuntu/dists/oneric/main/binary-armel/packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```
I'm guessing (please correct me if I'm wrong) that the nice people who made those packages, have moved or deleted them. And it looks like there's been no activity on this subject either there or here for a half a year so I assume that means nobody's interested in the old AC100 anymore. Fair enough really, but I have one, and I'd love some help making it work. Any help greatly appreciated.

---

### Post by MoreOrLess on 2012-01-18
The problem is that all of the packages are for Natty/11.04. You may not need some/all of them in Oneiric.

---

### Post by Adameke on 2012-01-26
Thank you. That explains a lot. However, I still don't know what to do. I have tried to follow the [mailing list archive]("https://lists.launchpad.net/ac100/") but I'm missing all the assumptions. I still don't know/understand whether they have finished making Ubuntu 11.10 work on the AC100, and if they have, it doesn't tell me whether taking advantage of their work is an automatic process or something I have to do manually, and if it's a manual process I don't know how to do that. Yeah.

---

### Post by maureenc on 2012-03-13
HI Adameke,

I have mine working pretty well on Ubuntu 11.10 using the information and steps outlined in these two sites:

      [https://wiki.ubuntu.com/ARM/TEGRA/AC100](https://wiki.ubuntu.com/ARM/TEGRA/AC100)

     [http://wiki.informatik.hu-berlin.de/nomads/index.php/Erfahrungsbericht_Toshiba_AC100](http://wiki.informatik.hu-berlin.de/nomads/index.php/Erfahrungsbericht_Toshiba_AC100)

I have added things like Zram and have reverted to the Gnome Classic as I can't stand Unity (it is aso v e r y slow!) It is installed by "session-fallback" and activated in the login window, top corner.

I've installed Midori from the Repositories as per :
        [http://ubuntuforums.org/showthread.php?t=1704500](http://ubuntuforums.org/showthread.php?t=1704500)

It is much faster than Firefox, less agro from upgrades and has a beautiful Speed Dial facility as well as nifty coloured tabs which make browsing much easier.
There are a few tricks like Scrofflix.css for certain slow loading sites..... 

I also installed Synapic Package Manager which I prefer to use.

The problem I have at the moment is getting Flashplayer to work! It seems to be the major issue with Tegra/Nvidia...... I've tried most of the options in the above articles but there is something wrong still.

Other useful info can be found at:

   [http://archlinuxarm.org/forum/viewtopic.php?f=27&t=1626&sid=daba9b27fe0033febdd9852d1a9823c3](http://archlinuxarm.org/forum/viewtopic.php?f=27&t=1626&sid=daba9b27fe0033febdd9852d1a9823c3)

     [http://forum.xda-developers.com/showthread.php?t=1273322](http://forum.xda-developers.com/showthread.php?t=1273322)

And there are several on 10/15/20 things to do when installing 11.10!

There is also some info about removing Unity, installing Lbuntu and various other more complicated bits and bobs...

Hope some of this helps....

I love the AC100 now that I have Ubuntu on board..... It's now just a case of fine-tuning and finding what works and what doesn't..

---

