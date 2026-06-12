---
title: "no updates for breezy?"
date: 2005-11-28
forum: General Help
---

### Post by hjm on 2005-11-28
I've seen queries like this posted before but have not seen satisfactory replies. Using what I believe to be satisfactory sources (sources.list entries below), I haven't seen any updates for the Breezy for several weeks.  With most other Debian distro's, there are usually multiple updates every day.  This wouldn't bother me much (the more updates, the more complexity, the more breakage, and Breezy has been the most stable, best working distro for my laptop that I've ever tried - 13 days of uptime on my lappie, with multiple sleeps every day!), but it concerns me as my konqueror has broken (and FF shows similar misbehavior, indicating some sort of shared code problem - will post details later) and I also haven't seen any security updates.

I know Linux is secure, but this lack of updates has now gotten me a bit concerned.

Is it that there just have not been any updates or is something wrong?

contents of sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

## PLF Free
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free

## PLF Non-free
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy non-free

Thanks!

hjm

---

### Post by pheitman on 2005-11-28
You may want to check out the [Backports forum]("http://www.ubuntuforums.org/forumdisplay.php?f=47"). It describes the Ubuntu philosophy about updates and provides a mechanism to get updates that will be available in Dapper.

peter

---

### Post by ecobuntu on 2005-11-28
[QUOTE=hjm]I've seen queries like this posted before but have not seen satisfactory replies. Using what I believe to be satisfactory sources (sources.list entries below), I haven't seen any updates for the Breezy for several weeks.  With most other Debian distro's, there are usually multiple updates every day.  This wouldn't bother me much (the more updates, the more complexity, the more breakage, and Breezy has been the most stable, best working distro for my laptop that I've ever tried - 13 days of uptime on my lappie, with multiple sleeps every day!), but it concerns me as my konqueror has broken (and FF shows similar misbehavior, indicating some sort of shared code problem - will post details later) and I also haven't seen any security updates.

I know Linux is secure, but this lack of updates has now gotten me a bit concerned.

Is it that there just have not been any updates or is something wrong?

contents of sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

## PLF Free
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free

## PLF Non-free
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy non-free

Thanks!

hjm[/QUOTE]


Also if you found a BUG you need TO REPORT IT...otherwise the developers can't fix it if it's new and they don't know about it.

---

### Post by Kyral on 2005-11-28
Yes, post the Bug to Launchpad

[www.launchpad.net](www.launchpad.net)

---

### Post by jaa1180 on 2005-11-28
See if adding these repositores help...
[http://users.piuha.net/martti/comp/ubuntu/install.html#3](http://users.piuha.net/martti/comp/ubuntu/install.html#3)
Then...
```

#apt-get update

```

See what you get.
Post the results.

---

### Post by hjm on 2005-11-28
Thanks for all the responses; the short answer is that my sources.list has backups for every possible repository, but in terms of finding valid updates, nothing more than when I started.

So I guess the answer is actually that there are no upgrades that might solve this short of trying out the new KDE release, but I think I'll wait for that to settle a bit.

I did try to submit a bug via the ubuntu bugzilla but managed to give it nausea.  So reports of both bugs  been emailed to the admin.

Another machine running the MEPIS distro with KDE 3.4.2 does not have this behavior.

Thanks again for the help.
hjm

---

### Post by littlepr on 2005-11-28
HJM,

If we are talking about security updates then you should be up-to-date. If you mean any update for any app then you might have the latest for now with the default repos. If you set the non-default then you should have received some update notifications. I just had the kernel update notification for kernel version 2.6.12-10-386. I was previously running 2.6.12-9-386. I have received a few others too. By the way, my original install was a fresh load of Ubuntu 5.04 which I then immediately upgraded to Ubuntu 5.10. This was done about three/four weeks ago.

---

