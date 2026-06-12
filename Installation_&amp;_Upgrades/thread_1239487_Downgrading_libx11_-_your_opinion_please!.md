---
title: "Downgrading libx11 - your opinion please!"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by Rambetter on 2009-08-13
First I will explain what I did (that I need your opinion about) and then I'll tell you why I did it.  I'm running 8.04.3 Ubuntu.

I did the following, which is basically downgrading these packages to versions found in Gutsy (7.10).

```

dpkg --get-selections | grep libx11
echo "libx11-6 hold" | dpkg --set-selections
echo "libx11-dev hold" | dpkg --set-selections
dpkg -i libx11-6_1.1.1-1ubuntu4_i386.deb libx11-dev_1.1.1-1ubuntu4_i386.deb

```


I managed to find those .deb packages on [https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/) .
  I'm wondering if what I did is a good idea, meaning will it break dependencies with other programs/libs?

======

Here's why I did this:

I needed to get push-to-talk to work in Mumble.  I added this to xorg.conf:

```

Section "Extensions"
        Option  "XEVIE" "Enable"
EndSection

```


And that would cause Mumble to not start (just frozen).  This is a problem that was discovered before and is covered in several other threads, including here: [https://bugs.launchpad.net/ubuntu/+source/mumble/+bug/210905](https://bugs.launchpad.net/ubuntu/+source/mumble/+bug/210905)

If anyone knows of a better way to get push-to-talk to work in Mumble please let me know, but my main question for this post is: Is downgrading libx11 and libx11-dev a wise idea?

---

