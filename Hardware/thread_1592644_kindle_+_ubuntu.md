---
title: "kindle + ubuntu"
date: 2010-10-10
forum: Hardware
---

### Post by phoda on 2010-10-10
how can i set up my ubuntu 10.10 in order to use amazon kindle?

---

### Post by S.R on 2010-10-10
As far as I know Kindle does not support Linux and I believe it uses a FAT file system. My recommendation is to use WINE to load your Kindle.

---

### Post by Dark_Stang on 2010-10-11
Article written in May, detailing how to make a Kindle work with Ubuntu.
[http://helpforlinux.blogspot.com/2010/05/manage-kindle-from-ubuntu.html](http://helpforlinux.blogspot.com/2010/05/manage-kindle-from-ubuntu.html)

---

### Post by Jazzy_Jeff on 2010-10-12
Are you talking about the Kindle for PC app or the actual Kindle. 10.04 sees my Kindle with no problem and mounts it like a removable drive. Then I start up Calibre to add books I have on my computer.

---

### Post by phoda on 2010-10-12
> **Dark_Stang said:**
> Article written in May, detailing how to make a Kindle work with Ubuntu.
[http://helpforlinux.blogspot.com/2010/05/manage-kindle-from-ubuntu.html](http://helpforlinux.blogspot.com/2010/05/manage-kindle-from-ubuntu.html)

doesn't work... i've tried... i have a kindle dx device, and i'm using ubuntu 10.10... :(

---

### Post by zengyro on 2010-10-13
Yeah the Kindle App under WINE was working great, but now appears to be broken in v10.10. 

Books can be read ok, but it doesn't seem to be able to connect to Amazon to download books and samples. 

Any ideas?

---

### Post by otherethe on 2010-10-13
> **zengyro said:**
> Yeah the Kindle App under WINE was working great, but now appears to be broken in v10.10. 

Books can be read ok, but it doesn't seem to be able to connect to Amazon to download books and samples. 

Any ideas?

Do any of your wine programs connect online? whats your out put for the program you speek of does wine crash when you try to connect?

---

### Post by zengyro on 2010-10-13
> Do any of your wine programs connect online?
I was running Spotify under Wine too. It seems to connect ok, but crashes due to what seems to be a non networking reason.

> whats your out put for the program you speek of does wine crash when you try to connect?
With the Kindle app under Wine it just can't connect to the Amazon server. It says 'Cannot Connect. Please Try again Later'
This has happened for a week, so it isn't a problem at their end.

---

### Post by zengyro on 2010-10-19
So I was able to get it to work. All that needed to be done was to upgrade to the latest version of Wine. 

Note that this is achieved by using the Wine repository, not the one maintained by Canonical. 

You can follow the instructions [here]("http://www.winehq.org/download/deb"). 

The recent posts in this [thread]("http://ubuntuforums.org/showthread.php?t=1326044") explain the problem a little better.

---

