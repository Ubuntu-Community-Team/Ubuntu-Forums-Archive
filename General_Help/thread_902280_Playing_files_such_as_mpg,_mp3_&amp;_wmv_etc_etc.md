---
title: "Playing files such as mpg, mp3 &amp; wmv etc etc"
date: 2008-08-27
forum: General Help
---

### Post by Fxy on 2008-08-27
Hi...  Could anyome pls tell me how i can play files such as mpg, mp3 & wmv on ubuntu.  I have done a few search on the forum and also on google, the best i have found is "VLC PLAYER" the only problem is my laptop doesn't have internet access.  You help will be much apprichated ;).. .

---

### Post by WRDN on 2008-08-27
> **Fxy said:**
> Hi...  Could anyome pls tell me how i can play files such as mpg, mp3 & wmv on ubuntu.  I have done a few search on the forum and also on google, the best i have found is "VLC PLAYER" the only problem is my laptop doesn't have internet access.  You help will be much apprichated ;).. .

The codecs to playback multimedia files aren't installed by default, because of legal reasons. If you can find a machine with internet access, then you can download the "GStreamer" plugins used for playback, or better yet, the packages that "ubuntu-restricted-extras" includes.

---

### Post by ghostdog74 on 2008-08-27
> **Fxy said:**
> Hi...  Could anyome pls tell me how i can play files such as mpg, mp3 & wmv on ubuntu.  I have done a few search on the forum and also on google, the best i have found is "VLC PLAYER" the only problem is my laptop doesn't have internet access.  You help will be much apprichated ;).. .
mplayer

---

### Post by arun.in on 2008-08-27
download **gstreamer0.10-ffmpeg, gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-bad** from **[packages.ubuntu.com]("http://packages.ubuntu.com")**
try to install it in your system, sometimes there is a chance to show some dependency problem, then download the required dependent packages from the same site.

[Learn Bash]("http://personal.riverusers.com/~thegrendel/abs-guide.pdf")

---

### Post by Fxy on 2008-08-28
> **arun.in said:**
> download **gstreamer0.10-ffmpeg, gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-bad** from **[packages.ubuntu.com]("http://packages.ubuntu.com")**
try to install it in your system, sometimes there is a chance to show some dependency problem, then download the required dependent packages from the same site.
 
[Learn Bash]("http://personal.riverusers.com/~thegrendel/abs-guide.pdf")
 
Yea well i download all the above highlighted in bold and opened terminal and then done the following steps:
[LIST]
[*]used the cd command to navigate to were the above is stored
[*]sudo apt-get install build-essential
[*]./configure
[/LIST]Duno if this is how you install them but only the first one runs stuff throught terminal etc etc n i still cant play any music or video files :| ...

---

