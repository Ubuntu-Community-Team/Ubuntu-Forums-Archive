---
title: "Replacement Battery for Sony Vaio Model-3H1L"
date: 2015-01-14
forum: Hardware
---

### Post by gee_man on 2015-01-14
I have a Sony Vaio laptop - Model PCG-3H1L with a battery that is no longer holding a charge well.   I have checked prices for replacement batteres with the same specs and find that I can by one from a third party manufacturer for much less.  But most say that using a third party manufactured battery requires system changes in order for the battery to work as intended.  Information varies with manufacturer about use - some say that a BIOS update is required, others purport to solve this problem with software solutions or by removing some startup files.  All of these assume that the laptop is still using windows.   I am using lxle 14.04 and want to know if anyone has experience with using a third party battery replacement.  Do the same requirements as above apply or does it "just work?" My reasoning is that if removing windows startup files works, then using one with a system not using windows, should work.
Thanks for input.

---

### Post by tgalati4 on 2015-01-14
If you click on the battery icon with the original battery, you will see a bunch of statistics:  designed capacity, actual capacity, current voltage, discharge rate, etc.  It's possible that an aftermarket battery will not show as much information because the BIOS expects an original battery.  This should not impact the use of the battery, just less information. 

On my T43p Thinkpad, the WindowsXP driver can detect how many charge-recharge cycles (around 300 on this old battery--which is about all you get), but I can't detect the number of cycles within linux.  So yes, the linux module (probably related to ACPI) can't get as much information as the proprietary Windows driver.  It doesn't affect the operation of the battery.  Knowing how many cycles is helpful for predicting remaining life of the battery, but when the battery dies suddenly, then it's due for a change--regardless of what the information says.

Original batteries tend to have better quality control then a no-name battery.

---

### Post by gee_man on 2015-01-14
Thank you tgalati4.  This is exactly the sort of info I was seeking.  Most of the  various  stats aren't very useful for the way I use my laptop.   About the only thing that I use regularly is remaining charge/time left so not having them isn't  a big deal to me.   Do you find that the remaining charge/time left info is reasonably accurate for your laptop under ubuntu?

---

### Post by gee_man on 2015-02-01
I purchased a 3rd party replacement battery (Tech Rover brand) that  advertized that no BIOS update was required and it works as stated. So I do not know the answer to my original question, but I now know that it is possible to buy a replacement that requires no BIOS update.  Battery seems to discharge more quickly than Sony documentation states the original should - a charge lasts about 2 hours (depending on what I'm doing) instead of 3 as Sony states.  I bought the laptop used and so don't really know whether the original gave the stated service.  Either way, I'm happy.

---

