---
title: "Flash 9 + nvidia dualview (twinview) YouTube fullscreen issue"
date: 2008-09-04
forum: General Help
---

### Post by gybe on 2008-09-04
Hello!

New here. ;) Been using Ubuntu for three days now. ;)

I was going through everything I could possibly find about flash and firefox and I managed to set it up right. So now I am using flash player 9 with FF, installed it by [this method]("http://ubuntuforums.org/showthread.php?t=766683"). Everything works fine now, I have even managed to get amarok back working with ALSA so I am not experiencing those pulse audio negotiations.

I am using two displays at the time. They are both identical, running off of GeForce 6600. I have also installed the 3D driver from the package manager. Everything is running fine and I am using twinview (extended desktop) by modifying the xorg.conf file myself after 5 minutes of googling. The only real issue with this setup is that I cannot watch YouTube videos in fullscreen.
I tried to turn off the twinview in xorg.conf so only one (primary) display was being used and it worked without a problem.
With twinview I get fullscreen video forced on a secondary display even though I am usually running FF on a primary display. It just drops it in the secondary display, the video size is the same as in window mode, the area around it (which should be fullscreen) is tipical YouTube white.

It is not that I am much of a YouTube watcher, but in my case when I'm doing the thing it has to be flawless in any way possible. I tried other video portals and they load fullscreen perfectly on my primary display.

Anyone having the same issue?

Thanks for you help!

---

### Post by innernaut on 2008-10-07
I have the exact same issue.  Anyone know whats up with this?

---

### Post by Demian1980 on 2008-10-15
I have the same problem.

Grtz

D

---

### Post by cordor on 2008-12-02
It seems to me Flash 10 has the same problem too. Here is a workaround.

1. install vlc plugin for firefox(mplayer has audio sync problem on flash video)

2. install greasemoneky if you don't have it.

3. install this userscript. 

[http://userscripts.org/scripts/show/25318](http://userscripts.org/scripts/show/25318)

This will replace flash player on youtube pages.

---

### Post by Roasted on 2008-12-06
I just set up twinview myself.

I have a 9600GT PCIE 2.0 graphics card, a 22 inch ViewSonic LCD monitor, and a 17 inch Dell CRT as my secondary.

I'm running Ubuntu Intrepid 8.10 64 bit.

Same issue here.

---

### Post by levelnext on 2008-12-07
Ubuntu Hardy 64 bit, flash 10, same issue.

---

### Post by JKT7 on 2008-12-18
Ubuntu 8.10 Intrepid Ibex, 64 bit, flash 10, same issue.

---

### Post by XtremXpert on 2009-01-05
Same here, gonna install an other distro (Suse) and let you know if it's a ubuntu or upstream bug

---

### Post by redilyn on 2009-01-05
Not just with nvidia cards either.

Same problem here with Ati & Big Desktop.

---

### Post by XtremXpert on 2009-01-06
Just install OpenSuse and got the same issue, so it's not a ubuntu specific bug.  I have the impression that the bug is from the youtube player itself.

---

### Post by tuxxy on 2009-01-06
Yep same here, opens the video on second monitor too.

---

### Post by XtremXpert on 2009-01-06
Ok, we can fix that issue by using the new player (warp) in the test area of youtube ([http://www.youtube.com/testtube](http://www.youtube.com/testtube)).

So jump directly there [http://www.youtube.com/warp_speed](http://www.youtube.com/warp_speed) instead of the normal home page.

To launch a video in full screen, juste replace the watch? by warp.swf.

So watching Akon Right na na na normaly at [http://www.youtube.com/watch?v=tTJcUwOy6qM](http://www.youtube.com/watch?v=tTJcUwOy6qM) became [http://www.youtube.com/waarp.swf?v=tTJcUwOy6qM](http://www.youtube.com/waarp.swf?v=tTJcUwOy6qM) to watch it in the new warp player.

Don't forget to put firefox in fullscreen mode (F11) and enjoy :popcorn:

---

### Post by Roasted on 2009-01-08
We have to manually change the "watch?" part in every url of every video we'll ever watch on YouTube in order to make it full screen?

If that's the case, I'll be quite happy keeping the screen small. I'll just deal with it.

---

### Post by spidermagicat on 2009-01-24
this is problem with all flash though, I personally need it sorted for BBC iplayer or tvcatchup :-).

As a bonus piece of info I setup my twinview with the nvidia-settings application. Some might find it easier than manually editing the xorg.conf file manually, I know I did (you have to run it as root to save to xorg.conf obviously)

---

### Post by Seaweed on 2009-03-14
Same problem here is there no real fix fix for this other than work arounds?

---

### Post by ugkbunb on 2009-04-18
Same issue here... totem-plugin and greasemonkey script is a decent workaround for youtube... but that still doesn't sovle the other flash websites. I read somewhere that Adobe has this by-design.. they consider a security issue to have a fullscreen flash on the non-"primary-monitor".

---

### Post by zsobin on 2009-10-15
I have a workaround I use.
Just "Zoom" in on it with Compiz accessibility options.
Its not real elegant but it is workable.

Under add/remove I typed compiz.
I installed "Desktop Effects" and "Advanced Desktop Effects"
Under System->Preferences->Appearance, choose "Advanced"
"Advanced" didn't appear for me but I chose "Extra" and that worked.
Under System->Preferences->CompizSettings Manager choose Enhanced Zoom Desktop.

I set zoom-in to <Super>Button1
I set zoom-out to <Super>Button2
Super is the windows key, Button1 & Button2 are the mouse keys.

I then zoom in on any video I'd like to watch in fullscreen.

---

### Post by jandrioli on 2010-01-07
Please vote in Adobe bug tracking system so they will fix this issue:

[http://bugs.adobe.com/jira/browse/FP-562](http://bugs.adobe.com/jira/browse/FP-562)

currently there are less than 50 votes :(

---

### Post by a2z on 2010-01-07
Good day everyone,

Youtube on my system is not consistant.

With some videos none of the buttons work. (I believe it has something to do with the codecs and or format used with the specific video)
To me it looks like "PAL" format might be problematic for Ubuntu/unix? youtube.

While other videos where the buttons actually work, I have been able to open and keep open full screen via ctrl + click on full screen button.

Note: The above observation from a noobs point of view. But might help in figuring out a complete solution. I hope...

a2z

---

### Post by smooth_dudes on 2011-09-06
I have the exact same problem, and i am still unable to find a solution :(

---

### Post by UltraAnders on 2011-09-06
Anyone tried this, ["Full Screen Hack"](http://al.robotfuzz.com/content/workaround-fullscreen-flash-linux-multiheaded-desktops)?
Few reasons I thought I'd ask here rather than just suck it and see:
[LIST=1]
[*]It's not clear to me if this is written for Unity.
[*]I'm not sure how to tell if I'm running native or ndiswrapper flash.
[*]I'm reluctant to run code I've found off the WWW. 8-[
[/LIST]

---

### Post by UltraAnders on 2011-09-06
Oops

---

### Post by shdwfeather on 2011-09-16
I can confirm that the fullscreen hack mentioned above works beautifully.

[http://al.robotfuzz.com/content/workaround-fullscreen-flash-linux-multiheaded-desktops](http://al.robotfuzz.com/content/workaround-fullscreen-flash-linux-multiheaded-desktops)

The hack itself is mere 30 lines of simple c code, and it's configurable for different display sizes and 32bit/64bit/ndiswrapper set ups. Just follow the instructions in the README file! Note that you may need to install libx11-dev and libxrandr-dev in order to compile the code.

---

### Post by woutervanvliet on 2011-09-27
It does work, but it's more of a workaround then a fix I'd say. And without knowing what kind of memory it consumes and how else it affects my browser performance I'm not really keen on running it.

Better alternative right now would be to turn on YouTube's HTML5 player. But, as others before me, that only solves it for YouTube.

However, I did watch the f8 event the other day, and that stream went fullscreen without problems. Still only on the primary monitor - but it worked. So it looks like there could be an actual way to fix it within the Flash player code, which YouTube hasn't done yet.

---

