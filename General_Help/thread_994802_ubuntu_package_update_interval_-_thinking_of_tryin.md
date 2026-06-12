---
title: "ubuntu package update interval - thinking of trying it from debian lenny"
date: 2008-11-27
forum: General Help
---

### Post by graysky on 2008-11-27
Currently been using debian lenny for a few weeks and noticed that iceweasel (debian-branded firefox) is still 3.0.3 despite the 3.0.4 release of the office firefox.  As I understand it, updates on packages for debian aren't that rapid.

I'm thinking about resizing a partition and adding a 12 gig spot to try out intrepid ibex (amd64).  **How rapidly do ubuntu repos get updated with new versions of packages?**

---

### Post by Xiong Chiamiov on 2008-11-27
Lenny is updated every so-often, while Sid is updated as frequently as new versions release (beta or otherwise), and Etch only has things that were released a few years ago.  When the next version comes out, they'll all rotate towards more stability, with Lenny being stable, Etch being gone, and Sid always being unstable.

Ubuntu has a new release every 6 months.  Other than that, most packages don't get updated (the idea being that everything works, so it shouldn't be touched).  High-visibility packages like Firefox get updated fairly often, although I can't say how much lag there is between new releases and it working its way into the repository.  Currently, [the firefox package in Intrepid]("http://packages.ubuntu.com/intrepid/firefox") is 3.04.

If you really feel like having the latest stable releases within a few days of their release, I'd suggest you check out [Arch Linux]("http://archlinux.org").  It's not the distro for many people, but it's [extrememly up-to-date]("http://distrowatch.com/table.php?distribution=arch"), and rolling releases mean that you never have to deal with upgrades to new versions.

---

### Post by philinux on 2008-11-27
If you activate the backports repo you'll get more updates.

And if your feeling itchy for a challenge you could activate proposed too.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

