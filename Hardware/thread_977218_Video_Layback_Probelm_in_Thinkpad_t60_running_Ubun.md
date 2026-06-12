---
title: "Video Layback Probelm in Thinkpad t60 running Ubuntu 8.10"
date: 2008-11-10
forum: Hardware
---

### Post by ramnarayan on 2008-11-10
Hi

Installed ubuntu 8.10 about a week back on my Thinkpad T60. Everything seems pretty good, faster, cleaner, etc.
But my video playback is quite bad - i get constant flickering -

There is as ATI X1300 graphics card - for which i installed the fglrx module and enabled it. Did not change the problem, i uninstalled it completely - even that did not help.

Further sometimes when i play two videos (through a playlist) the first video continues flickering - both in fullscreen mode and in normal mode, but just sometimes the second video (only in full screen mode) works normally.

So what could be wrong.

Could not find help at the thinkwiki site or anywhere else on this forum, or on the net (atleast with the search strings i used)

would appreciate help

ram

---

### Post by ramnarayan on 2008-11-10
> **ramnarayan said:**
> Hi

Could not find help at the thinkwiki site or anywhere else on this forum, or on the net (atleast with the search strings i used)


Ok when i used "flickering video" got lots of good results
some are
[http://ubuntuforums.org/showthread.php?t=964912](http://ubuntuforums.org/showthread.php?t=964912)

[http://ph.ubuntuforums.com/showthread.php?t=763649](http://ph.ubuntuforums.com/showthread.php?t=763649)

[http://ph.ubuntuforums.com/showthread.php?t=965246](http://ph.ubuntuforums.com/showthread.php?t=965246)

---

### Post by ramnarayan on 2008-11-10
found my solution in
[http://ubuntuforums.org/newreply.php?do=newreply&p=6084066](http://ubuntuforums.org/newreply.php?do=newreply&p=6084066)

> **Stex said:**
> If you haven't already try running (Alt+f2) [COLOR="DarkGreen"]gstreamer-properties[/COLOR]

In the video tab try a selection of the output options, these affect programs using gstreamer (e.g. totem).

Thanks Stex , works for me 
chose X Window No XV 

will figure out what the compromise is later on

ram

---

