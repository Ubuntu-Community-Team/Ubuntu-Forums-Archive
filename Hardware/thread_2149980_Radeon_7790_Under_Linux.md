---
title: "Radeon 7790 Under Linux"
date: 2013-05-30
forum: Hardware
---

### Post by Kodeine on 2013-05-30
So I'm hoping to get a 7790 in the coming days. I've not read any problems with such video card under Linux but that isn't to say there isn't any. I ask on different forums who's video cards are better under Linux, AMD or Nvidia and every time I ask I get told that nVidia are way better then AMD. Faster performance less bugs but I'll ask again and this time it's AMD who has better documentaion, less bugs more drivers to choose from.

Has anyone used the 7790 with Ubuntu? Has there been any notable problems? Are the drivers almost on par with that of their Windows counterparts?

---

### Post by atcrank on 2013-06-27
Hi - I've just installed one last night to a 64-bit 12.04 setup.  I used the AMD website to download the driver and a really good forum post about setting it up.  The basics are to make the file executable somewhere in your home directory and run it as a shell script with sudo sh, but there is a bit of preconfig(meeting dependencies etc) and there seems to be some reason to buildpkg and then dpkg install.  I'm in a rush and can't find the exact link.  Might post later, but its here somewhere.

Early results - runs 3d games OK.  Mythtv misbehaved with VDPAU (wouldn't launch), and OpenGL playback (video freezes when you hit escape and I had to reboot to regain control), so I'm running with SLIM profile at the moment which puts everything on the CPU (as I understand it).  AMD has put source out there for these, so hopefully in the next few months (& if I go to 13.04) we'll get better perf. I'm dualbooting to windows to play games, but I'd like to get VDPAU access to UVD working.

More to follow.

---

### Post by atcrank on 2013-06-30
Here's the link for the howto: that I used.
 [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
I think its possible that I'd get better results from Mythtv with the open source drivers (there were instructions on Phoronix about updating so as to use the AMD-authored VDPAU code).  As a perpetual Linux beginner I'm hesitant to embark on that unless I need to.  Happy to try/test if someone wants to point me at a walkthrough.
Also, I should say the 3d games are TORCS and SuperTuxKart, which did not tax my old geforce 210 which I replaced.

---

### Post by Yellow Pasque on 2013-06-30
The proprietary AMD driver doesn't support VDPAU. It does, however, support xvba and va-api. See:  [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Hardware_Video_Decode_Acceleration_.28EXPERIMENTAL.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Hardware_Video_Decode_Acceleration_.28EXPERIMENTAL.29)

---

