---
title: "Screen Resolution Trouble after install"
date: 2005-02-27
forum: Hardware &amp; Laptops
---

### Post by awilhelm on 2005-02-27
I'm installing several different Linux Distro's on refurb equipment for a school system. The users are going to choose one to be the district standard.

A friend gave me an Ubuntu set so I decided to try it as it seemed like an easy standard supported way of running Debian, which I have tried.

I tested a system with the live cd with perfect result. (Using that system right now to post this.) However after harddrive install I can only get 640x480 resolution. I can't seem to get any change forced. Should I possibly have selected something other than the default VESA video during install?? Should I indentify the motherboard video and reinstall? Or is there some configuration for x that I can change without install?

Okay I found the x.org thread and there is a solution to try with a text configurator
sudo dpkg-reconfigure xserver-xfree86
I'll try that.
Didn't work, x not installed error??
Okay tried again from Root Terminal window without the suda and rechecked spelling and it ran the reconfigure, I'll restart and see if this works.

No luck, I've tried S3 Trio and VESA and others and config seems to configure with all the supported video sizes but after restart it is still just 640x480???

Other distros I've tried auto configured video on the same system with no problems, and the live CD does the same??? :???:

---

