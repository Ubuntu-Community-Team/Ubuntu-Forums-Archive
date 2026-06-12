---
title: "recommended way to build i915 drivers (DRI, mesa)"
date: 2008-09-07
forum: Hardware
---

### Post by adamantivm on 2008-09-07
Hi,

I'm trying to configure my Thinkpad to use a dual-head display with DRI enabled and, to do that, it seems I have to apply a couple of very simple patches: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/146859](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/146859)

My question is: what is the easiest recommended way to build these drivers without screwing my standard Ubuntu Hardy set-up?

Thanks,

Julian

---

### Post by adamantivm on 2008-09-09
While there is no reply, I'll start posting what I find myself along the way.

Regular (non restricted) video drivers seem to come as part of Xorg. Here is a URL that I found after some digging around that seems to be talking about what I need: [http://xorg.freedesktop.org/wiki/CompileXserverManually#head-a1aa3f4ddc919c1e913e626d1fce3d402f3d9a69](http://xorg.freedesktop.org/wiki/CompileXserverManually#head-a1aa3f4ddc919c1e913e626d1fce3d402f3d9a69)

In Ubuntu Hardy, the right commands seem to be:

```
sudo apt-get build-dep xserver-xorg-video-intel
```

which takes care of downloading the build dependencies and:

```
sudo apt-get source xserver-xorg-video-intel
```

which gets the actual source code and puts it in /usr/include/xorg/xserver-xorg-video-intel-2.2.1

NOW I do have the source code for what is already installed via packages and I can find the file I wanted to patch. I hope I can compile and replace this driver now ...

---

### Post by adamantivm on 2008-09-10
A friend pointed me [here]("http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html"), which was very helpful for what I needed to do

---

