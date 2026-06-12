---
title: "Intel (Sandy Bridge) Graphics &amp; oibaf repo"
date: 2014-04-18
forum: Hardware
---

### Post by den_ on 2014-04-18
I was getting some distortions in Google Chrome, for example when scrolling on webupd8.org, so I decided to try newer drivers (I have also updated the kernel.) and added oibaf repo.

The difference is obvious. It is much better, and effects like windows transitions look (maybe placebo?) faster too, but distortions are definitely gone.

---

### Post by startas on 2014-04-18
is it very dangerous to use alpha versions of drivers. the other day i used it, my mouse cursor just disappeared, thanks to my mouse skills, i was still able to save all my work using mouse and reboot pc to revert oibaf ppa. current stable intel 2d drivers is a big and super slow mess, so using any newer beta is big improvement, as "stable" version is not even usable.

---

### Post by den_ on 2014-04-18
Stable can be dangerous too. I remember ext3 bugs shiped with stock 'stable' kernels, some years ago, which destroyed a lot of data. If one doesn't feel comfortable, just leave it. Regarding Sandy Bridge and newer Intel stuff, alpha packages from oibaf work great (at least for me.). I was using oibaf all the time with 13.10, and never had a serious issue. When it happens is usually quickly resolved, and one can always do ppa-purge (it is a launchpad repo. So fix doesn't take a while), and reboot.

Regarding your bug, where cursor disappeared, I understand it is not always, and usually a great idea to run alpha on production workstation, but it depends on lot of thing really. I was runing Gentoo unstable for years without serious issues. So it depends on, if one is capable of dealing with issues, and seriously... I was having more serious issues with 'stable' LTS for two days now, then what you mentioned. Strange that you mentioned mouse cursor : )), because that is the only thing that worked for me : ))), and only partially (I couldn't click anything.).
That is the reality of software and the world we live in : ). 'Stable' doesn't work well, and that on very common hardware (Actually intel graphics are among, if not the best supported ones.), and builds from live repositories work much better, and more stable. Go figure.

---

### Post by den_ on 2014-04-18
Warning for people with HD 4000 graphics, and probably newer, just noticed a guy on phoronix forums complaning about issues (only software renderer no 3d support.).

---

### Post by monkeybrain20122 on 2014-04-18
It can be dangerous but it can also bring huge performance and feature gain and I would rather take a chance than to stick with stock Ubuntu driver, which sacrifices features for 'stability aiming at the lowest common  denominator hardware wise, by that I mean a feature would be disabled if there is a risk that it may cause troubles with some corner cases, --I don't mean necessarily lowest common denominator in terms of specs,--so for example hardware acceleration for nouveau is diabled in 14.04. I can understand the caution and if I were Canonical I would do the same. But as an end user I am only taking risks with my own machines, if I have a chance to use my hardware to full potential you bet I would, even if that means giving up Canonical's well meaning support.

To minimize the risk (actually almost no risk with this approach) I clone my root partition with fsarchiver before updating with oibaf (and also other potentially risky updates). The root partition (with only system files, no data) is less than 15 G and takes less than 15 minutes to clone and less than 5 to restore, if anything goes wrong 5 minutes later I am back in business. Also I stop updating when I reach a sweet spot. The only risk is the unlikely event that both oibaf and fsarchiver fail at the same time. 

Oibaf was known to be very unstable back in the 12.04 days and often killed unity, so I had to restore several times (took about 5 minutes) but I have not experienced that for a while even though there are occasional set backs (on one test installation on an external hard drive I update everyday)

---

### Post by den_ on 2014-04-18
I have no experience with nvidia and nouveau, but I never had so serious issue which would require making backups of whole root partition. Consider there are not much files you changed, except some cofiguration files, if you are developer, or even source code if you are developer, but most of it is easy to get from official repositories, or installation media, so why backup it? And I doubt you have over 6-7 GB of data on your root partition, if you are not gamer : ) that's it.

Also I am not sure it stopping of updates is always smart, from security standpoint of view. I am telling this also considering this is a LTS release, so letting a security hole for years without updating is not quite nice. But you probably update more often.

---

### Post by monkeybrain20122 on 2014-04-18
> **den_ said:**
> I have no experience with nvidia and nouveau, but I never had so serious issue which would require making backups of whole root partition. Consider there are not much files you changed, except some cofiguration files, if you are developer, or even source code if you are developer, but most of it is easy to get from official repositories, or installation media, so why backup it? And I doubt you have over 6-7 GB of data on your root partition, if you are not gamer : ) that's it.


Well how are you going to farret out which file have changed if you can't even boot, and why would I want to waste time trouble shooting that if I can restore the whole partiton in less than 5 minutes? Yes you can boot into rescue and run ppa-purge but that is complicated  (usually it works but I had run into dependency issues) and you lose all the gains from previous updates and revert back to square one. Sometimes I restore just because of a regression, not necessarily a serious one, but it is just so easy to get back.
(e.g if I am one of the people who lost 3d in the latest upgrade that  you warned about, I would just restore to the previous state before the  update and disable the ppa, clean and easy or I can switch to  xorg-edgers as it is a bit older, or try with the proprietary drver..  all in less than 30 minutes. It gves me the freedom to all sorts of tests and experiments )

I have 13 G in my root partition for my working system as I have all kinds of stuffs :)  If you have only 6-7G that would be even faster to clone and restore.

---

### Post by den_ on 2014-04-21
> **den_ said:**
> Warning for people with HD 4000 graphics, and probably newer, just noticed a guy on phoronix forums complaning about issues (only software renderer no 3d support.).

Apparently there were no real issues with oibaf (latest mesa and drivers) for above mentioned cards. The issue was because he did an upgrade from 13.10, and during the process xserver-xorg-video-intel went lost, actually uninstalled. After reinstall everything is working well.

---

