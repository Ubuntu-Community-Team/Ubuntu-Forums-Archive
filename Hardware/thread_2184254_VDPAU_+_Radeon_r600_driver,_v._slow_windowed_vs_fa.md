---
title: "VDPAU + Radeon r600 driver, v. slow windowed vs fast fullscreen video playback"
date: 2013-10-28
forum: Hardware
---

### Post by mr.matryc on 2013-10-28
Hi

Well recently I installed ubuntu 13.10, which by the way is really so great, and works better and better on my foxconn brazos nettop (nt-3700 to be exact).

I also setup VDPAU with radeon open source driver (r600), and in general at youtube I get accelerated video rendering & accelerated video decoding, and 1080p works smoothly with ~20% CPU usage each core. 
But there are some videos that does not work with acceleration, like: [http://www.youtube.com/watch?v=T6ixMKU1YT8](http://www.youtube.com/watch?v=T6ixMKU1YT8) 

When I click statistics for nerds I get black stats (not small transparent window, without accel/soft information), what is the problem? Since terminal doesn't split anything and both cores are used nearly 100% playing 360p video file with multiple frame drops. Where can I seek help? Where do I have to check...

And I also noticed that other websites (think triple x category ;) ), where we have embeeded video, when I start playback everything chokes as hell (so you can figure out that IS an inconvenience :P ) , and when I switch playback to fullscreen, playback is smooth and beautiful.

This situation is in both firefox and chromium-browser.

Thanks in advance.

**Edit:**

Well I did some additional research :)

And there seems to be a problem with adobe-flash plugin and vdpau.
After disabling adblock plus I've noticed that some flash banners and some elements of pages are unreadable and whole made of graphical artifacts so I've installed google chrome to check the behavior of their libpepflash plugin.

So fast configuration:
```
[chrome://flags/](chrome://flags/)
```
[COLOR=#000000][FONT=Ubuntu][B]Override software rendering list = ON
[/B][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]Fast check:
[/FONT][/COLOR]```
[chrome://gpu/](chrome://gpu/)
```
[COLOR=#000000][FONT=Ubuntu]
Output:
[/FONT][/COLOR]```
**Graphics Feature Status**


[LIST]
[*]Canvas: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Compositing: [COLOR=#008000]Hardware accelerated on all pages[/COLOR]
[*]3D CSS: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]CSS Animation: [COLOR=#008000]Accelerated[/COLOR]
[*]WebGL: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]WebGL multisampling: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash 3D: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D Baseline profile: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Texture Sharing: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Video Decode: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Video: [COLOR=#008000]Hardware accelerated[/COLOR]
[/LIST]

```

> Everything seems to be in order

**Test**: libflashplayer.so (Version:11.2 r202):
Youtube: [COLOR=#000000][FONT=Verdana]accelerated video rendering & accelerated video decoding, full speed gpu decoding ;)
video which I posed earlier was in html5 so no acceleration at all.
Rubbing site ;) : I've noticed that player has another layer to serve ads, so libflashplayer is not handling it too good with vdpau (when you resize the video, aspect of the video changes, and the layer also changes, but the video isn't fulling the layer, so there are those artifacts...), very slow in window player, after choosing fullscreen, v. fast, coz there is no additional layer in fullscreen mode!

**Test2**: libpepflashplayer.so ([/FONT][/COLOR]Version:11.9.900.117)
[COLOR=#000000][FONT=Verdana]Youtube: [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]accelerated video rendering & software video decoding, ehhh, no luck. Slow.
[/FONT][/COLOR][FONT=Verdana][COLOR=#000000]Same rubbing site, same video ;): EUREKA! I hit play, and no visible artifacts! Change of aspect, and resize of video ALSO! Everything works good (as for software decoding ofcoz), but 80%-90% of CPU is used. Switching to fullscreen is not a good option since no acceleration is made, but it works with a few frame drops.[/COLOR][/FONT]

[FONT=Verdana][COLOR=#000000]As for now you can just switch between libflash and libpep manually, but I'm wondering if libpep can be made to use gpu?

[B]EDIT2: 

[/B][/COLOR][/FONT][COLOR=#000000][FONT=Verdana]Well I've tested libflash against software decoding and it works well with windowed videos. So the reason of this behavior (broken flash banners) is that flash just bites with hardware acceleration, no easy solution...
 [/FONT][/COLOR]

---

