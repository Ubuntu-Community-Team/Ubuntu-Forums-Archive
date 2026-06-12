---
title: "Problem with KWorld PlusTV HD PCI 115 card (ATSC 115)"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by mystex.rm on 2007-08-09
I'm new to Linux and Ubuntu, I haven't been able to figure out how to get this working. I'm trying to learn how to set this up so I can build a mythtv setup. I'm no sure how to proceed from here but definitely will appreciate any help, I'm very excited about learning more about how this all works.

---

### Post by mystex.rm on 2007-08-10
I've tried looking through the forums and online but I can't figure out how to get them working, even tried looking at the mythtv wiki but I am completely stumped.

---

### Post by newlinux on 2007-08-11
what have you tried and what's not working? Do you have myth setup and just can't get this card to work?

make sure to look at [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110)


for setting up the card (applies to the 115 as well) and look at:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

for setting up myth in ubuntu. Without more information it is hard to help you.

Setup the card first with the info for the first link, then try to setup up myth.

---

### Post by mystex.rm on 2007-08-11
I just looked at it and I must admit I'm a little lost. It talks about the kernel source directory but I'm not sure where that is. I haven't actually tried installing mythtv yet as I was reading some posts and they advised that you could verify your card was working through using XawTV first. But I can't seem to find any channels with that.

---

### Post by mystex.rm on 2007-08-23
Ok I just did a clean install of ubuntu after trying many things. After the install I followed the mthwiki exactly on installing the Kworld ATSC card and its now being detected as a ATSC 110, when I run the mythtv channel scanner it detects a chanel, but its not showing anything but static. I know the card works as I've tried it in a windows computer and its working fine. What I'm wondering is if there is something perhaps I've missed or done wrong or some trouble shooting steps I should try. I'm still looking around to find answers to this but I'm kinda stumped.

---

### Post by newlinux on 2007-08-23
Are you scanning for OTA or QAM stations? Make sure you are scanning the right frequency for what you are trying to pick up. Also, you said your scan detects a channel. Is detecting multiple channels or just one? Another thing I've noticed it (this is weird) it that sometimes the input for QAM/NTSC/ATSC changes, so try the other input for scanning and viewing.

Let us know what you are trying to scan for and the settings you are using for your scan. Sorry I couldn't be more helpful

---

### Post by mystex.rm on 2007-08-23
I got it to work, had the cable plugged into the wrong socket. Now I just need to get sound working. Then I think I saw one of your posts detailing how you could use both cable inputs so I think I'll try to get that working next.Thanks for all the help newlinux.

---

### Post by newlinux on 2007-08-24
Glad it worked out. I would be glad to try an help you with sound problems as well. Are you trying to get the digital or the analog sound to work?

---

### Post by mystex.rm on 2007-08-24
I believe its the analog, since I'm not behind the cable box but rather on one of the other cable sockets in the house. Hey as a side not what's the best way to get active and start helping out others, I don't think I've much useful knowledge as of yet to help but I'd like to try.

---

### Post by newlinux on 2007-08-24
> **mystex.rm said:**
> I believe its the analog, since I'm not behind the cable box but rather on one of the other cable sockets in the house. Hey as a side not what's the best way to get active and start helping out others, I don't think I've much useful knowledge as of yet to help but I'd like to try.

Are you tuning QAM stations? If you are that is digital, if not it's analog (NTSC). They both come from the same cable, but are tuned differently.

Well, I've been using ubuntu for a year, and I just learned more as I had questions, and saw people with the same questions and started trying to answer them. So every so often I do a search on the forums on topics I know about and see if there are any questions I can answer, or if I know a resource where the answer is easy to find (like ubuntuguide.org, which is great). You pick stuff up as you go.

try running mythfrontend from a terminal with -v playback for more info.

```
mythfrontend -v playback
```

Try tuning a station. Then in the terminal you should see a lot of messages, some of them should relate to what's wrong with the audio. Does your audio work with anything else? How are you outputting your audio (to PC speakers, to a receiver, etc.).

---

### Post by mystex.rm on 2007-08-24
This is what I got when I ran that command.

```
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-08-24 22:11:39.129 Using runtime prefix = /usr
2007-08-24 22:11:39.453 Gnome-Screensaver support enabled
2007-08-24 22:11:39.454 DPMS is active.
2007-08-24 22:11:39.683 New DB connection, total: 1
2007-08-24 22:11:39.772 Connected to database 'mythconverg' at host: localhost
2007-08-24 22:11:39.799 Total desktop dim: 800x600, with 1 screen[s].
2007-08-24 22:11:39.847 Using screen 0, 800x600 at 0,0
2007-08-24 22:11:39.876 user: 1000 effective user: 1000 before privileged thread
2007-08-24 22:11:39.876 user: 1000 effective user: 1000 after privileged thread
2007-08-24 22:11:39.877 user: 1000 effective user: 1000 run_priv_thread
2007-08-24 22:11:39.921 Current Schema Version: 1160
2007-08-24 22:11:39.922 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-08-24 22:11:39.922 Enabled verbose msgs:  important general playback
2007-08-24 22:11:40.583 max_width: 1280 max_height: 1024
2007-08-24 22:11:41.054 Total desktop dim: 800x600, with 1 screen[s].
2007-08-24 22:11:41.057 Using screen 0, 800x600 at 0,0
2007-08-24 22:11:41.060 Switching to square mode (G.A.N.T.)
2007-08-24 22:11:41.195 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-08-24 22:11:41.598 Joystick disabled.
2007-08-24 22:11:42.069 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-08-24 22:11:42.162 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-08-24 22:11:42.390 Registering Internal as a media playback plugin.
2007-08-24 22:11:51.519 New DB connection, total: 2
2007-08-24 22:11:51.657 Connected to database 'mythconverg' at host: localhost
2007-08-24 22:11:52.192 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-08-24 22:11:52.216 Using protocol version 31
2007-08-24 22:11:52.905 TV: Attempting to change from None to WatchingLiveTV
2007-08-24 22:11:52.907 Using protocol version 31
2007-08-24 22:11:56.505 LiveTVChain(live-mythbackend-2007-08-24T22:11:52): ReloadAll(): Added new recording
2007-08-24 22:11:56.516 RingBuf(/var/lib/mythtv/recordings/1009_20070824221155.nuv): OpenFile(/var/lib/mythtv/recordings/1009_20070824221155.nuv, 12)
2007-08-24 22:11:56.569 RingBuf(/var/lib/mythtv/recordings/1009_20070824221155.nuv): CalcReadAheadThresh(4000 KB)
                         -> threshhold(146 KB) min read(32 KB) blk size(64 KB)
2007-08-24 22:11:56.579 DPMS Deactivated
2007-08-24 22:11:56.619 TV: StartRecorder(): took 48 ms to start recorder.
2007-08-24 22:11:59.653 detectInterlace(Ignore Scan, Interlaced Scan, 29.97, 480) ->Interlaced Scan
2007-08-24 22:11:59.882 Opening ALSA audio device 'default'.
2007-08-24 22:12:00.386 RingBuf(/var/lib/mythtv/recordings/1009_20070824221155.nuv): CalcReadAheadThresh(0 KB)
                         -> threshhold(32 KB) min read(32 KB) blk size(32 KB)
2007-08-24 22:12:00.387 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(0)
2007-08-24 22:12:00.393 Position map filled from DB to: 0
2007-08-24 22:12:00.394 SyncPositionMap watchingrecording, from DB: 1 entries
2007-08-24 22:12:00.528 Filling position map from 1 to 3
2007-08-24 22:12:00.531 Position map filled from Encoder to: 3
2007-08-24 22:12:00.532 SyncPositionMap watchingrecording total: 4 entries
2007-08-24 22:12:00.533 SyncPositionMap, new totframes: 90, new length: 3, posMap size: 4
2007-08-24 22:12:00.704 VideoOutputXv: ctor
2007-08-24 22:12:01.128 Over/underscan. V: 0, H: 0, XOff: 0, YOff: 0
2007-08-24 22:12:01.185 Display Rect  left: 0, top: 0, width: 800, height: 600, aspect: 1.33333
2007-08-24 22:12:01.186 Video Rect    left: 0, top: 0, width: 480, height: 480, aspect: 1.33333
2007-08-24 22:12:01.186 VideoOutputXv: Pixel dimensions: Screen 800x600, window 800x600
2007-08-24 22:12:01.248 VideoOutputXv: Estimated display dimensions: 332x250 mm  Aspect: 1.328
2007-08-24 22:12:01.249 VideoOutputXv: Estimated window dimensions: 332x250 mm  Aspect: 1.328
2007-08-24 22:12:01.259 VideoOutputXv: XvMCTex: Init failed
2007-08-24 22:12:01.275 VideoOutputXv: @ j=3 Looking for flag[s]: XvInputMask XvImageMask
2007-08-24 22:12:01.276 VideoOutputXv: Adaptor#0: I810 Video Overlay has flag[s]: XvInputMask XvImageMask
2007-08-24 22:12:01.319 VideoOutputXv: Grabbed xv port 65
2007-08-24 22:12:01.320 VideoOutputXv: XVideo surface found on port 65
2007-08-24 22:12:01.320 VideoOutputXv: XVideo Adaptor Name: 'I810 Video Overlay'
2007-08-24 22:12:01.430 VideoOutputXv: XVideo Format #0 is 'RV15'
2007-08-24 22:12:01.457 VideoOutputXv: XVideo Format #1 is 'RV16'
2007-08-24 22:12:01.457 VideoOutputXv: XVideo Format #2 is 'YUY2'
2007-08-24 22:12:01.458 VideoOutputXv: XVideo Format #3 is 'YV12'
2007-08-24 22:12:01.458 VideoOutputXv: XVideo Format #4 is 'I420'
2007-08-24 22:12:01.459 VideoOutputXv: XVideo Format #5 is 'UYVY'
2007-08-24 22:12:01.459 VideoOutputXv: Using XVideo Format 'I420'
2007-08-24 22:12:01.460 VideoOutputXv: CreateShmImages(32): video_dim: 480x480
2007-08-24 22:12:01.726 Display Rect  left: 0, top: 0, width: 800, height: 600, aspect: 1.33333
2007-08-24 22:12:01.727 Video Rect    left: 0, top: 0, width: 480, height: 480, aspect: 1.33333
2007-08-24 22:12:03.701 NVP: ClearAfterSeek(1)
2007-08-24 22:12:03.702 TV: StartPlayer(): took 4364 ms to start player.
2007-08-24 22:12:03.792 TV: Changing from None to WatchingLiveTV
2007-08-24 22:12:03.872 VideoOutputXv: ClearAfterSeek()
2007-08-24 22:12:03.873 VideoOutputXv: DiscardFrames(0)
2007-08-24 22:12:03.874 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2007-08-24 22:12:03.875 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2007-08-24 22:12:03.876 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2007-08-24 22:12:03.936 Realtime priority would require SUID as root.
2007-08-24 22:12:04.008 A audio timecode 11
2007-08-24 22:12:04.057 A audio timecode 34
2007-08-24 22:12:04.060 A audio timecode 58
2007-08-24 22:12:04.061 A audio timecode 78
2007-08-24 22:12:04.062 A audio timecode 100
2007-08-24 22:12:04.129 A audio timecode 124
2007-08-24 22:12:04.131 A audio timecode 147
2007-08-24 22:12:04.181 A audio timecode 170
2007-08-24 22:12:04.238 A audio timecode 195
2007-08-24 22:12:04.297 A audio timecode 216
2007-08-24 22:12:04.299 A audio timecode 240
2007-08-24 22:12:04.356 A audio timecode 263
2007-08-24 22:12:04.400 WriteAudio: buffer underrun
2007-08-24 22:12:04.704 RingBuf(/var/lib/mythtv/recordings/1009_20070824221155.nuv): CalcReadAheadThresh(10369 KB)
                         -> threshhold(379 KB) min read(32 KB) blk size(256 KB)
2007-08-24 22:12:04.789 nVidiaVideoSync: Could not open device /dev/nvidia0, No such device or address
2007-08-24 22:12:04.843 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2007-08-24 22:12:04.844 RTCVideoSync: Could not set RTC frequency, Permission denied.
2007-08-24 22:12:04.892 Using audio as timebase
2007-08-24 22:12:04.892 Video timing method: USleep with busy wait
2007-08-24 22:12:04.893 Refresh rate: 16579, frame interval: 33366
2007-08-24 22:12:05.535 NVP: Video is 3.1667 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:05.583 NVP: Video is 4.04589 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:05.588 NVP: Video is 4.96002 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:05.601 NVP: Video is 5.91536 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:05.653 NVP: Video is 6.84916 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:05.657 NVP: Video is 7.79674 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:05.705 NVP: Video is 8.78466 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:05.767 NVP: Video is 9.74288 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:05.832 NVP: Video is 10.7687 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:05.898 NVP: Video is 11.7405 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:05.965 NVP: Video is 12.739 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:06.031 NVP: Video is 13.7126 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:06.098 NVP: Video is 14.7051 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:06.165 NVP: Video is 15.7118 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:06.198 A audio timecode 1477
2007-08-24 22:12:06.246 NVP: Video is 16.744 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:06.262 A audio timecode 1500
2007-08-24 22:12:06.286 WriteAudio: buffer underrun
2007-08-24 22:12:06.299 NVP: Video is 9.03641 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:06.332 A audio timecode 1522
2007-08-24 22:12:06.333 A audio timecode 1546
2007-08-24 22:12:06.334 WriteAudio: buffer underrun
2007-08-24 22:12:06.378 NVP: Video is 3.51049 frames ahead of audio,
                        doubling video frame interval to slow down.
2007-08-24 22:12:06.421 A audio timecode 1569
2007-08-24 22:12:06.430 WriteAudio: buffer underrun
2007-08-24 22:12:06.436 NVP: Video is 3.90517 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.436 NVP: Video is 5.95591 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.437 NVP: Video is 7.24669 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.437 NVP: Video is 7.975 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.438 NVP: Video is 8.27399 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.440 NVP: Video is 8.25847 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.440 NVP: Video is 7.99958 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.441 NVP: Video is 7.56564 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.441 NVP: Video is 6.99293 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.442 NVP: Video is 6.31613 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.442 NVP: Video is 5.56878 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.443 NVP: Video is 4.75352 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.443 NVP: prebuffering pause
2007-08-24 22:12:06.443 NVP: Waiting for prebuffer.. 0 AAAAAAAAAAAULAAAAAAAAAAAAAAAAAA
2007-08-24 22:12:06.456 A audio timecode 1595
2007-08-24 22:12:06.511 A audio timecode 1615
2007-08-24 22:12:06.512 A audio timecode 1638
2007-08-24 22:12:06.552 A audio timecode 1662
2007-08-24 22:12:06.590 NVP: Waiting for prebuffer.. 1 AAAAAAAAAAAUUUULAAAAAAAAAAAAAAA
2007-08-24 22:12:06.629 A audio timecode 1685
2007-08-24 22:12:06.630 A audio timecode 1708
2007-08-24 22:12:06.675 A audio timecode 1731
2007-08-24 22:12:06.726 A audio timecode 1755
2007-08-24 22:12:06.728 A audio timecode 1778
2007-08-24 22:12:06.730 NVP: Waiting for prebuffer.. 2 AAAAAAAAAAAUUUUUUULAAAAAAAAAAAA
2007-08-24 22:12:06.773 A audio timecode 1801
2007-08-24 22:12:06.829 A audio timecode 1824
2007-08-24 22:12:06.832 A audio timecode 1847
2007-08-24 22:12:06.870 NVP: Waiting for prebuffer.. 3 AAAAAAAAAAAUUUUUUUUULAAAAAAAAAA
2007-08-24 22:12:06.877 A audio timecode 1871
2007-08-24 22:12:06.924 A audio timecode 1897
2007-08-24 22:12:06.978 NVP: Video is 3.9023 frames behind audio (too slow), dropping frame to catch up.
2007-08-24 22:12:06.984 A audio timecode 1917
2007-08-24 22:12:06.986 A audio timecode 1940
2007-08-24 22:12:07.039 A audio timecode 1963
2007-08-24 22:12:07.092 A audio timecode 1987
2007-08-24 22:12:07.093 A audio timecode 2010
2007-08-24 22:12:07.147 A audio timecode 2033
2007-08-24 22:12:07.207 A audio timecode 2056
2007-08-24 22:12:07.208 A audio timecode 2080
2007-08-24 22:12:07.265 A audio timecode 2103
2007-08-24 22:12:07.321 A audio timecode 2129
2007-08-24 22:12:07.368 A audio timecode 2149
2007-08-24 22:12:07.370 A audio timecode 2172
2007-08-24 22:12:07.425 A audio timecode 2197
2007-08-24 22:12:07.476 A audio timecode 2219
2007-08-24 22:12:07.477 A audio timecode 2243
2007-08-24 22:12:07.533 A audio timecode 2265
2007-08-24 22:12:07.578 A audio timecode 2288
2007-08-24 22:12:07.584 A audio timecode 2312
2007-08-24 22:12:07.631 A audio timecode 2335
2007-08-24 22:12:07.686 A audio timecode 2358
2007-08-24 22:12:07.687 A audio timecode 2381
2007-08-24 22:12:07.731 A audio timecode 2405
2007-08-24 22:12:07.777 A audio timecode 2430
2007-08-24 22:12:07.831 A audio timecode 2451
2007-08-24 22:12:07.832 A audio timecode 2474
2007-08-24 22:12:07.873 A audio timecode 2497
2007-08-24 22:12:07.918 NVP: prebuffering pause
2007-08-24 22:12:07.918 NVP: Waiting for prebuffer.. 0 AAAAAAAAULAAAAAAAAAAAAAAAAAAAAA
2007-08-24 22:12:07.925 A audio timecode 2521
2007-08-24 22:12:07.926 A audio timecode 2544
2007-08-24 22:12:07.968 A audio timecode 2567
2007-08-24 22:12:08.009 A audio timecode 2591
2007-08-24 22:12:08.011 A audio timecode 2614
2007-08-24 22:12:08.059 NVP: Waiting for prebuffer.. 1 AAAAAAAAUUUULAAAAAAAAAAAAAAAAAA
2007-08-24 22:12:08.199 NVP: Waiting for prebuffer.. 2 AAAAAAAAUUUULAAAAAAAAAAAAAAAAAA
2007-08-24 22:12:08.338 NVP: Waiting for prebuffer.. 3 AAAAAAAAUUUUUAAAAAAAAAAAAAAAAAA
2007-08-24 22:12:08.338 A audio timecode 2637
2007-08-24 22:12:08.404 A audio timecode 2661
2007-08-24 22:12:08.457 A audio timecode 2683
2007-08-24 22:12:08.459 A audio timecode 2708
2007-08-24 22:12:08.487 NVP: Waiting for prebuffer.. 4 AAAAAAAAUUUUUUULAAAAAAAAAAAAAAA
2007-08-24 22:12:08.529 A audio timecode 2730
2007-08-24 22:12:08.577 A audio timecode 2753
2007-08-24 22:12:08.579 A audio timecode 2776
2007-08-24 22:12:08.625 A audio timecode 2799
2007-08-24 22:12:08.627 NVP: Waiting for prebuffer.. 5 AAAAAAAAUUUUUUUUUUAAAAAAAAAAAAA
2007-08-24 22:12:08.682 A audio timecode 2822
2007-08-24 22:12:08.684 A audio timecode 2846
2007-08-24 22:12:08.732 A audio timecode 2869
2007-08-24 22:12:08.785 A audio timecode 2892
2007-08-24 22:12:08.787 A audio timecode 2915
2007-08-24 22:12:09.084 A audio timecode 2939
2007-08-24 22:12:09.156 A audio timecode 2965
2007-08-24 22:12:09.185 A audio timecode 2986
2007-08-24 22:12:09.186 A audio timecode 3008
2007-08-24 22:12:09.214 A audio timecode 3032
2007-08-24 22:12:09.242 A audio timecode 3056
2007-08-24 22:12:09.242 A audio timecode 3078
2007-08-24 22:12:09.299 NVP: prebuffering pause
2007-08-24 22:12:09.403 NVP: Waiting for prebuffer.. 0 AAAAAAAAAAAAAAAAAAAAAAAAAUAAAAA
2007-08-24 22:12:09.407 WriteAudio: buffer underrun
2007-08-24 22:12:09.453 A audio timecode 3101
2007-08-24 22:12:09.502 WriteAudio: buffer underrun
2007-08-24 22:12:09.514 A audio timecode 3126
2007-08-24 22:12:09.516 A audio timecode 3149
2007-08-24 22:12:09.544 NVP: Waiting for prebuffer.. 1 AAAAAAAAAAAAAAAAAAAAAAAAAUUULAA
2007-08-24 22:12:09.581 A audio timecode 3171
2007-08-24 22:12:09.624 A audio timecode 3197
2007-08-24 22:12:09.684 NVP: Waiting for prebuffer.. 2 AAAAAAAAAAAAAAAAAAAAAAAAAUUUUUL
2007-08-24 22:12:09.824 NVP: Waiting for prebuffer.. 3 AAAAAAAAAAAAAAAAAAAAAAAAAUUUUUL
2007-08-24 22:12:09.899 A audio timecode 3217
2007-08-24 22:12:09.901 A audio timecode 3240
2007-08-24 22:12:09.948 A audio timecode 3266
2007-08-24 22:12:09.967 NVP: Waiting for prebuffer.. 4 ULAAAAAAAAAAAAAAAAAAAAAAAUUUUUU
2007-08-24 22:12:10.026 A audio timecode 3287
2007-08-24 22:12:10.028 A audio timecode 3310
2007-08-24 22:12:10.078 A audio timecode 3333
2007-08-24 22:12:10.111 NVP: Waiting for prebuffer.. 5 UUULAAAAAAAAAAAAAAAAAAAAAUUUUUU
2007-08-24 22:12:10.126 A audio timecode 3357
2007-08-24 22:12:10.251 NVP: Waiting for prebuffer.. 6 UUUULAAAAAAAAAAAAAAAAAAAAUUUUUU
2007-08-24 22:12:10.392 NVP: Waiting for prebuffer.. 7 UUUULAAAAAAAAAAAAAAAAAAAAUUUUUU
2007-08-24 22:12:10.461 A audio timecode 3385
2007-08-24 22:12:10.462 A audio timecode 3403
2007-08-24 22:12:10.542 A audio timecode 3426
2007-08-24 22:12:10.544 A audio timecode 3449
2007-08-24 22:12:10.598 A audio timecode 3472
2007-08-24 22:12:10.658 A audio timecode 3497

```

---

### Post by newlinux on 2007-08-25
Judging by this you are using the card to tune analog stations (you set this up as a V4L card instead of a DVB card). Analog is a little harder to get working, especially due to this not being a hardware encoding card for analog signals.

Did you try the commands:

 v4lctl -c /dev/video0 setattr automute off
 v4lctl -c /dev/video0 volume mute off

assuming /dev/video0 is the device for this tuner (if you have other tuners it might be /dev/video1 or something).

Do you get no sound, or crackling sound?

---

### Post by mystex.rm on 2007-09-16
sorry its taken me a bit to reply back been busy with family. I just ran those commands but still have no audio at all when watching tv. I'm going to try recording a show and see if I can get anything.:confused:

---

