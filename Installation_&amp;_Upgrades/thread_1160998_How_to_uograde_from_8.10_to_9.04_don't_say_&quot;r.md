---
title: "How to uograde from 8.10 to 9.04? don't say &quot;read Upgrading to Ubuntu 9.04&quot;"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by Big_Lebowski_2009 on 2009-05-16
Hi all, wanna upgrade from 8.10 to 9.04, downloaded Alternate CD/DVD
(ubuntu-9.04-alternate-i386.iso) but when I'm trying to upgrade, it takes to download some files (about 300Mb) else,
Of course, I read "Upgrading to Ubuntu 9.04" article ([http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)) it says nothing...
Why should I download 300Mb else if I already downloaded Alternate CD?
What I do wrong?

Thanks all in advance.

---

### Post by Brandon Williams on 2009-05-16
If you did not install any additional software in 8.10 and therefore only have software on the box that was on the 8.10 installation CD, then you will most likely not have to download anything when you upgrade using the 9.04 alternate install CD. I only say "most likely" because ... welll ... I have never (and most likely will never) left an Ubuntu install with just the software that was initially installed, so I don't have any experience to confirm my expectation.

On the other hand, if like most people you have installed a whole bunch of other stuff after the fact (video codecs, dev tools, games), then there will be a whole bunch of updates that have to be fetched from the net when you upgrade to Jaunty.

---

### Post by Big_Lebowski_2009 on 2009-05-16
> **Brandon Williams said:**
> If you did not install any additional software in 8.10 and therefore only have software on the box that was on the 8.10 installation CD, then you will most likely not have to download anything when you upgrade using the 9.04 alternate install CD. I only say "most likely" because ... welll ... I have never (and most likely will never) left an Ubuntu install with just the software that was initially installed, so I don't have any experience to confirm my expectation.

On the other hand, if like most people you have installed a whole bunch of other stuff after the fact (video codecs, dev tools, games), then there will be a whole bunch of updates that have to be fetched from the net when you upgrade to Jaunty.

Thank you Brandon Williams,

But I'm afraid I installed a lof of "additional software in 8.10" :) it seems to me I will have to install 9.04 after removement 8.10, don't want to go this way, but don't see another solution :(

---

### Post by ales on 2009-05-16
> **Big_Lebowski_2009 said:**
> Thank you Brandon Williams,

But I'm afraid I installed a lof of "additional software in 8.10" :) it seems to me I will have to install 9.04 after removement 8.10, don't want to go this way, but don't see another solution :(


Why don't u upgrade directly from 8.10?

---

### Post by Big_Lebowski_2009 on 2009-05-16
> **ales said:**
> Why don't u upgrade directly from 8.10?

Of course, I'm upgrading directly from 8.10, as I pointed above, I downloaded Alternate CD/DVD, and trying to upgrade  from it, as well I downloaded Ubuntu CD (not Alternate CD), but the first CD takes to download some files else.... the second one, doesn't upgrade upon old Operating System (8.10)... it's very, very difficult to solve such trivial - as I thought before - task....

---

### Post by ales on 2009-05-16
> **Big_Lebowski_2009 said:**
> Of course, I'm upgrading directly from 8.10, as I pointed above, I downloaded Alternate CD/DVD, and trying to upgrade  from it, as well I downloaded Ubuntu CD (not Alternate CD), but the first CD takes to download some files else.... the second one, doesn't upgrade upon old Operating System (8.10)... it's very, very difficult to solve such trivial - as I thought before - task....

I still don't understand you. I just pushed button upgrade to 9.04 and nothing went wrong. All my installed apps are as they were in 8.10. Why do you download CD. Why don't you use upgrade in Update Manager

---

### Post by Big_Lebowski_2009 on 2009-05-16
> **ales said:**
> I still don't understand you. I just pushed button upgrade to 9.04 and nothing went wrong. All my installed apps are as they were in 8.10. Why do you download CD. Why don't you use upgrade in Update Manager

))) heh why should I use upgrade in Update Manager, if I got Alternate CD/DVD and Ubuntu CD ?? :))) with my internet connection, I will upgrade in Update Manager during 2 days :))

---

### Post by Topsiho on 2009-05-16
You are trying to do two things at one time, just like doing a waltz and the limbo rock at the same time, which doesn't work (I am told).

1. You can upgrade by pushing the upgrade button, and sit back. The computer downloads a lot of new things for the new version of Ubuntu you are upgrading to. In my case this amounts to downloads of around 1200 MiB, which is the amount of nearly two CD's, takes ages, and after that comes the install proper, and throwing out the obsolete old stuff.

2. You can download a CD image with the new version, check the MD5sum, burn it, check this again and use it to do a clean install. If you have a separate /home partition and are careful (manually) to not format that partition, your data and setups of your applications will still be there, just as in a direct upgrade as described in 1.

So ... :)

***Please don't forget to first back up your valuable data.***

Topsiho

---

### Post by Big_Lebowski_2009 on 2009-05-16
> **Topsiho said:**
> You are trying to do two things at one time, just like doing a waltz and the limbo rock at the same time, which doesn't work (I am told).

1. You can upgrade by pushing the upgrade button, and sit back. The computer downloads a lot of new things for the new version of Ubuntu you are upgrading to. In my case this amounts to downloads of around 1200 MiB, which is the amount of nearly two CD's, takes ages, and after that comes the install proper, and throwing out the obsolete old stuff.

2. You can download a CD image with the new version, check the MD5sum, burn it, check this again and use it to do a clean install. If you have a separate /home partition and are careful (manually) to not format that partition, your data and setups of your applications will still be there, just as in a direct upgrade as described in 1.

So ... :)

***Please don't forget to first back up your valuable data.***

Topsiho

Hello Topsiho, 
Of course I downloaded CD image with the new version, burn it, but I don't want to lost my old files,  to copy ones I need else HDD or many DVD-discs.... so I'd like to upgrade instead of clean install.... Upgrading is normal mode as I read in UBUNTU web-site..... But if upgrade keep goes wrong, I will have to clean install probably...

---

### Post by poldie on 2009-05-21
> **Big_Lebowski_2009 said:**
> ))) heh why should I use upgrade in Update Manager, if I got Alternate CD/DVD and Ubuntu CD ?? :))) 

Because it will work.  Why do you want to try and get some CD working when you can just press a button marked 'upgrade'?   Why did you get the CD in the first place?

---

