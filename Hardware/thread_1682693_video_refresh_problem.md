---
title: "video refresh problem"
date: 2011-02-06
forum: Hardware
---

### Post by boddhisatva on 2011-02-06
Hello,

I have a problem (**Ubuntu 10.10 64bit, GeForce 9600 GT**) when e.g. watching video, the image doesn't seem to refresh evenly, so it temporarily gets sort of 'cut up' into strips when there is a lot of movement, especially when a large area of the video is moving. It's not very noticeable at first, but gets quite irritating after a while. I used to have this problem on previous Ubuntu releases and on another hardware, but when I turned off Compiz it disappeared, so I could watch movies without problems. Also, it used to help to turn on the vsync for textures in the NVidia X Server settings, e.g. for games. Now nothing seems to help. I turn vsync on and off in xserver xvideo settings and opengl settings, I turn compiz off and on, but the problem doesn't go away. I'd appreciate any suggestions.

---

### Post by markthekdeguy on 2011-02-08
dunno what videoplayer you are using, but tearing is an issue.
if possible in the config of the videoplayer, maybe there will be
a selection in something like 'video preferences' or something.

in VLC for example,  in preferences, in video, in output
you can try one of the other options, they wont all work
and the ASCII ones draw the video with zillions of alphabet letters
and looks very weird !

try a different deinterlacing,
disable overlay (as a quick test)

you may not be using VLC of course, but these options or similar
ones are often available in other media players.
Goo Luck !
Mark

---

### Post by boddhisatva on 2011-02-08
Thanks for the reply!
The problem occurs in both Totem and VLC (I don't have other players). I tried changing all the settings in VLC, but I'm afraid nothing seems to help.

---

### Post by boddhisatva on 2011-02-08
Actually, the strange thing is, the tearing now does not happen when I turn off compiz. So it's the old compiz bug, apparently. I've found another thread, where the issue is discussed, perhaps I'll find a solution:
[http://ubuntuforums.org/showthread.php?t=1680775](http://ubuntuforums.org/showthread.php?t=1680775)

---

### Post by boddhisatva on 2011-02-08
I think I've solved it. In ccsm, in general options > image settings, there's a little option 'synchronize with vsync'. When I first saw it I knew immediately that would do the trick. And it did! I guess compiz needs to be told to synchronize with nvidia vsync.

---

### Post by markthekdeguy on 2011-02-12
Yes vsynch can be troublesome at times. it really is a case of
general tweaking about most times :) 

Have Fun !

---

### Post by ruif13 on 2011-02-12
Hi,

I had the same problem and I installed the last nvidia driver from source.

and solved my problem :)

regards.

---

