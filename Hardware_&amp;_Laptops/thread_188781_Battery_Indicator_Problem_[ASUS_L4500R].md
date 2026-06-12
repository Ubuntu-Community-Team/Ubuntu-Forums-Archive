---
title: "Battery Indicator Problem [ASUS L4500R]"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by kwicky21 on 2006-06-04
Hi,

Ever since I started using Ubuntu on my laptop, Hoary Hedgehog, until today, Dapper Drake Flight 7, it still hasn't detected my battery! Whenever I try to enable the battery indicator, it will say "System is running on AC power. no battery present", even if it IS running on Batteries and NOT on AC power. Now I know that this isn't a problem with my battery because I recently tried installing Fedora Core 5 and it was able to detect my battery properly without having to do anything special, just installed it. It even dims the brightness of my monitor everytime I unplug the laptop from the AC power supply.

I've already tried doing the steps mentioned in the wiki[1], and tried to look for solutions here in the Ubuntu Forum[2], but to no avail.

Can anybody please help me with this problem?

I'm on an ASUS L4500R Laptop[3] and am running Ubuntu Dapper Drake LTS.

Any help would greatly be appreciated.
Thanks!

[1] [https://wiki.ubuntu.com/ACPIBattery](https://wiki.ubuntu.com/ACPIBattery)
[2] [http://www.ubuntuforums.org](http://www.ubuntuforums.org)
[3] [http://tuxmobil.org/asus_l4500r.html](http://tuxmobil.org/asus_l4500r.html)

---

### Post by ccolon on 2006-06-14
I am having exactly the same problem. Unfortunately I don't have a solution either. There is a bug report regarding this here:-

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/24153](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/24153)

However it looks like no one has fixed this yet for ubuntu.

David

---

### Post by msak007 on 2006-06-25
My sister's laptop has this problem. When I first installed Kubutu (Dapper) on her machine, the battery was detected and worked great. However after about a week, the laptop no longer detects the battery. It first started by saying it was charging but the % wouldn't change. At first I thought the battery may have gone bad. I removed the battery, restarted, and put it back in, and now it says it's not detected even if it IS running off battery. I can't test in another distro or Windows, I might just reformat it to get it working again.

EDIT: Laptop is a Compaq Evo n160

---

