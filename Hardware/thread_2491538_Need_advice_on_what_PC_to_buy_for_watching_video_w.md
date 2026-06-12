---
title: "Need advice on what PC to buy for watching video with current and future codecs"
date: 2023-10-12
forum: Hardware
---

### Post by n0c0d3 on 2023-10-12
Hi all,

I'm looking to buy a new PC. I like it to be future-proof to play video with codecs like HVEC, AV1, AV2 and h266 in VLC at higher speeds. Normally I watch documentaries at a speed of 150 to 185 % in VLC. My current PC can't even normally play x265 without green or grey blocking at normal speed and when stepping backwards or forwards in the location bar this normally results in loss of sound as well. With x264 I do not have any such issues at all. I'm looking for a PC that can normally handle the latest and foreseeable future codecs like my current PC handles x264, without grumbles. There seems to be still no hardware support for AV2 and h266, so the rest of the system has to be capable of handling those as well by software decoding without unwanted artifacts.

I already had some conversation with someone who regularly encodes video and who I respect very much for his knowledge of computers and video-encoding, and he recommended me a PC with at least 4 cores, 8 threads for h266 (VCC) at double frame rate, at least 8 GB RAM and then the clock frequency is not all that relevant. And he said I need AVX2 support, but for what I've seen that's supported by all modern CPU's.

I prefer a low basic power consumption as I normally keep my PC running 24/7 to seed torrents. I'm not a gamer and I do hardly ever encode video myself, apart from the occasional Handbrake encode with more or less default settings, but I don't need to buy a pc especially equipped for that. I understood that if I'd wanted to frequently encode video AVX-512 would be recommended I believe, but for me this seems to be not a necessity. Because of price and power consumption I prefer an onboard graphics card (so no separate/distinct dedicated GPU card). Besides that Nvidia does seem to have problems with Wayland, which seems to be the future of the graphics layer on Linux.

I've been trying to squeeze  information out of the Intel and AMD sites, but not all information is that easy to find, like what codecs are hardware-supported. According to my own assessment I'd need at least an AMD Ryzen 5700G or a 7700 to be sure and prepared for unknowns in the future. When it comes to Intel it would be at least an i5-12500, but better would be an i5-13600 or an i7-13700. The latter would probably be already be overdoing it a bit I guess. The Ryzen 7700 and the i7-13700 would I think already be more than I need and are already quite expensive. The guy I asked these questions was pushing me a bit towards the AMD Ryzen 7900 and 7950 or the i9-12900 and he was frequently talking about encoding video, which I hardly ever do, so I think for me this would be overkill, and I believe that these recommendations were more based on what he wanted to buy if he was going to buy a new PC than taking into account what I actually needed, so I found it hard to not get confused by this.

But when it comes to future codecs that will not be hardware supported, like AV2 and AV1 16 bit 4:4:4 (currently only used for editing but maybe in the coming years also used for general encoding?) that will not be hardware supported by any current system, then maybe a more 'high-end' system would be recommended?

I also have not really any clue as to what would be better, an intel or an AMD. The Intels have these P and E cores, which makes them less power hungry when not pushing them. This could be an advantage, but I don't know if it has any drawbacks or something.

Maybe someone has some more issues to consider and I hope people on this forum can advice me and help me figure out what system would be best for me to buy, for a reasonable price. I could afford the high end stuff if it's really recommended, but preferably not.

It's become quite a story, so I hope people have made it this far.

Thanks in advance for any advice.

---

### Post by TheFu on 2023-10-12
future-proof isn't possible.  
> handle the latest and foreseeable future codecs 
Reset your expectations.  It isn't possible.  Nobody can predict the future.  Often, especially for niche needs, there might be a few competitors that provide what you seek, eventually. It won't be with medium-cost hardware.  

The way to get reasonable priced hardware is to be 1 generation behind.  

I transcode videos almost daily and still use h.264 for this task. I plan to retire my last player that doesn't have sufficient CPU to support h.265 in the next few months, but I have no plans to replace a streaming box that I've had for nearly a decade until it stops working. It didn't support mpeg2 when I got it, only h.264. I'm not sure when, but mpeg2 support was added later. It will never handle h.265. Never.

You could always transcode the h.26x videos into h.264 over night and watch them a day later on your current hardware. That would be more cost effective as any new video encoding standards solidify.  Until **ffmpeg** supports it, I don't see it being widely used.  ffmpeg is THE standard for video encoding.  The VVC standard was just approved last month, so it will be some time, assuming the licensees aren't difficult.

Considering that I had to look up what h.266 was (never heard of it before your post), perhaps I'm the wrong guy ... or hardware isn't planning to support it. I still have a number of systems that don't support h.265 decoding, if that's any hint.

Google has adopted vp9 (based on h.265) and that avoids expensive patent licenses that most other vcodecs have.  If the people creating video codecs can't learn their lesson, they will be cut out from content encoding.

Found this from 2022:
> In terms of deployments, standards-based codec adoption involves a number of milestones, particularly for those such as VVC and EVC, which will likely require hardware-accelerated decoding on mobile and living room platforms. Royalties must be set, then chips must be developed and integrated into retail products for deployment and, sometime later, reaching critical mass.

The only way to "future proof" anything for the next 6 months is to buy the fastest, most powerful, CPU available with as much RAM as you can afford.  For a longer period, pray is the best answer I have.  Those two options aren't exactly economically efficient.

Just saw this: [https://www.phoronix.com/news/Mesa-23.3-HQ-AV1-Radeon](https://www.phoronix.com/news/Mesa-23.3-HQ-AV1-Radeon)  Be sure to review the comments.

---

### Post by n0c0d3 on 2023-10-12
Thanks for your reply. Yes, as the saying goes, making predictions is hard, especially when it concerns the future. That's why I was talking about the foreseeable future, and mentioned the codecs that I think are the ones to take into consideration. This h266 codec I believe is not going to be widely used because of its commercial patenting limitations, but the others may well be.

That discussion you linked to is interesting, but I'm not really sure if it's really important to me cause they're talking about encoding video. I'm not going to do that much. I'm going to do the decoding part and as far as I know this is something quite different when it comes to the cpu that's needed. Or am I wrong here?

And it's not that I've got much choice in what codecs the encoders/releasers use. I've just got to go along with what they produce. That guy on that docu-forum I visit throws all kind of codecs at us. He's trying to squeeze the size as much as possible while maintaining good quality and as most modern pc's can handle most of those codecs he sees no limitation to use them and there are not really all that many complaints about it. He mostly uses x265, h266 and AV1. He often explains why he uses what codec, it has to do with grain and noise, fast moving stuff and frame rates and such, but many of those technicalities are above my level of comprehension. I just want to be able to watch documentaries at high speeds without blocking and stuttering.

Still looking forward to more suggestions!

---

### Post by TheFu on 2023-10-13
If you are watching commercially created stuff, hosted by commercial sites, then you are right, the encoding vcodec cost probably doesn't matter much.  But if these videos come from "big tech", they are more likely to avoid paying the steep prices demanded by the encoders.  You do recall how h.264 was dying due to license costs both on the encoder and decoder side, right?  As a way to save their profits, the people behind it decided to make decoding free, but increased the charges for encoding.  

h.266 has learned that lesson, but they do see a way to charge more because their compression for higher resolution files is more efficient.  
h.264 is very efficient for DVD-quality videos.  The gains in h.265 for those resolutions isn't compelling, until pushed to the point where artifacts become common in the resulting video.

If you aren't archiving these videos, there's little reason to accept just what is presented.  Transcode them to whatever works for you.  For example, Plex and Jellyfin will transcode on-the-fly to what my players can handle, usually h.264 (using a x264 vcodec).  That removes worrying about player support for my needs. YMMV.

I don't know that I've ever seen AVC1 (I don't do bluray) and I'm positive that I've never seen h.266 anywhere.  A few months ago, I did see that google changed their default to vp9 AND I had to make changes to my workflows to force h.264 output.  A video chat/presentation/meeting site, switched from h.264 to h.265 a few weeks ago.  That broke one of my tablet's ability to use the site at all.  The people behind it were told about the issue and they decided that so few people were using a tablet from 2017 that it wasn't important.  I think about 3 yrs ago, h.265 support in hardware became common in android.  It is the low-end devices where these issues will matter most.

Again, you can always throw lots of CPU at problems to address issues.  Stuttering is probably related to the lack of maturity for newer drivers/code and will take a few years to resolve, if the market picks up.

Also, where in the world you are located will drastically determine what you are likely to see. Since I'm in the USA, our broadcast TV is still in mpeg2 format and attempts to move that to ATSCv3 have been delayed and will be delayed again - probably until after 2030.  ATSCv3 supports:
[LIST]
[*]    H.266/MPEG-I Part 3 VVC
[*]    H.265/MPEG-H HEVC
[*]    H.264/MPEG-4 AVC
[*]    MPEG-4 Part 2
[*]    H.262/MPEG-2 Part 2
[*]    VC-1
[*]    AVS3
[*]    AVS2
[*]    AVS+/AVS1-P16
[*]    AVS/AVS1-P2
[/LIST]
But I've only seen VC-1 and HEVC listed in local station trials.  The broadcasters and content creators are screwing up again here - trying to get encryption allowed. This has been delaying any hardware. The most popular tuners don't support encryption and cost about 5x more than the current ATSC tuners.  Don't know if you saw this, but LG has announced they are removing ATSCv3 support from their TV lines.  Govt making mistakes in favor of copyright groups is screwing regular people and businesses who would like to make the required hardware.  ATSCv3 doesn't even support HDR video.

OTOH, if you are in Europe, I vaguely recall they are adding the newest vcodecs to their standards, since it really is just 1 field that specifies which vcodec will be used. I can't imagine that field being smaller than 8-bits, so 255 choices.

What sort of documentaries are you viewing?  My library has many available, but most are very special interest or have been on PBS already.

---

### Post by n0c0d3 on 2023-10-14
Normally I watch from what I record from tv or download over torrent, mostly from the forum I mentioned, but there are many torrent sites. I'm in Europe and what I get from tv is mpeg2 as well as far as I know. But on torrent there's quite a variety of codecs in use, some even still use Xvid, others venture into AV1 and more modern codecs. I have no say in what those people use to encode. I just have to adapt to what's on offer if I want to watch something, just like you with your tablet and chat software.

I watch all kind of things. nature, science, socio-politics, history, whatever looks interesting. Sources can be BBC and PBS, but it's not limited to that.

---

### Post by Yellow Pasque on 2023-10-14
It's going to be hard to future proof for newer codecs where we don't know how prevalent they'll become and what resolutions will be common. Personally, I would focus on a system that gives good AV1 playback.
This will make it clear as mud:
[https://en.wikipedia.org/wiki/Video_Core_Next](https://en.wikipedia.org/wiki/Video_Core_Next)
[https://en.wikipedia.org/wiki/Intel_Quick_Sync_Video](https://en.wikipedia.org/wiki/Intel_Quick_Sync_Video)
(I guess I could link Nvidia PureVideo too, but you'd have to spend at least $200 to get a card with AV1 hardware decode, or else it's not a worthwhile upgrade over an iGPU for video playback. Plus, you said you preferred integrated GPU's and wanted to avoid Nvidia.)

Okay, I'll try to simplify.
On the AMD side, the Ryzen 5600G or 5700G should do what you want now. They'll playback 4k60 AV1 without issue, even without AV1 hardware decode. Prices for those CPU's and corresponding components (Socket AM4 motherboard, DDR4 RAM) are very reasonable since they are previous gen.
If you want to build around the latest tech, the Ryzen 7600 seems like it's ideal for your use case. A system with that (and AM5/DDR5) is going to cost a chunk more, but it will more provide some more power and give you AV1 hardware decode. Also, AMD has said they'll use Socket AM5 for a while, so you'll probably have the chance to upgrade the CPU down the line.

I don't know as much about the Intel side. I do know they change sockets frequently. I also know they're generally not as efficient as comparable Ryzens. "At least an i5-12500, but better would be an i5-13600 or an i7-13700" sounds about right. Even an i5-12400 should play AV1 efficiently.

Personally, I built a Ryzen 5600G system earlier this year. I haven't noticed any issue with video playback. And with the money I saved over the AM5 stuff, I bought a Scythe Mugen RevC cooler for it, because I'm neurotic about noise. It's wonderful.

---

### Post by TheFu on 2023-10-14
I'd have a hard time recommending AM4 sockets to anyone except budget shoppers at this point.  And I have 2 Ryzen 5600G systems here.  Upgraded one less than a year ago from a Ryzen 2600 to remove nvidia and get a 40% speed bump from the older Ryzen. No regrets. Kept the same motherboard and RAM, so it truly was just a CPU upgrade, nothing else.

Ryzen 7xxx is still in the premium price range. Anything with DDR5 will be for another year or so.  If you can put off any changes for a year (Fall 2024), then DDR5 RAM, motherboards and Ryzens should begin to get cheaper.  Then is when buying a Ryzen with AM5 socket will make the most sense, specifically if you get a higher-end AM5 motherboard which has better long term support and will be likely to get more firmware updates for newer Ryzen AM5 generations.  A chief reason to buy AMD CPUs is to get their onboard iGPUs AND be able to upgrade just CPUs for many years between different sockets.  Intel has this nasty habit of changing sockets every 12-24 months, making upgrades that don't include a new motherboard next to impossible.  For people like me, that means paying about 2x for any upgrade compared to an AMD upgrade.  Sometimes, Intel-based systems are really excellent deals and if you buy/build a system for 10 yrs of use, then it matters less and less.  OTOH, if you plan to chase video codecs and playback of newer types in GPU hardware support, that means you'll be upgrading every 2-3 yrs. It will get expensive.

BTW, both my systems have cases that are 15+ yrs old. One is actually from 1999 and held my first 2 CPU (not core) system.  Sure, they are each on their 3rd PSU and probably 5th (or more) motherboard+CPU, but upgrading just the parts that actually need upgrades really keeps costs down.  Until about a year ago, I was using a 25 yr old keyboard.  With some love, I bet it would work again.  I expect that keyboard will be working longer than I'm alive, it was built extremely well.  On the other end, I don't think I could accurately count the number if disks that have failed over the decades.  I can see 22 than need a few drill holes and potassium to ensure they *tell no tales*.  That's just the ones that are visible on shelves, not necessarily all that don't work or won't be used ever again.  I think there are some 300GB IDE drives inside a few old DVRs somewhere too. Need to pull those, see what's on them and give them the drill+NA too!  Perhaps next 4th of July.

Anyway, reusing parts from the prior system is a good way to keep costs down.

---

### Post by TheFu on 2023-10-14
I've added new silent Noctua fans to my systems for better and nearly silent cooling.  Having a fan pull air across 4 drives really reduces the temperatures, usually more than 10°C.

I need to look up how to encode AV1.  Just did a test with some streaming media. It is a 46min recording. Here are the transcoding results:
```

VCodec     WxH     VRate  ACodec  ACh Filename             Notes
------  ---------  -----  ------  --- --------           ------------------------
 h264   1280:720   59.94   MP4A   2   File-huge.mkv      # Source file
 h264   1280:536   59.94   VORB   2   File-long.mkv      # Handbrake h.264 transcode
 hevc   1280:536   59.94   VORB   2   File-hevc-hb.mkv   # Handbrake HEVC transcode
 hevc   1280:720   59.94   VORB   2   File-huge.hevc.mkv # ffmpeg medium HEVC transcode
 hevc   1280:544   59.94   VORB   2   File.hevc.crop.mkv # ffmpeg medium HEVC transcode, cropped


Sizes
------
2.6G    File-huge.mkv       # Source
585M    File-long.mkv       # Handbrake h.264 transcode
324M    File-hevc-hb.mkv    # Handbrake HEVC transcode
284M    File-huge.hevc.mkv  # ffmpeg medium HEVC transcode
268M    File-hevc.crop.mkv  # ffmpeg medium HEVC transcode, cropped

```

Note the resolutions. Handbrake makes cropping easy.  Cropping helps, a little.

Also, the size related to the time required to transcode.  I'm using **CRF=19.5** for all transcodes and all codecs. Basically, there are no visible differences and no artifacts in any of these that aren't also in the source.

The source is from a relatively cheap hardware video recorder that is limited to stereo audio.  File size is less a concern, it seems, for that recording device.
In general, I don't record at 1080i resolutions. Made that choice years ago and haven't revisited it. Perhaps I should. I do have poor eyesight, so higher resolution isn't likely to be "wow" to me.

---

### Post by TheFu on 2023-10-15
I spent a few hours yesterday running lots of other tests and have decided to transcode all new hidef recordings to HEVC.
Thanks for asking this question and getting me to look deeper.  This morning, I wanted to compare HEVC with AV1, but since my core system are running 
```
ffmpeg version 4.2.7-0ubuntu0.1
```
AV1 isn't supported by all my processing tools.

The ffmpeg included with Jellyfin /usr/lib/jellyfin-ffmpeg/ffmpeg has
```
ffmpeg version 5.1.3-Jellyfin
```
But I don't do extra processing using that system.

[ 30 minutes later]

So, I've been trying to get the jellyfin ffmpeg to use either libsvtav1 or libaom-av1 codecs.  Plagued by core dumps. Appears it isn't ready.  Maybe in a year, it will be solid?  Back to HEVC for transcoding.

---

### Post by n0c0d3 on 2023-10-15
@Yellow Pasque

Thanks for your advice. From what I've been able to figure out the Intel 11th generation and up support AV1 (both encode and decode), [https://www.intel.com/content/www/us/en/docs/onevpl/developer-reference-media-intel-hardware/1-1/overview.html](https://www.intel.com/content/www/us/en/docs/onevpl/developer-reference-media-intel-hardware/1-1/overview.html) from AMD the 7000 series does support AV1 decode, the "Raphael" from the wiki page you referred to, but no encode, but I'm not going to use that very much anyway, if at all.

But (your) 5600G plays it well without hardware decoding? That's encouraging. How much RAM do you have? And does AV1 play well on VLC at higher speeds,like 177 or 185%? Is your memory usage going up a lot, and the temperature? And can you easily jump from one place to another in the video without artifacts like slow (re-) starts, grey or green blocking and loss of sound or whatever? That would be interesting to know, because that would also say something about cpu's from newer series, they would only be better and also handle even newer codecs better (I assume) and I'm sightly inclined in that direction.




@TheFu

I don't really want to wait and gamble prices are going down. There's always something to wait for and I'm just in need of a new trustworthy pc. And I'm not really good at fiddling around with computers and continuously replacing all kinds of parts, so I don't think that will be much in my consideration.

I'm not really a pixel-devotee either I just want to see a good documentary on my ordinary pc-monitor, so I don't need very fancy video. But of course people with floor to ceiling and wall to wall screens will have different opinions.

But since you also have a 5600G, can you also answer the questions I asked Yellow Pasque above, about how it plays AV1? I assume there won't be much difference, but maybe you have different RAM size or something like that. I don't now yet what RAM to get, but I think 16GB will suffice in whatever system I'm going to buy.

Thanks for your support guys!

Edit:
Btw, if you could also do a test on h266 for me that would be great. I found some small test files here: [https://www.elecard.com/videos](https://www.elecard.com/videos)

---

### Post by TheFu on 2023-10-15
I don't use VLC.  I find it bloated.  I use mpv for video playback on computers that aren't media player devices.
Also, I don't have any AV1 content that I'm aware and is seems I can't create any either.

All hardware encoders seem to be crap compared to CPU-based encoding, until you get into higher-end commercial setups.  How bad of quality are you willing to accept? That's the real question.

AV1 isn't just 1 type of file.  There are lots a different profiles which can be modified by the people creating the initial encoding.  Some of those settings are better for streaming at the cost of quality. Use the **mediainfo** tool to get more details, especially for the video encoding options used. There are usually about 100 options, just for video encoding. I think you'll come to a better understanding for why 1 encoding can be a problem while others are not.  Just depends on the many different options available.  For example, AV1 can be encoded for size optimization, speed of encoding, or a "balanced" option which uses less time, but results in larger files.  There are also options to make decoding less CPU intensive or to optimize for streaming.  

Lots of options that deal with coloring, sharpness, how many blocks to consider etc.  h.264 uses a static, equal-sized grid.  

Newer video codecs have a more dynamic grid that changes based on how much data nearby is changing too.  Smaller grid areas are used where there is more action. Larger grids are uses where the amount of visual data changes are less.  All of these things go into how hard a video is to decode.  

If there are keyframes every second, then the file size will be larger, but going faster through it (fast-fwd or skipping ahead) will have fewer artifacts.  OTOH, keyframes every 10 or 30 seconds can drastically reduce file sizes, but skipping or forwarding through a file are usually limited to restarts on keyfames.  See the issues?

---

### Post by n0c0d3 on 2023-10-15
You're right of course. I'm aware that all video's are different. I added this link to some small video's on all kinds of formats in my previous post, but they're very static so I already doubted they would be of any practical use, but I did it anyway. When I play x265 things go relatively well when the video isn't fast moving, but when fast panning or when filmed from a car while driving on a road with trees at the sides my cpu goes berserk. And there's the screen size of course. The encoder I talked about uses different codecs for different video's, dependent on it's visual content, like noise, grain and movement and such, because codecs seem to handle different situations differently (if I understood well).

And I use VLC because it allows to play at different speeds. maybe mpv does that as well, but if I remember well (it's been a while since I tried), this player has no interface to speak of and only works with shortcuts. I don't mind a shortcut here and there, they can be quite handy, but that was a bit too much for me, so I ditched it.

---

### Post by Yellow Pasque on 2023-10-15
> **n0c0d3 said:**
> But (your) 5600G plays it well without hardware decoding? That's encouraging. How much RAM do you have? And does AV1 play well on VLC at higher speeds,like 177 or 185%? Is your memory usage going up a lot, and the temperature? And can you easily jump from one place to another in the video without artifacts like slow (re-) starts, grey or green blocking and loss of sound or whatever? 

I played with the AV1 ("City Hall") you linked to. I didn't notice much RAM usage increase (I have 32GB DDR4-3600). Both the 1080 and 4k play great at normal speed and you can skip around without issue. The 1080 used about 10% CPU and the 4k 15-20%
When cranking the playback speed up 1.5x or 2x, there is a restart delay if you skip around. It's not too bad with the 1080, but very noticeable with the 4k. CPU usage is around 25-30%.
FWIW, I went back and played the 4k AV1 in smplayer (uses mpv as a backend) and skipping around at double speed seemed much, much smoother than vlc.
As for temp readings, they go up with CPU usage like anything else. I looped the 4k file at 1.5x playback and my temp stayed below 38C. I don't think that's too useful info though. Like I said, I have a beefy aftermarket cooler. I have Turbo Boost disabled to save power. Also, my ambient temp is 62F at the moment, so that probably has an effect.

When it came to the VVC/H.266 file, my system (specifically, my ffmpeg version) doesn't support it yet.

> but I think 16GB will suffice in whatever system I'm going to buy.

Probably, and of course you can add more easily.

---

### Post by n0c0d3 on 2023-10-15
Thanks for the testing. These video's are quite static. so probably not the most representative for practical use, but maybe an indication for what to expect. So far so good I'd say. The temperature itself may not be a good representation, but the increase may be. Is the temp of the room where your pc stands 62F (17C)? That's quite cool. In summertime at 35C or so it may have been  60C or so with a more dynamic video? I'm just guessing, but it's still not all that alarming.

My pc is in a 20C room and the cores are 40C while I'm typing this with with base load. That said, my fan may need a bit of a brush. When I play a 1280x720 x265 video with normal movement at 177% the cpu (i5-4430 / 8 GB) load is at least 55% and 55C, increasing to 65% / 65C in more dynamic parts. Larger formats will be worse, and my experience is that then VLC may even crash in the dynamic parts. I can't play AV1 or h266.

So for AV1 a 5600G should do, the video is pretty well behaved so to speak (when skipping and such), a 5700G would of course be better, but there needs to be enough RAM and cooling.

I think this gave me a more thorough insight in what to expect than I previously had. Thanks very much for that!

So my intermediate conclusion would be that I maybe better go one step up to be somewhat future proof, like the Ryzen 7600 or 7700, or Intel equivalent, but I'd have to get back to my comparison sheet for the numbers on those.

---

### Post by Yellow Pasque on 2023-10-15
Yeah, it's quite cool in here right now. 

> The temperature itself may not be a good representation, but the increase may be.

I think you're reading too much into that. It doesn't really tell you/us anything, other than the temperature goes up with CPU usage. That is not specific to video playback. Like I said, the most demanding test I did, with the 4k AV1 running at double speed, only pushed the CPU usage to about 30% maximum in htop.

---

### Post by n0c0d3 on 2023-10-16
Yes, I probably am. I'm always a bit wary of higher temperatures because when I watch video with these "advanced" codecs my problems with bad performance correlate with high cpu usage and high temperature. But 30% is absolutely not very much for 4K AV1 as far as I know, even though the video is quite static in itself. I think there's nothing in the way to get a Ryzen 5600G or 5700G at the moment, that's for sure. It's the "future proof" (as in foreseeable) that I'm still wresting with.

---

### Post by SeijiSensei on 2023-10-16
OK, I didn't read much of this conversation, but codecs and the like are software dependent. Yes, there are some video adapters that have built-in H.264 converters, but they're not needed any more. Most CPUs have enough power to display video.

Right now, my primary video PC device is one of these: [https://www.newegg.com/p/2SW-007T-00008](https://www.newegg.com/p/2SW-007T-00008)

Plays most anything I throw at it at full speed. Supports 4K resolution. mpv on this device plays an x265-encoded 2160p BD rip smoothly.

---

### Post by Yellow Pasque on 2023-10-16
> **SeijiSensei said:**
> mpv on this device plays an x265-encoded 2160p BD rip smoothly.

The graphics built into your CPU do HEVC hardware decode, so that's expected. See how your system does with the "City Hall" AV1 at 1080 or 4k: [https://www.elecard.com/videos](https://www.elecard.com/videos)

---

### Post by TheFu on 2023-10-16
> **Yellow Pasque said:**
> The graphics built into your CPU do HEVC hardware decode, so that's expected. See how your system does with the "City Hall" AV1 at 1080 or 4k: [https://www.elecard.com/videos](https://www.elecard.com/videos)

Mine stutters with the 1080 version, running full screen, normal speed, with mpv on a 20.04 system. it was pretty bad.
The VP9 video @ 1080 was smooth.
The h.265 video  @ 1080 was full of green blocks, which is odd since I've been using h.265+HEVC the last few days to encode stuff I'm archiving and it all plays great both on computers and on video playback devices like an ARM-based Kodi and 2022 Android tablet.
```
9.3M    CityHall_1920x1080.webm  - stutters bad
9.8M    TSU_1920x1080.mp4   - green blocks. Unwatchable
13M     UshaikaRiverEmb_1920x1080.webm  - smooth and looks good
4.8M    NovosobornayaSquare_1920x1080.mp4  - no codec recognized.
3.8M    SFTI_1920x1080.bin - no codec recognized.

```
My display is 1920x1200.
These are all 10 second clips, so besides being playable without defects/artifacts, the file size and CPU load are the next important aspects.  Being small, but not playing is useless.

I transcoded the TSU_1920x1080.mp4 through my ffmpeg settings (basically the medium preset) and the resulting file is nice, no green blocking, but larger than all the others.
```
23M     TSU_1920x1080.mp4.hevc.mkv
```

It would be really nice if rather than posting different videos with different codecs, they had the same video encoded with all the different codecs, so the comparison would be easier. There are video analysis tools that can compare specific frames to show the different results and if the original input file is available, differences from that would be extremely useful to gauge the overall quality of any encoding.  Apples to apples comparisons are always better than apples to peas comparisons.

---

### Post by n0c0d3 on 2023-10-17
I'm sorry for my late response guys.

@SeijiSensei
I've been looking at things like that and mini pc's, but they're really not what I'm looking for. Thanks for your advice anyway!

@Yellow Pasque
Likely that system SeijiSensei recommended does play AV1. I tested a City Hall  webm AV1 and even the 1080 worked in my browser and playback was good,  but cpu went up to over 55%, but the 2160 more or less stalled. But when  AV1 is wrapped in mkv then nothing will play it.
When I buy a new  system and there will be AV2 in several years from now, or even AV1 16  bit 4:4:4, then it will also fall back to software decoding as well. I  hope to be able to play that smoothly then.

@TheFu
Thanks for  your analysis. Strange the City Hall AV1 doesn't work for you when it  works for me though. The VP9 works for me as well and smoothly up to the  2160, which kind of stalls. I had never heard of AVS3 (the SFTI video)  before, neither has my pc. It's a no go.
The h265 TSU is very bad for me as well, but that's to be expected. Strange this one is bad on your system though. How much is your RAM?


Thanks again for your support guys.

---

### Post by TheFu on 2023-10-17
Playing videos doesn't take much RAM.  That's the point of encoding.  I have 32GB and on the system I was running it, it is seldom strained, even during encoding.

```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi       **7.4Gi  **      17Gi       126Mi       6.3Gi        22Gi
Swap:         4.1Gi       120Mi       4.0Gi

```
Next to zero swap use.

---

### Post by n0c0d3 on 2023-10-18
Yes, that's what I've been told before. But as you're supposed to be able play h265 well as it's even hardware decoded on the CPU I was wondering if you maybe had just little RAM, so that's why I asked. So that's still a bit of a mystery I think.

---

### Post by TheFu on 2023-10-18
> **n0c0d3 said:**
> Yes, that's what I've been told before. But as you're supposed to be able play h265 well as it's even hardware decoded on the CPU I was wondering if you maybe had just little RAM, so that's why I asked. So that's still a bit of a mystery I think.

I think it is the encoding options used.  There are lots of options and to get higher quality, people might make choices about harder to decode.  Or it could be that my 2020 version of mpv doesn't know about the new options? Doesn't matter. It should still work.  In 1.5 yrs, I'll start thinking about migrating to a newer OS release.

---

