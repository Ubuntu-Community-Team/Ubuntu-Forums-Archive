---
title: "BETA TESTERS WANTED - Superdeb installer"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by hammer v2 on 2009-02-02
Hi guys,
I've created a way to install deb files in any ubuntu 8.10 based distro windows-style without the internet. I've called it superdeb. I'm about to unleash it onto the world but first I wanna be sure it's working correctly.

I've bundled pingus (a lemmings-type game) into a superdeb. You can download it from here;

[http://superdeb.googlecode.com/files/pingus0-7-2-UB0810.sdeb]("http://superdeb.googlecode.com/files/pingus0-7-2-UB0810.sdeb")

Would you guys be so kind as to try and install it for me? just download the file, double-click on it and follow the prompts. It's not pretty but seems to be working ok over here.

Please let me know how you guys go! Give me as much feedback as you want. 

Hope you're all well.
H.

---

### Post by hammer v2 on 2009-02-03
bump! :)

---

### Post by EXCiD3 on 2009-02-03
Works great for me, but wait you already know that! ;)

---

### Post by jenkinbr on 2009-02-03
If I get time, I will do this on a test machine later this week.

Really not in the mood to accidentally break my offline install that's running so smoothly. *cringes at the though of system breakage*

seriously, I will try this though.

---

### Post by hammer v2 on 2009-02-03
> **jenkinbr said:**
> If I get time, I will do this on a test machine later this week.

Really not in the mood to accidentally break my offline install that's running so smoothly. *cringes at the though of system breakage*

seriously, I will try this though.

Great! Thanks man! It shouldn't break anything hey. Superdeb doesn't re-invent the wheel. It is simply a .deb file and all of it's dependancies all bundled together with a metapackage. Everything is installed via gdebi (apt-get) and can be removed with synaptic. 

Can't wait to hear how you go.

H.

---

### Post by jenkinbr on 2009-02-04
The test package seemed to install fine.

Quick question:  When a user actually wants to download software using the superdeb tool, will there be a process similar to NoNetDebs, where your /var/lib/dpkg/status file needs to be uploaded so the system state can be scanned?

---

### Post by hammer v2 on 2009-02-04
> **jenkinbr said:**
> 
Quick question:  When a user actually wants to download software using the superdeb tool, will there be a process similar to NoNetDebs, where your /var/lib/dpkg/status file needs to be uploaded so the system state can be scanned?

nope. Sdebs use a pre-made /var/lib/dpkg/status file. I did this so sdeb files will install on any ubuntu with an Xserver. That pingus file should install on xubuntu, ubuntu, edubuntu and kubuntu no problems at all.

---

### Post by hammer v2 on 2009-02-04
> **jenkinbr said:**
> The test package seemed to install fine.



BIG thanks for trying out out jenkinbr! Any feedback? was it easy enough? Could your grandma install it?

---

### Post by hammer v2 on 2009-02-06
Here's something a bit more useful. A superdeb for Ubuntu-restricted-extras!

[http://www.zshare.net/download/551500648bbc0c4c/](http://www.zshare.net/download/551500648bbc0c4c/)

---

### Post by jenkinbr on 2009-02-06
> **hammer v2 said:**
> Here's something a bit more useful. A superdeb for Ubuntu-restricted-extras!

[http://www.zshare.net/download/551500648bbc0c4c/](http://www.zshare.net/download/551500648bbc0c4c/)
That I am skeptical of.

The ubuntu-restricted-extras package includes several other packages that need to make further downloads (msttcorefonts, flashplugin-nonfree, etc.)  Then, there is the issue of licensing.

See: [http://ubuntuforums.org/showthread.php?t=630696](http://ubuntuforums.org/showthread.php?t=630696)

---

### Post by jenkinbr on 2009-02-06
> **hammer v2 said:**
> BIG thanks for trying out out jenkinbr! Any feedback? was it easy enough? Could your grandma install it?
Install went fine, even with /etc/apt/sources.list pointing to /home/jenkinbr/setup/repo/ubuntu (I have indexes stored there, but no packages)

---

