---
title: "URGENT: clarification regarding disk space, system updates."
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by vrv123 on 2009-02-03
Hi UBUNTU xperts,

I have a question regarding system updates that I install using update mgr/apt-get.
I have been using ubuntu since version 7.04 and still going strong and enjoying every bit of ubuntu 8.10. I have a dell xps m1330 , 250gb total hdd space. I am paranoid about the disk space that I fear losing because of the huge recommended/security/other updates that the ubuntu dev community releases for the packages and modules w.r.t 8.10 or any version for that matter. why are the updates soooo huge, almost on a daily basis ? I love ubuntu to the core but I fear I will surely run out of disk space one fine day (when updates would have eaten up all of 250 gb).

The recommended and security updates are huge and I also know I should not be ignoring them. as of today i have 208 gb, so i can say I have PLENTY of space, but the updates are growing on a daily basis and I will run out of space after a few years may be. and this worries me..

I love love love everything about ubuntu, except for the release schedule.
I feel 6 months is too short a time for one to quickly switch and adapt between releases(i mean, the system maintenance is directly proportional to the additional packages w.r.t releases).

I like the LTS schedule, but the normal releases are too quick.
the only drawback I feel is that if I stick to LTS release for 3 years, i will miss out on the updated normal releases that happen every 6 months.

I now have my customized stable ubuntu intrepid, and 3 months down the line ubuntu 9.04 will be released and the upgrade from 8.10 to 9.04 will, I am sure, bring in additional packages --> more hdd space. I am planning to skip this upgrade due to space constraints and waiting for the next LTS release.

Please suggest me how to save/retain disk space... 

TIA...

---

### Post by snowpine on 2009-02-03
Hi there, you might find this thread informative: [http://ubuntuforums.org/showthread.php?t=1057908](http://ubuntuforums.org/showthread.php?t=1057908)

If you have 208gb free, I wouldn't worry about it. I am running Ubuntu on an eee pc with a 4gb drive. :)

---

### Post by vrv123 on 2009-02-03
Thanks snowpine, but [http://ubuntuforums.org/showthread.php?t=1057908](http://ubuntuforums.org/showthread.php?t=1057908) was created by me yesterday....I could get back 140mb after clean up. 

but my current post is generic in terms of updates/OS release-cycles that are growing on an almost DAILY basis, that in the coming years may eat up majority of my hdd space.

yeah for now i have no problems, 208gb is like owning a farmhouse(acres of land)......

w.r.t my current thread, any suggestions ?

---

### Post by Elfy on 2009-02-03
An apt-get clean removes all of the apt-cache

---

### Post by avtolle on 2009-02-03
A general observation; most updates replace existing apps already installed, and some, upon installation, will take up less room that what was replaced; some, more; some, the same.

---

### Post by vrv123 on 2009-02-03
i forgot to mention, I regularly do autoremove and autoclean....

can I totally ignore the recommended updates, and will this impact future ubuntu release upgrades ?

I am sure i will save a lot of space if I skip the recommended updates and just install the key security updates...

---

### Post by Elfy on 2009-02-03
I'm always trying out new things - I have security, recommended, proposed and backports enabled - I started with ~300Mb in the cache when I installed - I have ~600Mb now 

So no you won't save a lot of space in relation to 200Gb - but it's comletely up to you how you deal with your updates.

If you're that worried there's nothing to stop you clearing the cache immediately after you've finished.

That of course also means that if you need to remove and reinstall anything you have to download the package file again.

---

