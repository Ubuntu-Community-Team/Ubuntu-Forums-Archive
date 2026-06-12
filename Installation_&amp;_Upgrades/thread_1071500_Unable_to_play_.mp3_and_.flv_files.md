---
title: "Unable to play .mp3 and .flv files"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by ghataknav on 2009-02-16
hi,

i've just installed ubuntu 8.10 on my acer laptop. i have noticed that i am unable to play .mp3 and .flv files. 

earlier when i used fedora, i would download the required rpms from some open source links. can i do the same in ubuntu? or, do i have to connect my laptop to the net to get it upgraded ?

thanks in advance.

---

### Post by panmoto on 2009-02-16
go to synaptic package manager (you must have internet connection) and install :
- gstreamer0.10-plugins-ugly
- gstreamer0.10-plugins-bad
- gstreamer0.10-plugins-good

those contain needed codecs to play most of media files.

---

### Post by ghataknav on 2009-02-18
> **panmoto said:**
> go to synaptic package manager (you must have internet connection) and install :
- gstreamer0.10-plugins-ugly
- gstreamer0.10-plugins-bad
- gstreamer0.10-plugins-good

those contain needed codecs to play most of media files.

thanks for the info. i'll try that out.

---

### Post by Therion on 2009-02-18
Open a terminal and enter (copy & paste):```
sudo apt-get install ubuntu-restricted-extras
```
You can also use Synaptic to search for, and install, that same package (ubuntu-restricted-extras) if you don't like using the Terminal.  .mp3 is a "restricted" codec so you'll need that to play .mp3 files but the package includes codecs for a lot of other proprietary formats that you're going to want sooner or later.

---

