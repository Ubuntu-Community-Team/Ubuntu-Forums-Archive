---
title: "Jaunty audio issues when using nVidia drivers"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by homestar92 on 2009-04-23
So I updated to 9.04 today and after getting my nVidia drivers set up, (I tried all 3 options, 173, 177, and 180, all have the same issue) my audio screwed up. Basically, all audio (and video for that matter) seems to play very choppily, and at 2-3x speed. This happens on mp3s, video files, and even Youtube. However, if i run in low graphics mode, audio is fine, but no compiz and I get a max resolution of 800x600, which isn't really very usable. So, is there any way to fix these issues? And for that matter, has anyone ever heard of this before?

---

### Post by henwyn on 2009-04-23
I am not running nVidia drivers so I cna't comment on them, but audio has been off and on all through the testing process. I have been running the latest version of PulseAudio and it's on again for me so you might want to try the newest version which is available from the following site. Just add it to your /etc/apt/source.lst, either using an editor opened sudo as root or in synaptic under Settings Repositories Third-party Software. 
[http://ppa.launchpad.net/themuso/ppa/ubuntu/jaunty](http://ppa.launchpad.net/themuso/ppa/ubuntu/jaunty) main
If you don't have the medibuntu site added, you might want to add it as well and then update and see if that fixes anything.
[http://packages.medibuntu.org/jaunty](http://packages.medibuntu.org/jaunty) free non-free

If that doesn't help, it's probably beyond my expertise but I've generally found that with patience most things get fixed with updates. That said, you might get more help in the multimedia section. Good luck.

---

### Post by homestar92 on 2009-04-23
Thankfully, I got it to work by updating ALSA with a shell script I found here:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

