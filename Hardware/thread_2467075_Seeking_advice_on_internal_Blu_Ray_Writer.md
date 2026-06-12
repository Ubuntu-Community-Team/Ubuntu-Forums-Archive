---
title: "Seeking advice on internal Blu Ray Writer"
date: 2021-09-15
forum: Hardware
---

### Post by satimis on 2021-09-15
Hi all,

I'm prepared purchasing an internal SATA Blu-ray Writer to replace my old ASUS DRW-24D5MT writer

Drive: /dev/cdrom
Vendor                      : ASUS    
Model                       : DRW-24D5MT      
Revision                    : 2.00
Profile List Feature
DVD-R - Double-Layer Sequential Recording

DRW-24D5MT Specification
[https://www.asus.com/Motherboards-Components/Optical-Drives/Internal-DVD-Drive/DRW-24D5MT/techspec/](https://www.asus.com/Motherboards-Components/Optical-Drives/Internal-DVD-Drive/DRW-24D5MT/techspec/)

The main purpose of the new burner is for reading DVD Video and CD Music discs.  Burning DVD is ONLY in rare occasion.  I'm prepared converting all old stocks of music discs and DVD Video to mp3 and mp4 files respectively, to be stored in computer.

I'm now looking at following 2 Burners;
1)
Panasonic SATA 3D Blu-ray Burner UJ272
Specfication
[http://www.bluraysupplier.com/products/Panasonic-UJ272-Super-Slim-BD-RE-Blu-ray-Burner.html#.YUCKhvwzaV4](http://www.bluraysupplier.com/products/Panasonic-UJ272-Super-Slim-BD-RE-Blu-ray-Burner.html#.YUCKhvwzaV4)

2)
LG CH12NS40 Blu-Ray Combo Drive
(Internal SATA 12x Super Multi Blue LightScribeTM with 3D Play back)
Specification
[https://www.lg.com/ca_en/all-in-one-chromebase/lg-CH12LS28-internal-blu-ray-combo-drive](https://www.lg.com/ca_en/all-in-one-chromebase/lg-CH12LS28-internal-blu-ray-combo-drive) 

Could they work on Ubuntu 20.04?  Comment and advice would be appreciated.

Thanks in advance

Regards

---

### Post by TheFu on 2021-09-16
Do **any** BluRay players support commercial BluRay video playback with DRM?  For some reason, I didn't think this was possible under **any** Linux OS due to the BluRay cartel holding back all the DRM and keys. I found this:
> How to Play (Some) Blu-rays on Linux with VLC

Blu-rays are a bit more complicated. While there are technically paid DVD players you can purchase for Linux, **_there&#8217;s no officially licensed way to play back Blu-rays on Linux._**

MakeMKV, a commercial tool to rip optical media, is claimed to work.  I've used it a few times with DVDs, but found it cumbersome. I never used the BR capabilities.  I personally think BR is broken by design and don't/won't have any of that hardware in the house. Not everyone can make that choice. I'm fortunate. There's a bunch of hardware and software I won't allow in the house, on the network.

If you can live with using BluRay as a data-only format, not for DRM-Video, then I don't think it really matters. There are a number of BR writers. Any Linux-Hardware list should have some.

---

### Post by satimis on 2021-09-17
> **TheFu said:**
> Do **any** BluRay players support commercial BluRay video playback with DRM?  For some reason, I didn't think this was possible under **any** Linux OS due to the BluRay cartel holding back all the DRM and keys. I found this:

MakeMKV, a commercial tool to rip optical media, is claimed to work.  I've used it a few times with DVDs, but found it cumbersome. I never used the BR capabilities.  I personally think BR is broken by design and don't/won't have any of that hardware in the house. Not everyone can make that choice. I'm fortunate. There's a bunch of hardware and software I won't allow in the house, on the network.

If you can live with using BluRay as a data-only format, not for DRM-Video, then I don't think it really matters. There are a number of BR writers. Any Linux-Hardware list should have some.
Thanks for your advice.

I'll only use the BluRay Writer reading music CD, VCD and Video DVD, converting them to mp3 files and mp4 files respectively.  I won't use it to burn discs.

My old DVD Writer is still working.  There is no problem converting music CD to mp3 files running VLC.  The only problem is converting video discs, VCD and DVD, to mp4 files on VLC, some of them with good result and others with ghost video, unclear.  I don't know whether the bad result comes from the old DVD Writer or from the discs.  Especially those DVD video discs converted from VHS cassette tapes.  They are done by the shop specialized in converting VHS cassette tapes to DVD.

For such a reason I consider whether a new BluRay Writer will read the discs better?

Regards

---

### Post by TheFu on 2021-09-17
Optical media is a digital format.  Read errors should be corrected by the hardware and will show up in system logs.  I would suspect the media first, before the drive doing the reading, unless the drive has a history of failing to read.  They do wear out - moving parts have that problem.

I doubt "ghost video" is anything except a bad transfer from a bad source (VHS) or failure to remove copy-protection like macrovision.

I use **vobcopy** to ... er ... copy the VOB files off DVDs, but haven't used that technique in a few years.
I've never seen a commercial VCD. They never caught on here.

For video conversions to mp4 containers, I'd use handbrake.  Internally, it uses ffmpeg. I've always found vlc confusing for anything except media playback. I use vlc on Android on a tablet to connect into a plex/jellyfin server and present DLNA media.

I cannot say if BR hardware will be better.  I remember that computer DVD players/readers sometimes had problems reading CDROM media because the laser was so much smaller than the grooves of the CD media.  Would the same be true with BR and DVDs?  Blue lasers (actually violet) are much smaller (higher frequency: 405nm) than the red lasers used by DVD and CDROM readers. [https://en.wikipedia.org/wiki/DVD#Disc_quality_measurements](https://en.wikipedia.org/wiki/DVD#Disc_quality_measurements)

---

### Post by satimis on 2021-09-17
> **TheFu said:**
> Optical media is a digital format.  Read errors should be corrected by the hardware and will show up in system logs.  I would suspect the media first, before the drive doing the reading, unless the drive has a history of failing to read.  They do wear out - moving parts have that problem.

I doubt "ghost video" is anything except a bad transfer from a bad source (VHS) or failure to remove copy-protection like macrovision.

I use **vobcopy** to ... er ... copy the VOB files off DVDs, but haven't used that technique in a few years.
I've never seen a commercial VCD. They never caught on here.

For video conversions to mp4 containers, I'd use handbrake.  Internally, it uses ffmpeg. I've always found vlc confusing for anything except media playback. I use vlc on Android on a tablet to connect into a plex/jellyfin server and present DLNA media.

I cannot say if BR hardware will be better.  I remember that computer DVD players/readers sometimes had problems reading CDROM media because the laser was so much smaller than the grooves of the CD media.  Would the same be true with BR and DVDs?  Blue lasers (actually violet) are much smaller (higher frequency: 405nm) than the red lasers used by DVD and CDROM readers. [https://en.wikipedia.org/wiki/DVD#Disc_quality_measurements](https://en.wikipedia.org/wiki/DVD#Disc_quality_measurements)
Thanks for your further advice.

The video on my VHS cassettes were transferred from V8 cassettes.  The video were captured by me with Sony V8 Video Camera during my travel world-wide in the past.  There is no copy-protection.  I have about 10 VHS cassettes and haven't played them for long time because without a player.  

I'll receive another DVD disc next week from the shop responsible for converting another VHS cassette.  I'll test converting the video on the DVD disc to mp4 file running HandBrake, reading on my old DVD Writer.  I'll come back later.  There is no urgency for me to get a new BluRay combo burner.

My aid is to restore the video on the VHS cassettes.  I still have the original V8 cassettes but doubt whether they can work?

Up-to-now I have no problem converting the music CDs to mp3 files.  I have more than 100 music CDs to convert to mp3 files.  It is for storage only.  I still need music CDs to feed my Hi-Fi set.

Regards

---

### Post by satimis on 2021-09-20
Hi TheFu,

This is my first test on Handbrake.

**[COLOR="#FF0000"]Step-1[/COLOR]**
Create Ubuntu20.04.3 VM/Client of VirtualBox

[COLOR="#FF0000"]**Step-2**[/COLOR]
**Install Handbrake according to following document:-**
**[COLOR="#FF0000"]Linux – HandBrake – Copy a DVD to MP4 or MKV file[/COLOR]**
[https://www.tweaking4all.com/video/rip-dvd-blu-ray/linux-handbrake-copy-a-dvd-to-mp4-or-mkv-file/](https://www.tweaking4all.com/video/rip-dvd-blu-ray/linux-handbrake-copy-a-dvd-to-mp4-or-mkv-file/)
[B][COLOR="#FF0000"]
Step-3[/COLOR][/B]
Download Video from a DVD disc to the Download folder of VM:-
**VIDEO_TS - name of the video**
**on Terminal:**
$ ls Videos/VIDEO_TS/```

VIDEO_TS.BUP  VIDEO_TS.VOB  VTS_01_0.IFO  VTS_01_2.VOB  VTS_01_4.VOB
VIDEO_TS.IFO  VTS_01_0.BUP  VTS_01_1.VOB  VTS_01_3.VOB

```

**[COLOR="#FF0000"]Remark:[/COLOR]**
The DVD video was ripped on a VHS cassette by a shop specialized converting VHS/V8 cassette to DVD

**[COLOR="#FF0000"]Step-4[/COLOR]**
Start Handbrake
-> Open Source -> Video folder, select "VTS_01_1.VOB" on its folder
-> Start converting it to VTS_01_1.m4v
(pls see attached screenshot_summary.png)

**[COLOR="#FF0000"]Step-5[/COLOR]**
After finish, rename VTS_01_1.m4v as VTS_01_1.mp4
and
Open VTS_01_1.mp4 with Videos

Comparing the quality of VTS_01_1.mp4 with the mp4 video ripped on VLC, there is not much difference on quality.  Part of the video is not very clear.

Is there any method to rescue the quality of the video?  Thanks

Regards

---

### Post by TheFu on 2021-09-20
The quality should be imperceptible from the source - that being the VOB file.  If the VOB file(s) are junk, fix that.
Running CPU intensive programs like video transcoders inside a VM isn't a good idea.  For testing, it is fine, but not long term.

---

### Post by satimis on 2021-09-20
I have played the original video file "VTS_01_1.mp4" (size-300.6MB) on Videso Player.  Certain sections are very clear but other parts of the video are blurry.  I ran OpenShot to cut out a section of the blurry video and made following tests on OpenShot.
[B][COLOR="#FF0000"]
Test-1[/COLOR][/B]
Simple Settings:
Profile:  MP4(h264)
Video Profile: HD1080p60fps(1920x1080)
Quality:  High
Export Video file - VTS_01_1_01a.mp4 (size 620.8MB)

[COLOR="#FF0000"]**Test-2**[/COLOR]
Profile:  MP4(mpeg4)
Video Profile: HD1080p30fps(1920x1080)
Quality:  High
Export Video file - VTS_01_1_01b.mp4 (size 486.4MB)
[B][COLOR="#FF0000"]
Test-3[/COLOR][/B]
Profile:  MP4(h.264)
Video Profile:  HD720p60fps(1280x720)
Quality:  High
Export Video file - VTS_01_1_01c.mp4 (size 621.8MB)

There is not much difference on the test results.  The video is still not clear.

Then I started searching on Internet and found following articles:-

1)
How to Fix a Blurry Video For Good
[https://www.techsmith.com/blog/video-blurry-techsmith-tips/](https://www.techsmith.com/blog/video-blurry-techsmith-tips/)

2)
Repair Your Corrupted Videos and Photos
[https://repairit.wondershare.com/](https://repairit.wondershare.com/)

3)
How to Fix a Blurry Video on Computer
[https://recoverit.wondershare.com/video-repair/how-to-fix-a-blurry-video.html](https://recoverit.wondershare.com/video-repair/how-to-fix-a-blurry-video.html)

Unfortunately all of them work on Windows.

I have Windows10 VMs.  If I can't find a solution working on Linux environment then I'll start the test on Windows.

Comment and suggestion would be appreciated.  Thanks

Regards

---

### Post by TheFu on 2021-09-20
A DVD isn't an mp4.  That is not the source. 
DVDs are stored as mpeg2 VOB files.  THAT is the source. It the original is blurry, there's nothing to be done. Cannot be fixed.

I use vobcopy to get the vob files off the DVD, then use handbrake to transcode to h.264 with a CQ of 19.  this should reduce the file about 75% in size with no difference in playback quality.  The h.264 gets put into an MKV container, but it can be put into an mp4 container if you like.  mp4 is just more restrictive on the video/audio codecs allowed. MKV can hold pretty much any video, audio, subtitles, captions, and text files in the same container.  Having multiple video, audio, subtitles is very common.  I have a few with 1 video tracks, and over 10 audio and 10 caption tracks.  Players can pick which tracks - 1 of each - to be displayed during playback.

h.264 is probably the best choice for 366-576p resolutions.  For 720p and higher, HEVC (h.265) will be more efficient, but the supported players are fewer and more CPU is needed both for encoding and decoding.  h.265 (the family HEVC and AVC1) is what the world broadcasters have selected for 4k video both broadcast and streamed.

But it all comes back to the source - if it is crap, then you'll never have anything better by transcoding.

---

