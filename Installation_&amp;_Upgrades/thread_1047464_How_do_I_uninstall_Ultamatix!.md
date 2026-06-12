---
title: "How do I uninstall Ultamatix?!"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by TheBiles on 2009-01-22
It keeps giving me an error, I was going to get rid of it, but it doesn't show up in my Add/Remove Programs list, and running the .deb again only gives me the option to reinstall.

---

### Post by taurus on 2009-01-22
If you installed it with dpkg (.deb), you can remove it with dpkg also.

```
sudo dpkg -r package_name
```

---

### Post by jeriggs on 2009-01-27
I removed Ultamatix by opening terminal and executing the following command:

sudo apt-get remove ultamatix


Also, don't forget to remove the repositories that Ultamatix inserted in your sources list:

sudo gedit /etc/apt/sources.list

Delete starting at #ULTAMATIX REPOS START, all the way down to #ULTAMATIX REPOS END

You'll want to open terminal again and update your sources:

sudo apt-get update

---

### Post by spike_naples on 2009-03-31
Thanks for the info. I'm using Ultamatix but so far have no intention (yet) to uninstall it as it seems to be stable and very helpful in installing games for me.

I'll keep this post in mind though for any future reference.

---

### Post by oldos2er on 2009-03-31
Just be aware it can break your system. See [http://mjg59.livejournal.com/99905.html](http://mjg59.livejournal.com/99905.html)

---

### Post by spike_naples on 2009-03-31
> **oldos2er said:**
> Just be aware it can break your system. See [http://mjg59.livejournal.com/99905.html](http://mjg59.livejournal.com/99905.html)

Thanks, I'm being careful with it.

---

### Post by spike_naples on 2009-04-01
After a day of tinkering with Ultamatix, I, as a very novice user found that it could indeed be dangerous. 

I'm not saying that it's a bad program altogether but tinkering too much may lead to an unstable system. 

Yes I was careful but in my tinkering I have also learned that it isn't all that needed. 

I removed it...

Will just try to learn Synaptic Package Manager instead and read more of the forum posts for more knowledge.

I would recommend Ultamatix for the installation of some of the games listed in it though but still BE WARNED.

---

