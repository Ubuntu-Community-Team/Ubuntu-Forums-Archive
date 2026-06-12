---
title: "ATi x1400: not shure xv works"
date: 2008-06-22
forum: Hardware
---

### Post by Decoy on 2008-06-22
Hi all!
Looks like VideoOverlay (xv) doesn't work. I've installed restricted driver and executed `sudo aticonfig --overlay-type=Xv`:
```
$ cat /etc/X11/xorg.conf | grep VideoOverlay
	Option	    "VideoOverlay" "on"
```
But video (especially HDTVrips) in Totem doesn't run smooth and in worse quality. BTW,
```
$ xvinfo 
X-Video Extension version 2.2
screen #0
 no adaptors present
```
Looks like xv overlay doesn't work... What can I do?

---

### Post by executive on 2008-06-22
not sure if this helps in your case, but after making changes as outlined by this post, im now able to play any 720p.x264 HD rips in full screen while using VLC:

[http://ubuntuforums.org/showpost.php?p=5197345&postcount=2](http://ubuntuforums.org/showpost.php?p=5197345&postcount=2)

no more stuttering or pixelated washed out video... had to set TexturedVideo to off since it was causing major flashing in window mode.

but for some reason the video quality still isn't as crisp and vibrant as playing the same file under winxp (using Media Player Classic with ffdshow). 

so for now im forced to dual boot into xp to watch 720p tv rips..:D

---

### Post by Decoy on 2008-06-24
Thanks!
[http://ubuntuforums.org/showpost.php?p=5197345&postcount=2](http://ubuntuforums.org/showpost.php?p=5197345&postcount=2) helps me!

---

