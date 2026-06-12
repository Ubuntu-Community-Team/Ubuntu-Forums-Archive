---
title: "Breezy Won't Install on Omnibook"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by ierdha on 2005-12-13
Hi,
I am tring to install breezy on a Omnibook vt6200 512mb. ram, 1,5Ghz P4 processor. I got the cd from [http://shipit.ubuntulinux.org/](http://shipit.ubuntulinux.org/), 
I then stuck it in my computer and tried to install. But in the middle of the process, it stop with an error message. i forgot the message but it seems like the kernel having a problems with my omni. 

after i got this message, i choose to continue, but the next instalation process always failed.

i need some suggestion, currently i'm using hoary.I've read the doc in ubuntuguide, there's possibility to upgrade to breezy using apt. 
does anyone try it?

Thanks for any help!

NFM

---

### Post by aysiu on 2005-12-13
[QUOTE=ierdha]
i need some suggestion, currently i'm using hoary.I've read the doc in ubuntuguide, there's possibility to upgrade to breezy using apt. 
does anyone try it?[/QUOTE] First of all, can I ask why you want Breezy if you have Hoary? I upgraded to Breezy simply out of curiosity, but I didn't see anything special about it, and I remember Hoary being rock-solid--it also is supported for 18 months after its initial release.

In any case, a lot of people have upgrade using apt, and I'd say the success rate is about 50%. If you decide to do it, follow the Breezy instructions in the first link of my sig, then ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

