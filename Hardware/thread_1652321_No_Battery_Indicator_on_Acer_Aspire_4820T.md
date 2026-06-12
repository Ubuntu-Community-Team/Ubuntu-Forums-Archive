---
title: "No Battery Indicator on Acer Aspire 4820T"
date: 2010-12-24
forum: Hardware
---

### Post by jezzipin on 2010-12-24
Hi all,

My first post here so please go easy on me. After several experiments with Linux in the past I've finally decided to switch over from 'the other side' with the release of Ubuntu 10.10. The problem is, I have no battery indicator.

It will show when the battery is low but will give no indication of the level of power left in the battery. Even screenlet apps don't display the battery life. 

I've tried running acpi in the terminal and get the following:

"Battery 0: Unknown, 0%, rate information unavailable".

which suggests to me that the battery isn't being picked up at all. Has anyone found a fix for this as I really can't work not knowing when my battery is going to cut out. I lost some important documents the other day because of this and I'm seriously considering going back to Windows 7. Please help. I'm running an Acer Aspire 4820T on Ubuntu 10.10 Maverick Meerkat.

---

### Post by Tamrac on 2010-12-25
> **jezzipin said:**
> Hi all,

My first post here so please go easy on me. After several experiments with Linux in the past I've finally decided to switch over from 'the other side' with the release of Ubuntu 10.10. The problem is, I have no battery indicator.

It will show when the battery is low but will give no indication of the level of power left in the battery. Even screenlet apps don't display the battery life. 

I've tried running acpi in the terminal and get the following:

"Battery 0: Unknown, 0%, rate information unavailable".

which suggests to me that the battery isn't being picked up at all. Has anyone found a fix for this as I really can't work not knowing when my battery is going to cut out. I lost some important documents the other day because of this and I'm seriously considering going back to Windows 7. Please help. I'm running an Acer Aspire 4820T on Ubuntu 10.10 Maverick Meerkat.

I have the 3810T, which is more or less the same laptop. The only difference is the built in DVD and yours is 14in instead of 13in LCD.... 10.10 it should detect the battery. Have you updated everything to latest versions? After a few weeks of install, I noticed a number of updates by the update manager already.

---

### Post by jezzipin on 2010-12-25
> **Tamrac said:**
> I have the 3810T, which is more or less the same laptop. The only difference is the built in DVD and yours is 14in instead of 13in LCD.... 10.10 it should detect the battery. Have you updated everything to latest versions? After a few weeks of install, I noticed a number of updates by the update manager already.

Everything has been updated fully using the update manager. No matter what I try it still will not indicate the level of battery. I thought that with this build I would see some improvements in Ubuntu and it has come a long way but with setbacks like this I am beginning to understand why people stick with Windows. If the acpi is not detecting the battery then the destop indicator of screenlets won't be able to so it must be something wrong with this.

---

### Post by jezzipin on 2011-01-12
After much digging and time spent messing with different configurations, I've found the solution. My machine was running an older version of the BIOS so I did several upgrades to upgrade it to the the latest. (1.22 I think)

After the upgrade, my battery was detected and gives charge level and run-down time. I haven't yet tested it on a full charge to see if I can get the full 8 hours out of it however at least now I will have some warning so that I can save my work before Ubuntu just cuts out.

I'm so happy that I've found this fix that I've completely removed my Windows partion and I'm now running Ubuntu 10.10 only.

---

