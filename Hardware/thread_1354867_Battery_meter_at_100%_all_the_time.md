---
title: "Battery meter at 100% all the time"
date: 2009-12-14
forum: Hardware
---

### Post by Synoc on 2009-12-14
I have a Dell inspiron 1150. when I was running Ubuntu off the live CD, it told me the battery level fairly accurately. now that I've taken the plunge and installed it, it stays at 100%. now I did some research, and someone put forth the idea that if it works off the CD but not off the hard drive, it's a BOIS problem or a hardware problem not the fault of the OS. I'll accept this, if indeed it's the case, but how do I fix this problem? as it was working under windows, should it not also work under Ubuntu? 

need advice, please and thank you.

---

### Post by lidex on 2009-12-14
There appears to be a bug in gnome-power-manager in Karmic. You could go into synaptic and search "laptop" to see avaliable packages for replacing. For instance: ibam
> IBAM is an advanced battery monitor for laptops, which uses statistical and
adaptive linear methods to provide accurate estimations of minutes of
battery left or of the time needed until full recharge. It requires APM, ACPI
or PMU.


You might also try enabling Karmic-Backports in Updates section of Software Sources.

---

### Post by Synoc on 2009-12-14
> **lidex said:**
> There appears to be a bug in gnome-power-manager in Karmic. You could go into synaptic and search "laptop" to see avaliable packages for replacing. For instance: ibam


You might also try enabling Karmic-Backports in Updates section of Software Sources.

ok, I installed it, but I don't see it in my system>admin or prefs, or my apps. so how do I use it or does it automatically take over for gnome's?

---

### Post by lidex on 2009-12-14
Never used it; referred to it as an example. It's up to you to decide what is appropriate from the available options. 

Apparently this is a command line program -- no gui, so probably not what you're looking for.

[Info]("http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce-Dmitri-s-open-source-blend-of-productive-computing/Monitoring-Notebook-Battery-with-IBAM?blogbox")

---

### Post by Synoc on 2009-12-14
> **lidex said:**
> Never used it; referred to it as an example. It's up to you to decide what is appropriate from the available options. 

Apparently this is a command line program -- no gui, so probably not what you're looking for.

[Info]("http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce-Dmitri-s-open-source-blend-of-productive-computing/Monitoring-Notebook-Battery-with-IBAM?blogbox")
I am lookin for a GUI one, if one is available

---

