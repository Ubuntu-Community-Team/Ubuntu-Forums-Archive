---
title: "Ubuntu Update - Hash Sum mismatch"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by davit on 2009-07-02
I'm trying to update Jaunty and Hardy on 2 separate machines on the same network but have similar problems with apt-get update and source.list on each machine.

One error is ```
..
..
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.10.0-19ubuntu1.1_all.deb  Hash Sum mismatch
..

```

I tried the following a number of times #(as root);
```

apt-get update -o Acquire::http::No-Cache=True
apt-get update -o Acquire::BrokenProxy=true
apt-get upgrade --fix-missing
aptitude autoclean | aptitude clean
apt autoclean | apt clean
..

```

and this does not have any effect. Any other ideas?  Thanks

---

### Post by davit on 2009-07-03
bump.

would there be an issue with repositories overloading?

---

### Post by LinkedITS on 2009-12-16
I had the same exact problem. I tried Ubuntu, Mint 7, Mint 8 and every single time I would get the Hash Sum Mismatch Error when I try to install anything. Because I spent so much time searching for the answer to my problem, I am going to try to post this anywhere I see someone having problems with Hash Sum Mismatch.

But after seeing breaker's post (he mentions the problem might be with bad RAM), I realize it could be a problem with my RAM because I remember that my machine used to have Windows 7 OS on it and it failed to install anything because it kept getting corrupt files error. Originally I thought the problem was because my computer was unable to support Windows 7. But one of the symptoms of bad RAM is having corrupt files and bad disk. Another symptom is having distorted graphics on the web pages which i notice was another problem I had. 

Our office had ordered a couple of the same computer, so I did a test and installed Mint 8 on a computer of the same model. I was able to install everything I wanted on the new computer without any of the Hash Sum Mismatch errors.

So that led me to conclude that I kept getting the Hash Sum Mismatch errors because i had a bad RAM. (OR at the very least it is a hardware problem isolated to that specific computer). I am going to change the memory in my problematic computer and see if that fixes the problem. I'll post an update within the week with the results.

---

### Post by LinkedITS on 2009-12-16
As I mentioned in a earlier post, the Hash Sum Mismatch might be caused by bad RAM so i devised a experiment to test out my Hypothesis. In the "experiment" that I performed, I took the RAM out of the "Good Machine" and put it into the "Bad Machine." Then I booted into the "Bad Machine with the Good RAM" and tried to install the ntp package. However the installation failed with Hash Sum Mismatch once again. 

Then I put the "Bad RAM" into the "Good Machine" and booted into it. The "Good Machine with the Bad RAM" was able to install properly without any problems at all.

This leads me to the conclusion that the problem is NOT the RAM. I hypothesize that the problem, although not with the RAM, is still related with the memory in some way. I will continue to look into this and post any updates I have.

---

### Post by LinkedITS on 2010-02-05
After extensive memory tests on the machine which turned up showing there was nothing wrong with the memory, we found that it was a issue with the system board.

---

### Post by immesys on 2011-05-04
Bumping for irony.

I am getting the following error updating packages on both my Maverick pc and my Natty Beta2 pc:

Maverick:
```

Failed to fetch http://za.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.10.1-12ubuntu2.1_all.deb  Hash Sum mismatch

```

Natty:
```

Failed to fetch http://ls.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.10.1-17ubuntu4.1_all.deb Hash Sum mismatch

```

So two different versions of ubuntu, two different repositories, two different PC's... and they both have hash sum mismatches on a perl package? Any ideas?

---

### Post by jsg24 on 2011-05-06
Another bump for this thread.

I'm still running Ubuntu 10.10 . Haven't upgraded to 11.04 yet.

Use a Samsung NC10.

I also have a problem with Perl Modules. Everything else upgrades fine except for:
libperl5.10
perl
perl-base
perl-modules

I use a South African repository. But I still get the error:
> Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/pool/main/p/perl/perl-modules_5.10.1-12ubuntu2.1_all.deb](http://ubuntu.mirror.ac.za/ubuntu-archive/pool/main/p/perl/perl-modules_5.10.1-12ubuntu2.1_all.deb)  Hash Sum mismatch

I've tried using the UK repositories with same results.
I've tried downloading the actual deb files and running Software Centre on them. Same results.

Maybe upgrading will fix this?
Is someone else running 11.04 and still having this issue?

Thanks in advance.

---

### Post by garth.d on 2011-05-07
Just thought I'd post my problem, as I've had some great help in the past.  Thanks guys.  

Anyway....

Seems I'm not the only one having problems with the Perl updates...

All updates install just fine after a fresh install of 11.04 64bit, except for the following:

> Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.10.1-17ubuntu4.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.10.1-17ubuntu4.1_all.deb)  Hash Sum mismatch

> E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Now I've tried changing servers (tried like a 100 different ones, YES I DID...),  cleaning out apt & running sudo apt-get update && sudo apt-get upgrade on each like a zillion times today - same error, nothing seems to work.  Even re-downloaded the vanilla Ubuntu 11.04 + the Xubuntu 11.04 ISO's thinking I had bad images, but seems they're not, as BOTH yet again came up with the same error on the same package above.

PS:  I get no errors running sudo apt-get update at all on any server (only when upgrading)... also, I tried installing Flash the other day - same error, this time with the "ia32-libs" package that failed (mismatch again..)

Hoping someone can help in figuring out these hash mismatches - they're driving me nuts!

Kind regards.  (sorry for the lengthy post - I type too much..:))

---

### Post by DewaldB on 2011-05-09
I've got the same problem on both my work (10.10) and home (11.04) computers.

> Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.10.1-12ubuntu2.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.10.1-12ubuntu2.1_all.deb) Hash Sum mismatch

Tried various things, switched sources, cleared cache, etc. but no luck.
Must be something wrong with the actual deb released for this Perl update?

---

### Post by Graviti on 2011-05-09
I had the same problem here. After much mucking about trying to clear caches etc in my machines, I came to the conclusion, that the problem lay out there somewhere. As it was not appearing in the Launchpad Bug Reporting system, I guessed it didn't lie at the very end but somewhere in between. After much research, and people suggesting that resetting their modem was the answer, I tried it. It didn't work. So I contacted my ISP and got through to a super helpful technical bloke, who told me that the ISP has a transparent caching proxy. He then proceeded to flush the proxy of this file, and I was able to download it fine. I realised this, when I was able to download the file onto a different machine with a different ISP, and the two files had different hash values. So a quick phone call (I was lucky) got it sorted out for me, and anyone on my ISP.

My suggestion would be, reset your modem first. (Power out, Power in). If this doesn't work, phone your ISP and tell them to clear the file out of their Proxy Cache. I'm guessing enough people use Ubuntu to keep the same dud file in the cache for a really long time.

---

### Post by yuval.dagan on 2011-07-20
Yeah - I just selected other wireless network and its done

thx

---

