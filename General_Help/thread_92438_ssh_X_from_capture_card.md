---
title: "ssh X from capture card"
date: 2005-11-19
forum: General Help
---

### Post by dc2447 on 2005-11-19
Does anyone know if I can tunnel X back from a TV card using ssh?  Ie - ssh to one machine and run TVtime from there?

---

### Post by dc2447 on 2005-11-20
Ok - I am trying to run tvtime over ssh but I get this
> davidcam@obiwan:~$ tvtime -v
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/davidcam/.tvtime/tvtime.xml
cpuinfo: CPU AMD Athlon(tm) , family 6, model 6, stepping 2.
cpuinfo: CPU measured at 1252.957MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display localhost:10.0, vendor The X.Org Foundation, vendor release 60802000
xfullscreen: Single-head detected, pixel aspect will be calculated.
xfullscreen: Pixel aspect ratio on the primary head is: 1368/1355 == 1.01.
xfullscreen: Using the XFree86-VidModeExtension to calculate fullscreen size.
xfullscreen: Fullscreen to 0,0 with size 1280x1024.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is KWin and is EWMH compliant.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 61: NV Video Overlay.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/davidcam/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'saa7134', card ':Zolid Xpert TV7134' (bus PCI:0000:01:06.0).
videoinput: Version is 524, capabilities 5010015.
videoinput: Maximum input width: 720 pixels.
tvtime: Sampling input at 720 pixels per scanline.
xvoutput: Received X error: BadAccess (attempt to access private resource denied)
xvoutput: Received X error: BadShmSeg (invalid shared segment parameter)
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (63).
xcommon: Window fully obscured, marking window as hidden (63).
xcommon: Window made visible, marking window as visible (65).
xvoutput: Received X error: BadShmSeg (invalid shared segment parameter)
xvoutput: Received X error: BadShmSeg (invalid shared segment parameter)
tvtime: Cleaning up.
Thank you for using tvtime.


---

### Post by dc2447 on 2005-11-20
To be clear - I can run other GTK apps over ssh and tvtime runs fine when running locally - it just doesn't work over ssh

---

### Post by Drain on 2005-11-20
[QUOTE=dc2447]To be clear - I can run other GTK apps over ssh and tvtime runs fine when running locally - it just doesn't work over ssh[/QUOTE]

can you run other video programs remotely over ssh? xine or mplayer? I've always had difficulty doing that, although I could run something like xine locally and have it play a file from a network share. It'd be interesting to see if you get this working. :-)

---

### Post by dc2447 on 2005-11-20
[QUOTE=Drain]can you run other video programs remotely over ssh? xine or mplayer? I've always had difficulty doing that, although I could run something like xine locally and have it play a file from a network share. It'd be interesting to see if you get this working. :-)[/QUOTE]

Gxine works flawlessly playing DivX over ssh

---

### Post by adrianhensler on 2005-11-21
I think (guessing) this is the key here:
> xvoutput: Received X error: BadShmSeg (invalid shared segment parameter)
xvoutput: Received X error: BadShmSeg (invalid shared segment parameter)
It's trying to use shared memory; and that's just not going to work over ssh like that. What you might be able to do is send the data over ssh and then play it; sort of like a myth setup but with only the mpeg. Not sure exactly how you would do that; if I think of something I'll try it and let you know. (I just tried tvtime over ssh to a cygwin shell; and it crashed as well. I can't reboot to my linux partition right now to try from linux->linux; but I'll give it a try tomorrow).

Maybe you could netcat the data? I'm really grasping at straws now; I'm not really helping here am I...

ajh

(edit - what about using mencoder or something similar. I leave the actual command line up to the reader; but ssh (from pc with tv)-> tar(maybe not necessary) -> (internet/lan)->(pc for playback)->(expand with tar)-> save as mpeg stream on this pc -> start playing it with whatever. ) 

Or perhaps you could use Theora? ( [http://www.theora.org/theorafaq.html#41]("http://www.theora.org/theorafaq.html#41") for info on how to encode and stream Theora using the videoLan player) )Or the Real Media server (they used to have a freebie). Here's a link to some info for using Real Media Server:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialRealVideoStreaming.html]("http://www.yolinux.com/TUTORIALS/LinuxTutorialRealVideoStreaming.html")
Good luck; sorry I don't have any actual answers; but you might find something out of this. )

---

