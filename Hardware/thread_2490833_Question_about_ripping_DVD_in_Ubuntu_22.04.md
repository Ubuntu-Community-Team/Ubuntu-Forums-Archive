---
title: "Question about ripping DVD in Ubuntu 22.04"
date: 2023-09-17
forum: Hardware
---

### Post by cedric9 on 2023-09-17
I know that this isn't really an Ubuntu question, but I'm hoping to get some general advice anyway.


Several years ago I took my home DVD movie collection ripped them into AVI files, and then stored them on USB thumb drives.  I did this because it takes up less space in our front room, and it was more convenient to just leave a thumb drive plugged into our TV, so that my wife easily watch her favorite workout videos.  I ripped most of my DVDs between 2006 and 2012, and back then I was using a different PC with Windows XP as the primary OS.  


Of course flash forward a few years, and now I find that some of the thumb drives I put my movies on are starting to fail. 


Fortunately I still have most of my old DVDs in boxes in the back closet, but I cannot seem to find a reliable process to rip them into AVI files under Ubuntu.  The closest thing I have had to success thus far, is to use MakeMKV to rip my DVD into an ISO file, and to store that file on my computer's hard drive.  


However, I cannot seem to a method for ripping either my original DVDs, or the ISO files I have created, into AVI files which my TV can understand. Also, the interesting thing about this is that I know that I ripped some of these very same DVDs back in the mid 2000s using DVD Decrypter and Auto Gordian Knot (Under Windows XP) but I cannot seem to do very much with them using MakeMKV and OGMRip. 


Any info greatly appreciated, below is my system information.  Also, in spite of the fact that I've been using Linux for several years, I'm still pretty much a newbie at it. 




Operating System: Kubuntu 22.04
KDE Plasma Version: 5.24.7
KDE Frameworks Version: 5.92.0
Qt Version: 5.15.3
Kernel Version: 5.15.0-83-generic (64-bit)
Graphics Platform: X11
Processors: 4 × Intel® Pentium® Gold G5400 CPU @ 3.70GHz
Memory: 7.7 GiB of RAM
Graphics Processor: NV138

---

### Post by TheFu on 2023-09-18
**TL;DR Version**
As for ripping commercial DVDs, there are many ways to do it.  To rip and transcode at the same time, I'd use handbrake.  [https://handbrake.fr/](https://handbrake.fr/) It is in the repos.  

To deal with the DRM from the DVD, [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) explains.  After installing the library, most video tools will find it and make use of it automatically. That goes for handbrake too.  I've never used handbrake to directly read a DVD. I've always used vobcopy to "rip" the DVD separately, then point handbrake at that ripped directory structure with all the VOB files.

Changes are, for DVDs, you'll want to use mp4 + h.264 video + AAC audio.  This is the most supported format in the world today.

AVI isn't the best container to use, but if that's all your TV supports, fine.  AVI + xvid + mp3 is probably the best choice for a TV from 2008. For a TV from 2012 and later, go for mp4 + h.264 video + AAC audio.

**Longer Version**

MKV is the most flexible container and widely supported., 2nd would be .mp4.  Again, these are container formats.  The thing that holds the video and audio and other information for playback, like captions or subtitles or alternate audio tracks - say you would like to have English and Spanish audio. Put both audio tracks into the same container file.

For DVDs the highest quality rip would be either mpeg or h.264 video codecs.  Nearly all playback devices support both, with h.264 having better support from the cheap streaming sticks. Older Chromecasts don't support mpeg2 video, but h.264 is fine.

For audio encoding, there's mp3, AAC, vorbis, FLAC, and a few other, less popular formats.  Most DVDs have AC-3 (5.1) and mpeg2 stereo audio. Sometimes there is Dolby and others is it DTS and sometimes they are just straight uncompressed PCM audio.  MP3 audio was used mainly for stereo audio and was popular around 2010 for videos.  Since then, AAC which supports multi-channel audio seems to be much more popular.  Depending on your specific playback device, Vorbis audio is great for compressed audio from a quality and multi-channel support standpoint.  

Every DVD is a little different, except that they all use MPEG2 video.  The audio and captions/subtitles can be in a few different formats, but since you plan to "rip" them anyway, you can standardize once you know the best option for your specific playback device.  

Step 1: Determine which container type your playback devices support.  Don't check just the TV, but also your tablets, computers, phones, and DVD/BluRay players.  In order, I'd prefer containers like this:
[LIST=1]
[*]MKV
[*]MP4
[*]AVI
[*]
[/LIST]

Step 2: Determine the video codecs supported by your playback devices.  The best video encoding depends on the resolution of the video.4k videos work better with h.265/VP9 encoding.  720-1080 can work best with mpeg2, h.264/VP8, h.265/VP9.  "Best" is a combination of file size and having zero visible artifacts. After all, a 10GB file without artifacts isn't really impressive when someone else can make a file that looks as good in 700MB. Depending on the content, different encodings work better. For fast action with explosions, at DVD resolutions (480p), mpeg2 or h.264 are the best video encoding choices. The best choice depends on resolution and the type of content. You'll need to experiment if you care at all.  If you don't want to bother with that, just use h.264. Artifacts can be addressed by using more bits in the encoding, which makes for larger file sizes.
[LIST]
[*]MPEG2 - 480p - 1080p resolutions with lots of explosions (most player devices since 2010 support it, except the older, cheaper, video sticks)
[*]h.264/VP8/AVC - 480p - 1080p resolutions (well supported by most devices since 2012)
[*]h.265/VP9/AV1 - 720p - 4K resolutions  More powerful players are required and before about 2021, few players supported this codec for playback.
[/LIST]
There are other choices like xvid and divx, but those are mostly dead these days. Both of these video codecs typically are put into AVI containers. AVI containers are mostly dead now.

Step 3: Determine the audio codecs supported by your playback devices.  Personally, I always use vorbis audio, but all my playback devices support it. It a high quality encoding and free to use by everyone without concern for patents. Some of my older player devices didn't support vorbis, so I was stuck using mp3, aac, or uncompressed AC-3/DTS/DD. But since those old devices were retired about 5 yrs ago, lack of support isn't important.  In 2010, I always used mp3, but I stopped doing that. For me, audio is 50% of the enjoyment in any video/movie, so I want the best quality with the most open format supported by large numbers of devices. Today, that is vorbis or aac.  For DVDs, I will keep the original AC-3 audio track in English with 5.1 DTS/DD, but I'll add a vorbis version with the same number of channels.  Also, if there are other languages in stereo, I'll transcode those to vorbis.  For DVDs, here are my preferences:
[LIST]
[*]AC-3 5.1 PCM/DD/DTS
[*]Vorbis at 192Kbps for all tracks, matching the number of channels as the source.  Many people, probably with Apple devices would need to use AAC instead.
[/LIST]

Step4: Subtitles.  I just copy over all the subtitles and captions that the DVD has in whatever format they have.

Ok, that's enough background.

Now, we have to put all that together for our needs. So, here are a few examples.
```
Chronicles_of_Riddick-dvd
| + Duration: 02:14:03.903000000
| + Title: Chronicles_of_Riddick
|  + Track number: 1 |  + Codec ID: V_MPEG4/ISO/AVC
|  + Track number: 2|  + Codec ID: A_AAC|   + Channels: 2
|  + Track number: 3 |  + Codec ID: A_VORBIS|   + Channels: 2
|  + Track number: 4|  + Codec ID: A_AAC |   + Channels: 6
|  + Track number: 5 |  + Codec ID: A_AC3|   + Channels: 6
|  + Track number: 6 |  + Codec ID: A_AAC|   + Channels: 2
|  + Track number: 7|  + Codec ID: A_AAC|   + Channels: 2
|  + Track number: 8|  + Codec ID: S_VOBSUB
|  + Track number: 9|  + Codec ID: S_VOBSUB|  + Language: spa
|  + Track number: 10 |  + Codec ID: S_VOBSUB|  + Language: fre
|  + Track number: 11  |  + Codec ID: S_VOBSUB

```
So that's a MKV file with h.264 video and lots of different languages, including the original AC-3 5.1 audio with alternate languages as subtitles.

Exercise DVDs tend to be less international, only have 1 audio track and may not have any subtitles.
```
| + Duration: 00:43:59.003000000
|  + Track number: 1 |  + Codec ID: V_MPEG4/ISO/AVC
|  + Track number: 2 |  + Codec ID: A_AC3|   + Channels: 6
|  + Track number: 3 |  + Codec ID: A_AAC|   + Channels: 2

```
So that's a MKV file with h.264 video and the original AC-3 5.1 audio with 1 AAC in stereo.  Both the video and since audio track could be put into an mp4 container which would be well supported.

You may note that I've completely ignored webm as a container.  That's because it is just MKV with restrictions. It is pretty useless.  MKV can hold pretty much anything - any video, any audio, any subtitles and, as far as I can tell, any number of tracks of any sort.  It is possible to put 10 video tracks with 20 audio tracks and 50 subtitles into a single MKV container.
I've completely ignored MOV containers too.

This is a little old [https://www.makeuseof.com/tag/avi-mkv-mp4-video-filetypes-explained-compared/](https://www.makeuseof.com/tag/avi-mkv-mp4-video-filetypes-explained-compared/) but was accurate in 2017.

---

### Post by cedric9 on 2023-09-18
> **TheFu said:**
> **TL;DR Version**
 For a TV from 2012 and later, go for mp4 + h.264 video + AAC audio.


Thanks for the information, I will try the above during this coming weekend.  In the meanwhile, I may have noticed another solution which I was overlooking before.  My DVD player, which I have reconnected to the TV, also has a usb port on it, so I'm wondering if the USB files which I created with MKV would be recognized by my DVD player, if I were to copy them onto a USB thumb drive?  Anyway, this will have to wait for the weekend.  Thanks again for the information, I'm going to have to read it once or twice to make sure that I thoroughly understand it.

---

### Post by ajgreeny on 2023-09-18
Yes, handbrake is the way to go.
I have used it quite a lot and even on my 10 year old desktop machine it works very well, if a bit slowly when encoding.

I don't encode to mkv using h.265 but have stuck with h.264 as using 265 spikes my cpu usage right up to 100% when playing/transcoding, particularly when using Emby-Mediaserver to stream to my smart-TV, and I do sometimes still use mp4 as the output file-type which always seems to work well, though I prefer mkv if I can use it.

---

### Post by TheFu on 2023-09-18
> **cedric9 said:**
> Thanks for the information, I will try the above during this coming weekend.  In the meanwhile, I may have noticed another solution which I was overlooking before.  My DVD player, which I have reconnected to the TV, also has a usb port on it, so I'm wondering if the USB files which I created with MKV would be recognized by my DVD player, if I were to copy them onto a USB thumb drive?  Anyway, this will have to wait for the weekend.  Thanks again for the information, I'm going to have to read it once or twice to make sure that I thoroughly understand it.

Different players have different capabilities.  I wouldn't expect any DVD player to be able to play files from USB storage of any sort.  I think the USB is used to update firmware, nothing more, for most of those players.  If you have internet, you can get a copy of the manual for the device and look up what the USB port can be used for AND which containers+codecs the exact TV model you have supports.

---

### Post by ajgreeny on 2023-09-18
> **TheFu said:**
> Different players have different capabilities.  I wouldn't expect any DVD player to be able to play files from USB storage of any sort.  I think the USB is used to update firmware, nothing more, for most of those players.  If you have internet, you can get a copy of the manual for the device and look up what the USB port can be used for AND which containers+codecs the exact TV model you have supports.
I have an LG dvd player which itself has a USB port and allows playback of video files on a flash stick, though I've used it only once and I can't remember what limitations on file types that has but I suspect that I was using mp4 with h.264 but no idea about the audio codec as it was far too long ago.

Maybe that's not what you meant by DVD players not being able to play USB storage but I throw this out ànyway just for full information.

---

### Post by SeijiSensei on 2023-09-18
Some DVD and TV manufacturers only support a limited set of protocols. Sony has been especially bad in this department. As TheFu says, encoding to mp4+h.264 video+aac audio generally runs on most anything. Matroska (.mkv) files may be totally unrecognized, or even if the file format is recognized, the codecs used may not be supported. H.265 video support has been spotty.

---

### Post by cedric9 on 2023-09-25
Well, it seems that no matter what I do, neither my television or DVD player are willing to accept any type of file format other than an AVI file. Neither of them will play an MP4 or an MKV file. I tried using VLC Media Player to convert an MKV file into an AVI file, but the end result was pretty terrible.  Looks like I will have to put this on the back shelf for a while.

---

### Post by Tadaen_Sylvermane on 2023-09-26
I don't rip entire ISO files. Just the main title with MakeMKV then compress via handbrake. I've had the occasional disk where handbrake alone failed. The Makemkv / Handbrake combo has failed exactly once out of 3k + disks so far.

What you can do is get Amazon FireTV or some thing and put kodi on it? I keep my movies on my server and just run from that. It's not as easy as direct file access but it's a nicer interface. Does require some setup though because the firetv sticks  don't have much onboard storage. The thumbnails file can get big fast.

You could also look into Jellyfin. For my purposes it was no good but it does work, and it's an app on almost any android device. Probably could load into a Fire tv as well. If you have machine you can leave running the Jellyfin Docker is perfectly good for it.

---

### Post by SeijiSensei on 2023-09-29
> **Tadaen_Sylvermane said:**
> What you can do is get Amazon FireTV or some thing and put kodi on it?
Most modern TVs support the DLNA protocol out of the box. My former LG did, as does my new Hisense with Google TV as the OS. Roku sticks also offer this option. I have everything on a small server with a large attached storage device. I use minidlna which is simple to set up and works with every DLNA client I've thrown at it.

---

### Post by TheFu on 2023-09-30
I have a privacy concern over any "smart devices", especially TVs and streaming devices and cameras and smart-phones/tablets.  The FBI recommends those things, if you must have them at all, always be put onto a separate subnet and blocked from accessing the rest of your network. [https://www.fbi.gov/news/stories/cyber-tip-be-vigilant-with-your-internet-of-things-iot-devices](https://www.fbi.gov/news/stories/cyber-tip-be-vigilant-with-your-internet-of-things-iot-devices)  For most people, this would be fine, since they don't have network storage or stream from other devices on their LAN. It never crosses their minds. 

Alas, we are Linux people, so home networking is second nature to us.  Also, we tend to understand privacy implications a little more than normal people who can't be bothered.  It isn't always easy to attain privacy, especially when you know the dirty secrets.  Almost all commercial streaming devices and streaming services are stealing our data without EXPLICIT consent and selling that data to Facebook, Google and other "data brokers.  While it is next to impossible to be completely free from these things, we can muddy the waters, feed them l90% less data and feed them bogus stuff too, so their profile on every user in the household is wrong.

The first step is to not help feed them data from your playback and viewing devices.  To that end, here's my attempt at doing that:

My home setup for videos is this:

[LIST=1]
[*]Good enough Jellyfin server. It is on the network and runs 10 VMs and 10 linux containers while also performing as an NFS, Calibre, mpd, and a few other things "server".  Oh, and with jellyfin, it can be a tivo-like DVR thanks to Silicon Dust HDHR network tuners.  In short, this is the media server, but does much more.  DLNA and Jellyfin protocols are supported.  DLNA doesn't have any idea about "users", but Jellyfin does.

[*]Wired networking to the rest of the house. When it comes to streaming media, wired GigE connections make a noticeable difference when compared to spotty wifi. For my $day_job years ago, I designed and technically oversaw a corporate wifi deployment to over 1200 locations.  Wifi is junk and should be avoided.  To bridge my upstairs and downstairs networks, I use PowerLine networking, though if I were doing it against today, I'd use MoCA coax networking instead to get wired 2.5Gbps connections.

[*]Raspberry Pi v2/v3/v4 "playback" devices.  These all run OSMC, which is an optimized version of Kodi to play content. That content usually comes from the Jellyfin server. There are both DLNA and Jellyfin "renderers". They can also be a DLNA "Controller."

[*]Jellyfin app on a tablet/smartphone that uses a VPN to access the Jellyfin server to select what to play and where to play it.  Sometimes, that playback is to a Pi or the local tablet.  While it can stream to the Roku though some fancy firewall forwarding, I decided NOT to feed the Roku-privacy-sucking-program/device even more data than they get just from our DRM'd streaming.
[/LIST]

There you have it.  Each of the Raspberry Pis also has a MCE-RC6 remote control, so if a tablet isn't nearby, the remote is.  There's a pre-configured RC6 remote control config file included with Kodi/OSMC, so setting it up can be done through the setup GUI or deleting a symlink and creating a new one so the rc6.conf is used for the lirc.conf file. Knowing that means getting a remote that works easily is about 20 seconds over ssh.  

It is also possible to tell Kodi about NFS storage and let it scan all the media without jellyfin being in the middle. There are pros and cons to working this way.  This is actually how I started out.  A $100 computer with a spare 300GB HDD running ubuntu + kodi directly connected to the HDMI on a TV.  These days, a Raspberry Pi 4 would be a better choice, I think, because the r-pi v4 has built-in video decoding for h.265, h.264, and mpeg2, which should cover pretty much anything anyone makes these days and the Pi4 is fast enough CPU to handle older media like mpeg4, divx, xvid, and those odd containers like mov, flv, avi.  AVI used to be extremely standard. I used it for divx/xvid + mp3 audio. At the time, it was amazing, but h.264 blows that away and we can get 4TB HDDs for $50 at this point, so storage isn't the same limitation now like it was in 2010.

DLNA is an industry standard. There are servers, controllers and clients that can be on 1, 2, and/or 3 different systems. Mix and match as you like.  I tend to use the Jellyfin "server" above as the DLNA server (when I use DLNA, which isn't very often), the OSMC raspberry Pis as "renderers" and a smartphone or tablet as the "controller".  

Having a centralized media server provides a way to start a movie in one room, then move to another to finish it. The restart pick up where we left off.  It is also nice to see all the information about a series, episodes, and perhaps look up other media with the same actor in your library.  Want a Spaghetti Western Weekend?  That's easy. Just look for Clint Eastwood + Western ... Here's the list:
[LIST]
[*]Ambush at Cimarron Pass
[*]A Fistful of Dollars
[*]For a Few Dollars More
[*]The Good, the Bad and the Ugly
[*]Hang 'em High
[*]Two Mules for Sister Sara
[*]High Plains Drifter
[*]The Outlaw Josey Wales
[*]Pale Rider
[*]Unforgiven
[/LIST]
Probably more than anyone would watch in a weekend.  Perhaps 2 weekends ... when the snow gets deep outside?

Since our Jellyfin server also records broadcast TV, anyone can schedule a show to be recorded from almost anywhere in the house.  And they can watch that show live or wait for it to get placed into the "TV Shows" area in Jellyfin with all the commercials removed.  Remember the TiVo "season pass"?  That's easy.  Choose a show, in the recording details, pick a channel so you don't get reruns from other stations, and see how that goes.  If you like, especially for PBS stuff, picking a time to record can help avoid prime-time conflicts.  NOVA and Frontline are shown during primetime, but then again overnight, so our season pass records them overnight.

We don't even watch sports live anymore. Marking/removing commercials is pretty easy thanks to comskip, though it does take about 30 seconds per recorded show to validate + remove the commercials.  It is possible to have a recorded show marked with fairly accurate commercial break locations and play that back without removing the commercials, just using an "EDL" skip file (comskip).  But this won't matter if you only have DVD content.

Kodi/OSMC can accept straight DVD copies with the full disk structure maintained. That means removal of the copy protection, but all menus, captions, subtitles, languages, and special features left. No transcoding done.  Use **vobcopy** to do that, if it is your interest. I think all the popular media server software supports having full DVD copies, but I have to admit, I've never, ever, used that.  I'm willing to try, if there is interest.

Why Jellyfin and Kodi?  Privacy.  All the other media players/servers that I know "phone home" with every button you press, every song you listen to, every video/dvd/show you play.  It is their business model to sell you out.   Jellyfin and Kodi don't phone home to anyone, though if you access internet sites for metadata retrieval (song/album information, DVD, Episode data), then those individual services will see your query.  If you do a massive load of files, they will know your entire library due to all the HTTP GET requests from 1 IP.  Eventually, that data will probably be sold to Google and Facebook.

I still can't believe we actually pay for Roku devices with all the spying they do.  I ran a Plex Server for a few years and it was constantly phoning home almost as much as the Roku does.   We have a Roku to avoid 99% of DRM hassles that Kodi and Jellyfin have.  Bought the Roku when a streaming service we paid for kept changing and blocked Linux clients.  The Roku is about 7 yrs old now and plays back most DRM streams, but not all. I suspect in the next 3 yrs, it will stop working as more and more streaming services only support h.265 video, which our old Roku just can't do.  Sadly, Roku only makes 2 very expensive models with wired ethernet, which I consider mandatory. We avoid wifi here for a number of reasons, mainly because it will never actually be secure. I'm positive about that.

I won't have any smart TV connected to any network in the house. Today, we don't have a smart tv and I can't remember the last time we actually turned on the TV - must be since May or so.  We are projector people and have 3 projectors around the house. These don't have networking connected, though one of them does use Android as the OS on the projector. It is a small, quiet, travel projector that we use mostly as a backup when the bulb on our main Epson needs replacement.  Going from a 120inch screen to a 37inch or 50inch screen is quite the let down, but living without it for the 4 days that shipping a new bulb requires is good for our humility.  Actually, I think it is about time for new bulb again, so I should order one now before football post-season.

Anyway, there you have it.  I didn't start out with all this complexity.  I started with a $100 media player that could stream and have local media files connected by USB.  When the pre-bought commercial players didn't support all the types of media, I moved to Kodi/XBMC which could playback nearly anything.

Jellyfin does a specific, stand-alone, client just for a Pi hardware, but the player interface is off just a little for my tastes.  Whereas the Kodi interface provides good control over subtitles, subtitle sizes, colors, ± delays, audio tracks, etc. Maybe I should look at the jellyfin standalone app again? For now, I'm using the Kodi Jellyfin addon instead.

Of course, none of these things are perfect.  But we sometimes have problems with our roku playing streams too, so nothing is 100% "just works" these days.

---

### Post by Tadaen_Sylvermane on 2023-09-30
> **SeijiSensei said:**
> Most modern TVs support the DLNA protocol out of the box. My former LG did, as does my new Hisense with Google TV as the OS. Roku sticks also offer this option. I have everything on a small server with a large attached storage device. I use minidlna which is simple to set up and works with every DLNA client I've thrown at it.

True enough. I usually forget the DLNA stuff. I had searched for a library program and ended up with Kodi. DLNA was never on my radar. But it does work very well.

---

### Post by cedric9 on 2023-10-08
Well, I just wanted to report that I've finally had some success with my DVD to AVI project, and I wanted to share what I did in case anyone else stumbles across this thread in the future. Also, I realize that some of my steps may have been unnecessary, but here is what I did anyway.

1.  I took the DVD I wanted to rip and converted it into an ISO filed stored on my desktop's local hard drive. 
(I did this, because I'm guessing that my DVD drive might be slowing due to age, and maybe it was interfering with the ripping process.)

2.  I mounted the ISO image so that it showed up in File Manager as a drive.

3.  Launched HandBrake, open the ISO, and made the below changes to a few settings:
- Changed Preset from Fast 1080p30 to HQ480p30 Surround.
- Change frame rate to same as source.
- Video Codec H264 (x264)
- Set to Constant Quality
- Set quality slider bar to 20
- Under audio I removed the second track, but not sure if that was necessary.

4. Saved output file as an MV4 file, but later renamed it to give it an MP4 extension.

5.  From within File Manager, used the open terminal option within the directory where the new MP4 file was stored, and entered the below command in the terminal:
ffmpeg -i LESLIE1.mp4 -q:v 2 Leslie1.avi

6. Copied new AVI file to USB thumb drive, and my old TV is happy with it. 

I want to thank everyone who tried to help me with this, but sometimes I'm one of those slow people who just has to figure things out the hard way.

---

### Post by TheFu on 2023-10-09
You are transcoding twice. Each with a slight loss of quality.  If you want the output to be an xvid avi file, why not just directly transcode from the DVD to that format?  avidemux would be the tool I used for that.

Also, renaming extensions isn't needed.  That's for your desire, not ffmpeg. It will look at what's inside the file and decide.

You can use **mediainfo** on the resulting avi to see the final format you ended up with.  No reason to use handbrake if you are just going to re-transcode again. Use vobcopy to get the ISO off the DVD, then use ffmpeg (or avidemux) directly to make the desired avi file.

---

### Post by cedric9 on 2023-10-09
> **TheFu said:**
> You are transcoding twice. Each with a slight loss of quality.  If you want the output to be an xvid avi file, why not just directly transcode from the DVD to that format?  avidemux would be the tool I used for that.

Also, renaming extensions isn't needed.  That's for your desire, not ffmpeg. It will look at what's inside the file and decide.

You can use **mediainfo** on the resulting avi to see the final format you ended up with.  No reason to use handbrake if you are just going to re-transcode again. Use vobcopy to get the ISO off the DVD, then use ffmpeg (or avidemux) directly to make the desired avi file.

Well, I knew that I wasn't doing a few things correctly, and I appreciate your information.  I will take a look at avidemux this coming weekend.

---

### Post by cedric9 on 2023-10-09
I wanted to quickly add that the below command is what I actually had to use in order to get the AVI file to play on my TV.

sudo ffmpeg -i Leslie1.mp4 -c:v libxvid -q:v 5 -q:a 5 Leslie1.avi

---

### Post by TheFu on 2023-10-10
I've use **vobcopy** to rip the DVD files.
Then I'd use **ffmpeg** to convert each .VOB into an avi/xvid file.  No need for sudo with ffmpeg, BTW.  People overuse sudo and cause themselves more problems, which cause sudo to be used more and more and more until they trash their system.

Go directly from mpeg2 --> xvid.  That should make the process at least 50% faster and result in better quality, smaller, avi files.  Too bad the player doesn't work with h.264 directly, but that's to be expected with older hardware.

---

### Post by cedric9 on 2023-10-10
> **TheFu said:**
> I've use **vobcopy** to rip the DVD files.
Then I'd use **ffmpeg** to convert each .VOB into an avi/xvid file.  No need for sudo with ffmpeg, 

Very interesting.  Thank you for the information, this is starting to make sense now.

---

### Post by cedric9 on 2023-10-11
> **TheFu said:**
> I've use **vobcopy** to rip the DVD files.
Then I'd use **ffmpeg** to convert each .VOB into an avi/xvid file. 

I now have vobcopy and libdvdread on my system, and I would just like to ask a quick question regarding how to use vobcopy.

Assuming that the title of the DVD inserted into my ROM is, Step_Forward, and that I would like to use vobcopy to rip the DVD to a partition mounted at HD0-4, then would the below command be appropriate?  

vobcopy -m -i /media/Cire/Step_Forward -o /media/HD0-4

---

### Post by TheFu on 2023-10-12
No.
```
vobcopy -m -i /media/Cire/Step_Forward -o /media/HD0-4 
```
is not correct.  I don't have the program loaded here, so you'll need to check out the manpage to understand how the different options work.  My DVD collection was all ripped years ago.

Also, you probably want to create a subdirectory for each disc being ripped to be held. For example,  /media/HD0-4/Step_Forward/  For videos using VOB, you'll probably need to know the title number and use that to get the specific video.  VOB disks don't know anything about English titles for videos.  They just know a number from 1-99. For most discs, the longest video track will be the main title. I think vobcopy has a setting to rip the longest track.  However, some commercial videos know this and will ensure the longest track is the chapters, all out of order with a few extra to make certain it is longer than the real track you want.  Discs using this sort of DRM usually have 10+ tracks and may skip track numbers to add complexity.  Experience will teach this fast.

---

### Post by cedric9 on 2023-10-15
I just wanted to add that I seem to have found a couple of commands which will allow me to rip a DVD and encode it to an AVI file that can be played on my older TV.

1. Use below command to rip VOB files from DVD to hard drive,  
this will give you multiple VOB files from the DVD onto your hard drive:
vobcopy -i -l /dev/sr0 -o /media/HD0-4/WINGS_OF_WAX_VOB


2. Use the below command to combine the multiple VOB files into a single AVI file which will play on older TV and DVD machines:
ffmpeg -i "concat:WINGS_OF_WAX1-1.vob|WINGS_OF_WAX1-2.vob|WINGS_OF_WAX1-3.vob" -q:v 2 -q:a 2 /media/HD1-5/Movies/WINGS_OF_WAX/WINGS_OF_WAX.avi

This was a pretty good achievement for me, as I know virtually nothing about video codecs, and I know almost nothing about the command line environment, but with a little bit of trial and error, I seem to now have a process to once again rip my old DVDs.  BTW, the DVD I used in the above was released in the year 2002.

---

