---
title: "Outdated GIMP in repository?"
date: 2008-10-20
forum: General Help
---

### Post by Gnu32 on 2008-10-20
Greetings,
I was wondering why in the repository the GIMP version that is provided is 2.4.6, when version 2.6 has been out for quite a while now?

I have all repositories enabled in Synaptic and the latest reported version is "2.4.6-1ubuntu1~hardy (hardy-backports)".

Does this mean all the extra stuff like the plugin packages are outdated? :s

Cheers.

---

### Post by snowpine on 2008-10-20
> **Gnu32 said:**
> Greetings,
I was wondering why in the repository the GIMP version that is provided is 2.4.6, when version 2.6 has been out for quite a while now?

I have all repositories enabled in Synaptic and the latest reported version is "2.4.6-1ubuntu1~hardy (hardy-backports)".

Does this mean all the extra stuff like the plugin packages are outdated? :s

Cheers.

Hi there, Hardy has Gimp 2.4, but 8.10 Intrepid has Gimp 2.6. If you don't want to upgrade to Intrepid, you should be able to download and install the new version into Hardy from the Gimp website: [http://www.gimp.org](http://www.gimp.org)

Good luck!

---

### Post by Gnu32 on 2008-10-20
Cheers! :wink:

IMHO the guys really should update Hardy's version, but I guess with Ibex in 10 days there isn't much point.

---

### Post by snowpine on 2008-10-20
> **Gnu32 said:**
> Cheers! :wink:

IMHO the guys really should update Hardy's version, but I guess with Ibex in 10 days there isn't much point.

That is not how the Ubuntu repositories work. Everyone who uses the same release (Gutsy, Hardy, Intrepid, etc.) has the same versions of packages (the exception being minor upgrades to fix serious bugs or security flaws). 

You can install newer package versions from source (download from the Gimp site, for example) or using backports: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by ajgreeny on 2008-10-20
You can also get the gimp .debs (there are six needed if you include dependencies) which work well from [getdeb]("http://www.getdeb.net/").  They certainly work without fault as far as I can see, having already installed them.

---

