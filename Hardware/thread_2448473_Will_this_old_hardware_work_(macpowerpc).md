---
title: "Will this old hardware work (mac/powerpc)"
date: 2020-08-08
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2020-08-08
Nigher asked me to look at this thing, he thinks it just needs more ram (while this is true, there is a bigger issue)
this hardware is so far EOL that software support ended ages ago
[it has 1.5GB of DDR2 ram and a 2.1Ghz powerpc CPU](https://everymac.com/systems/apple/imac/specs/imac_g5_2.1_20.html)
Even if i can boot a light weight linux distro on this will it even be able to play a video youtube without studdering?

---

### Post by Yellow Pasque on 2020-08-09
I don't think I'd use Lubuntu for a PowerPC. LxQT is heavier than lxde, and Ubuntu doesn't officially support PPC from what I can tell.
I'd try Debian: [https://cdimage.debian.org/cdimage/weekly-builds/ppc64el/iso-cd/](https://cdimage.debian.org/cdimage/weekly-builds/ppc64el/iso-cd/)

> will it even be able to play a video youtube without studdering?
It's hard to say without having experience with that specific hardware.

---

### Post by pqwoerituytrueiwoq on 2020-08-09
i burned it to my last black cd, but the thing will not show the disk in the boot menu (only thing that shows up is the internal hdd when i hold the alt key) with either the internal nor my external cd/dvd drive
burned the disk image with brasero on the lowest speed
edit:
i can't get debian ppc64el to boot the cd
i was able to boot lubuntu-16.04-alternate-powerpc.iso ([found here](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/))
i was able to get it to play youtube using vlc -> media -> open location from clipboard
* web browsers are way out of date on this version on lubuntu (firefox stopped at 47and midori stopped at 0.5.[something])
looks like nothing this is still maintained supports this museum piece

---

