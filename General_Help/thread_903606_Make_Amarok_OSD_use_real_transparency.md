---
title: "Make Amarok OSD use real transparency"
date: 2008-08-28
forum: General Help
---

### Post by oobuntoo on 2008-08-28
After much searching, I came across [http://forum.compiz-fusion.org/showthread.php?t=1866&page=2]("http://forum.compiz-fusion.org/showthread.php?t=1866&page=2"). Amarok's OSD can now be configured to use real transparency. So, thanks to those guys over at compiz-fusion forum.

Here's how:

1. Must have compiz/compiz-fusion installed and enabled and also have CCSM installed.

2. Disable the fake transparency in the Amarok's setting; that is, untick the "Make the background translucent" under OSD within Amarok's setting.

3. In the CCSM's General Options, go to Opacity Settings tab and add new entry to Windows opacities section with the following line for Opacity windows:

   (name=amarokapp & role=osd & type=normal)

and any number you want for Opacity window values. I used 90.

4. This is optional. If you use Blur Windows plugin and want to blur the OSD background, add to the "Alpha blur windows" within the Blur Windows plugin's setting, the following line:

   (name=amarokapp & role=osd & type=normal)

Make sure to tick the "Alpha Blur" below it.



If anyone else know a better way to do this, please comment.

---

