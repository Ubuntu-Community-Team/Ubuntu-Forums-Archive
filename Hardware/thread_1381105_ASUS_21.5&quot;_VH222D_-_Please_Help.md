---
title: "ASUS 21.5&quot; VH222D - Please Help"
date: 2010-01-14
forum: Hardware
---

### Post by distortedecho on 2010-01-14
Hi, 

I have just purchased the Asus VH222D 1080p LCD monitor:

[IMG]http://www.negoziofree.com/images6/AS.3A.jpg[/IMG]

But I only get these options in my display, running Ubuntu 9.10:

[IMG]http://i47.tinypic.com/21bw0eg.png[/IMG]

"Something" just doesn't look right... I've never had a widescreen before. I had a 19" standard tft, which looked superb until it became faulty....

I feel I should be in a higher, 16:9, resolution? Please advise.

Desktop Screenshot:

[IMG]http://i45.tinypic.com/rkyjk1.png[/IMG]

---

### Post by distortedecho on 2010-01-16
Resolved.

Steps taken:

Tried to install the ATI Radeon Driver from their website without success.
Tried to use EnvyNG from the Universe Repo, which trashed Xorg/Xserver.

On boot I was asked to go into low graphics mode and lost 3d support.

So a friend of mine went into the console and used:

```
sudo apt-get remove --purge xserver-xorg
```

Rebooted back to console mode

```
sudo apt-get install xserver-xorg
```
```
sudo dpkg-reconfigure xserver-xorg
```

Rebooted

```
http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html
```

Now I'm set to 1920x1080 (16:9)

Woot!

---

