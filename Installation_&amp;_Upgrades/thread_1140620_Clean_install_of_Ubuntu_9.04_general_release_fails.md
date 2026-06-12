---
title: "Clean install of Ubuntu 9.04 general release fails"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by bchalstrom on 2009-04-27
When doing a clean install, either directly from the CD or after running the live disk, the installation hangs up at the screen #2 where you have to select a timezone.  If I leave the default timezone selected and click the Forward button, nothing happens - for hours.  The progress indicator seems to be moving but extremely slowly.

When I choose the Safe Graphics option on the install, everything works fine.  Except that I cannot get the system to have a resolution higher than 800x600.

I did not have this problem on 8.10.

Brownell

---

### Post by sgosnell on 2009-04-27
I suspect you have a faulty live CD.  Boot the live CD you burned, and choose to check the media.  If that checks, check the md5sum of the .iso you downloaded.  If that checks, burn a new CD, and make sure you do a verify after burning.  Then boot that, and check the media again.  There are several places errors can be introduced, including the download and the burn.

---

### Post by barry_hk on 2009-05-16
I have exactly the same problem encountered, the clean installation stuck after the timezone setting page, but the installation can go on if the resolution is set at 800x600.

Although I haven't tried the media scanning of the CD, I don't think that is the cause because I have successfully used the same CD to fresh install Ubuntu on two other laptops.

I don't really need the 3D graphics effect on X31, but at least I would like to have 1024x768 resolution... and I cannot find how to change it in xorg.conf (?). Sorry if it is a dumb question since I am a newbie.

---

