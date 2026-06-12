---
title: "[done] How to fake x.org or nvidia-96"
date: 2015-02-13
forum: Hardware
---

### Post by Byb on 2015-02-13
Good morning
I have an old laptop with a video GeForce4 4200 Go (nv28M id 0x0286) with precise. Unfortunately, although I wanted to stick to precise and thought it was enough to keep the pc working, I enabled the HarWareEnablement Stack which removed nvidia-96 package and I can't reinstall it because ABI thing incompatibility. Is there a way to make one accept the other or downgrade x.org to the original precise version?

My /etc/apt/preferences is empty and I have not checked the box "precise-backports" in synaptics.

Thank you

My solution was to revert back to the genuine 12.04. I read that having a pre-HWE stack kernel was required so I installed 3.2.0-38 and rebooted to it.
I also had to purge all -lts-trusty packages and resinstall xserver-xorg-core and xserver-xorg to bring back a graphical display.

---

