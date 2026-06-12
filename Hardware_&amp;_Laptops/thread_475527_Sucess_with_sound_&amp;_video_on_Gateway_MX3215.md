---
title: "Sucess with sound &amp; video on Gateway MX3215"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by jeeves on 2007-06-16
The [ Gateway MX3215 ]("http://support.gateway.com/s/Mobile/Q106/Magic/5948sp2.shtml") is an inexpensive laptop, but has been an absolute nightmare to get working with Linux. I guess the  UniChrome Pro Integrated Graphics Processor is not very linux friendly. Here is a short writeup of how I finally managed to get sound and video working on my MX3215;
[B]
Installing the graphic drivers[/B]
After installing Xubuntu, the my Gateway  booted up with vesa drivers running and a ridiculously low screen resolution, so I needed to install OpenChrome drivers. I used the instructions in the Community Documentation  [ [https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome") ] to get the 2D acceleration working. I had one problem when following the guide. When trying to run the "make" command while compiling the OpenCrome I would get "no makefile found" error. I'm not sure of the cause, but what fixed it was reinstalling** xorg-video-via** with the snaptic package manager. Then I ran through the steps in the guide again and everything worked without a hitch.
[B]
Workaround for  the blank screen when playing videos problem[/B]
Apparently there is a[ bug in the Open Chrome drivers]("http://www.openchrome.org/trac/ticket/40") that causes the video players to display a blank screen when playing back videos. While I don't have a fix I, I do have a workaround for watching your videos.
[INDENT]
1. Install Xine
[PHP]sudo apt-get install xine-ui[/PHP]

2. edit xine's "config" file located in the hidden ".xine" folder in your home folder. Uncomment the **video.driver** line and change its value to **xshm**
[I]
Now you should be able to see video, so long as you are using the xine player. Xine is a pretty decent player that does DVDs, so I don't mind this limitation.[/I][/INDENT]
[B]
Getting the sound to work[/B]
If the sound does not work, read this post [http://ubuntuforums.org/showthread.php?p=1469365#post1469365]("http://ubuntuforums.org/showthread.php?p=1469365#post1469365")

What I did was start alsamixer (type alsamixer in a terminal). Then I moved the focus on to the input labeled "External" using my arrow keys. Then I MUTED this input by pressing "M". I have no idea why this works, but it fixed the problem with my MX3215 not producing any sound.
[B]
Battery monitor[/B]
In Xubuntu Feisty Fawn the [battery monitor for the panel does not seem to be behaving itself.]("https://bugs.launchpad.net/xfce/+bug/113440") My workaround was to install** acpitool.**
[HTML]sudo apt-get install acpitool[/HTML]

This battery monitor is command line, so perhaps not the best for keeping tabs on the power level, but its enough for me. There probably are some better packages out there for monitoring the power level.

---

