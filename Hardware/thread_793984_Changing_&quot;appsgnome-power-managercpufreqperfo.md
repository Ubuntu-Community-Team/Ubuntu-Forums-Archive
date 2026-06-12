---
title: "Changing &quot;/apps/gnome-power-manager/cpufreq/performance_ac&quot; key"
date: 2008-05-14
forum: Hardware
---

### Post by Limulf on 2008-05-14
Hello. Looking around a bit Gnome's configuration, first with "Ubuntu Tweak" and later with "gconf-editor", I have found this key: "/apps/gnome-power-manager/cpufreq/performance_ac". If I set its value to 100 instead of the default of 85, would I notice any performance increase? Is it a dangerous change?
 Thanks a lot for your time and work.

---

### Post by Mr. Picklesworth on 2008-06-03
I have come across this, too. Anyone know? Can someone with a desktop computer please say what that key is?

I suspect that this is set to 85 for laptops to avoid generating excess heat, but I do not really know.

One thing you can do is change the key /apps/gnome-power-manager/ui/cpufreq_show to get some helpful data on that stuff in the power management preferencs :)

A little bit of stuff later on in this mailing list discussion:
[http://www.nabble.com/New-preferences-UI-to7881309.html#a7881309](http://www.nabble.com/New-preferences-UI-to7881309.html#a7881309)

Edit:
Here, [for example](http://www.nabble.com/New-preferences-UI-to7881309.html#a7954284). Regrettably this isn't a great place to look for "what to do best", but there is very little information elsewhere!

---

### Post by Thingymebob on 2008-09-24
My understanding of this is that it sets the cpu frequency up scaling threshold of the ondemand governor,

So if you set to 100 your cpu will never scale down, Setting this correctly is most useful for laptops to conserve battery life however it is also useful for servers and desktops etc where power consumption needs to be kept in check I have mine set to around 35 which means the cpu will not up-scale untill it is under about 85% load at the lower frequency. With modern cpu switching speeds, setting this quite low should not really effect performance as the cpu will scale up very quickly when needed.

the [ondemand white paper]("http://www.kernel.org/pub/linux/kernel/people/lenb/acpi/doc/OLS2006-ondemand-paper.pdf") and [http://www.lesswatts.org]("http://www.lesswatts.org") are both good reading

---

