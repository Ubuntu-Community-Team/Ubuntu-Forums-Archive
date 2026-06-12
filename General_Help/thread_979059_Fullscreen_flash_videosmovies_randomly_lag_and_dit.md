---
title: "Fullscreen flash videos/movies randomly lag and dither"
date: 2008-11-11
forum: General Help
---

### Post by RonB123123 on 2008-11-11
Fullscreen flash videos/movies randomly lag and dither

How do I prevent it from happening? I tried uninstalling the flash-nonfree package and installing the flash 10 Ubuntu 8.04 .deb file from adobe.com. The problem still exists.

I know it's a problem in flash on Ubuntu because when using the flash on Vista, it works fine. Is there any way to fix this?

---

### Post by RonB123123 on 2008-11-12
bump. Can anyone help?

---

### Post by RonB123123 on 2008-11-12
bumpity bump.

---

### Post by rudy.elgato on 2008-11-13
I know that on my system, running 8.04.1, fullscreen videos can look pretty jittery if I've left the "Visual Effects" setting to either the "Extra" or middle setting.  If I select "None" then my fullscreen videos play much, much smoother.  The setting I'm referring to is reached by:


System --> Preferences --> Appearance --> Visual Effects


Hope this helps some...

---

### Post by philinux on 2008-11-13
> **RonB123123 said:**
> Fullscreen flash videos/movies randomly lag and dither

How do I prevent it from happening? I tried uninstalling the flash-nonfree package and installing the flash 10 Ubuntu 8.04 .deb file from adobe.com. The problem still exists.

I know it's a problem in flash on Ubuntu because when using the flash on Vista, it works fine. Is there any way to fix this?

Usually a symptom of graphics card driver problem. What's your system specs?
What does system>admin>hardware drivers show?

---

### Post by RonB123123 on 2008-11-17
My visual effects are already set to none and when I go to System > Administration > Hardware Drivers, I just get a message saying "No proprietary drivers are in use in this system."

Any hope for me lol?

---

### Post by fatbuttlarry on 2008-11-17
Ron,

Try using the Restricted Drivers manager to enable proprietary drivers.  It may be called something different in newer releases, but the icon and interface should look similar. This may boost the performance issues you are seeing.  If your computer does not have a proprietary driver listed, research your card's 3d capabilities with Ubuntu.  There are [helper scripts]("http://www.albertomilone.com/nvidia_scripts1.html") available that will enable proprietary drivers with the "latest-and-greatest" but they are "hit-and-miss" for some people and I've noticed the helper scripts sometimes bring new issues.

[IMG]http://img442.imageshack.us/img442/5766/restricted0ue6.jpg[/IMG]

[IMG]http://img442.imageshack.us/img442/5391/restricted1fi9.jpg[/IMG]

[IMG]http://img442.imageshack.us/img442/2952/restricted2dg6.jpg[/IMG]


If new drivers do not help you, please read this background on Flash and Linux.  Enjoy.

Desktop Effects (aka "Compiz") can cause slowness (follow bottom link for explanation).
If you are running the 64-bit version of Ubuntu, you'll see a lot of posts with similar reports of buggy-ness, slowness, choppy-ness.

Myself and 3 of my colleagues have had performance boosts with the latest Flash 10.  We are all using the 64-bit versions of Ubuntu.  A friend using the 32-bit version of Ubuntu seems to have better performance without upgrading from Flash 9 to Flash 10.

Here's the script we used to upgrade Ubuntu 64-bit to the 32-bit version of Flash 10.  [COLOR=Red]**Only follow this link if you are running 64-bit:**[/COLOR]
[http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)

Today, Adobe released a 64-bit version of Flash 10.  I've installed it using this guide. **[COLOR=Red]This is for a beta version for 64-bit only.[/COLOR]**
[http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html)

... however, from my early testing **[COLOR="Red"]the 32-bit version of Flash 10 performs better than the 64-bit version of Flash 10 on my workstation ((K)Ubuntu 8.04 64-bit)[/COLOR]**.  This behavior is both with "Compiz" Desktop Effects **enabled** and with Desktop Effects** disabled**.

Here is an article written by an Adobe developer on why Flash still has some fundamental problems with Ubuntu, but more specifically why it doesn't play well Fullscreen with Linux as a whole.
[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

---

### Post by RonB123123 on 2008-11-26
Unfortunately, I dont have a restricted driver manager. All I have is System > Administrators > Hardware Drivers

And it says that my Ubuntu isn't using any proprietary drivers.

---

### Post by 900donuts on 2008-12-07
it sounds like you have the same problem i have except i have ubuntu 8.04 (my specs are in  my sig)

---

### Post by FountainDew on 2008-12-09
I'm also having the same issue, my graphics are onboard. When I was on XP youtube videos worked fine, and now that I'm on Ubuntu they stutter and have noticeable performance drops.

---

### Post by philinux on 2008-12-09
Need to know hardware specs and graphics card in use to be able to help.

That applies to all posters.
Cheers.

---

### Post by Allegretto on 2008-12-09
I've been having this problem as well, and I've found a fix for it. The problem lies in the latest version of the Flash plugin. I don't know why, but it has major performance issues, at least on my system (and apparently other people's judging by this thread). For example, this streaming video:

[http://www.gamersyde.com/stream_9595_en.html](http://www.gamersyde.com/stream_9595_en.html)

With the latest Flash plugin, it plays like a slideshow in Ubuntu (no problems in XP, incidentally). However, I noticed whilst using a Live CD of Linux Mint Elyssa, the video above played just fine, with no lag or stuttering at all. 

It turns out that on that Live CD an older version of Flash resides -- specifically 10.0 b218, a beta of Flash 10. As such, I thought it would be interesting to see what happened if I copied the libflashplayer.so file from the Live CD and replaced my Ubuntu one with it.

So I tried it, and sure enough, no more stuttering in Ubuntu, and generally far smoother and faster Flash playback everywhere. I'm not exactly sure what Adobe have cocked up since this beta version, but the performance differences between the two versions of the plugin are like night and day on my system.

I've uploaded the necessary file here in case anyone else wants to try it:

[http://rapidshare.com/files/171864617/libflashplayer.so.html](http://rapidshare.com/files/171864617/libflashplayer.so.html)

It should be noted that it's the 32-bit version of the plugin, so I guess wouldn't help the topic creator unfortunately. It just needs to be copied over the newer one in /usr/lib/adobe-flashplugin/

---

### Post by CarpKing on 2009-01-20
Anyone using the open-source ATI drivers should take a look at [this](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/300346).  Enabling that option fixed the problem for me.

---

### Post by tegnoto89 on 2009-01-27
Has anybody found a workaround for this?  The link posted by Allegreto no longer works (at least for me).

---

### Post by RonB123123 on 2009-02-07
I went to adobe.com and downloaded the .deb file for installing the latest Flash Player. I then installed it and rebooted firefox but the problem still exists. 

What do we do? Is there a work around? I really dislike having to login to Vista when I want to watch a movie.

---

### Post by ives31 on 2009-05-02
I have the same problem.
Allegreto...can you post a new link to that file?

thanks

---

### Post by ives31 on 2009-05-03
Well, I installed Suse 11.1 yesterday and the fullscreen flash video was perfect. I installed the same latest flash ( 10, I think it is).

So, this must be an Ubuntu problem

---

### Post by ives31 on 2009-05-03
[BslBryan]("http://ubuntuforums.org/member.php?u=797010") on another thread wrote:
Are you using Compiz? 
 If so, in the Advanced Desktop Effects Settings, under "General Options", there's an option called "Unredirect fullscreen windows."

this seems to have improved things imeasurably

---

### Post by RonB123123 on 2009-11-11
9.10 fixed my problem. Does anyones full screen flash now work?

---

### Post by mocatz187 on 2011-01-24
This happened to me after an update. Go into system administration/drivers and search to see if the update disabled you driver.
Enable  accelerated 3d graphics driver.
This corrected my problem.

Awhile back I had looked for a fix for this and read posts like this one which did not help, just passing along what worked for me.
Thanks.

---

