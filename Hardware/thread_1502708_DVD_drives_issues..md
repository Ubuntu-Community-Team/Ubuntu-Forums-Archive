---
title: "DVD drives issues."
date: 2010-06-05
forum: Hardware
---

### Post by shadowcrunch on 2010-06-05
Hello! I'm back with more dvd drive problems. I spent some time trying other distros to find what was right for me...I went from ubuntu 9.10 to Fedora 12, Ultimate Edition 2.3, Ultimate Edition 2.6, Mandriva 2010, and back to ubuntu 10.04. Through it all, I may have figured something out about my optical drives...I'm thinking they are not compatible with linux. 

I'm running a dvd reader and a burner, both appear in the BIOS at startup, and both work perfect in windows. Both drives are around 4 years old. Since my first install of ubuntu 9.10, I have had problems with these drives. Ubuntu 9.10, one showed up in fstab, neither would mount (even in terminal). When I got to Ultimate Edition 2.3, with a little help from a forum mod and some other sites, I tweaked the fstab settings for both drives (they both appeared right from install) and they both mounted discs perfectly, for about 3 days...after that it was hit or miss. Ultimate Edition 2.6, again neither drive showed in fstab, but the reader would mount only data discs if they were in at startup. Mandriva found both drives, all the way down to the model numbers, but neither were able to mount anything. 

Now I'm running Ubuntu 10.04. One drive showed in fstab, but will not mount any type of drive I put in it. After trying all of these distros, is it safe to say I just have drives that are totally incompatible? The reader is from Ben-Q, the writer is a Sony, if that helps at all.

---

### Post by dileepm on 2010-06-06
Try this post [http://starksolutions.blogspot.com/2010/05/linux-auto-mount-partitions.html](http://starksolutions.blogspot.com/2010/05/linux-auto-mount-partitions.html) I am not sure of the DVD drive compatibility with different OS flavors.

---

### Post by jjloupe on 2010-06-09
many are having optical drive issues with 10.04, but no one seems to want to admit it's an issue?

---

### Post by shadowcrunch on 2010-06-09
Sounds that way. I've been away from the desk for a while, but I did get a chance to try that link dileepm posted. Unfortunately it didn't make any noticeable changes to my optical drives. Keep in mind, for me it hasn't just been 10.04...I've had issue with every version and distro I've tried! 

Something odd though, even though I don't have any opticals listed in fstab, I was able to auto-mount a dvd that I left in there when I did a reboot. The icon was sitting on my desktop for about 30 minutes, then just vanished. Not sure how it found it, or why it went away. I guess we keep looking. Thanks for the posts!

---

