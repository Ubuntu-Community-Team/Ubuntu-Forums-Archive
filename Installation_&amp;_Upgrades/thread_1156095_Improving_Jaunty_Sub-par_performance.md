---
title: "Improving Jaunty Sub-par performance"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by slumbergod on 2009-05-11
This post is just to help anyone else who might be suffering poor performance with Jaunty. I am using an Acer Aspire 5720 laptop and following a clean install of Jaunty Xubuntu, firefox was jerky with scrolling and video playback had similar issues. I also notice my sound was very quiet and the volume control wheel on my laptop stopped working. 

Overall, I have found Jaunty to be a very lack-lustre release. My main reason for installing Jaunty was that Xfce4.6 was now included. 

To address the sound issues, I had to get rid of PulseAudio components and go back to using ALSA/OSS. Decent volume returned after rebooting, though the laptop's volume wheel control still does not function.

As for the crappy video performance, well I tried two things:

Fistly, I tried downgrading the intel driver to the intrepid version. It did improve things but not enough.
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Then I came across an alternative so I re-upgraded back to the Jaunty intel driver then tried method 2. This method improved things noticably and things feel much snappier now.
[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html/comment-page-2#comment-8810](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html/comment-page-2#comment-8810)

You can also try this PPA for more up-to-date drivers:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

or follow this article to live on th bleeding edge:
[http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html](http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html)

In general, I have to say I am disappointed that Jaunty had these issues. It felt like a step backwards rather than a step forwards. I wonder if new people to Ubuntu will not get a good impression of Linux if they experience such issues. All the forum postings I read clearly state there are issues with intel drivers and the 965 chipset and that they are not likely to be resolved until the next release of Ubuntu.

---

