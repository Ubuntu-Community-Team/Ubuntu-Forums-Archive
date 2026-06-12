---
title: "video capture--my laptop screen as a monitor for my ps4"
date: 2014-11-06
forum: Hardware
---

### Post by kccv42 on 2014-11-06
I am trying to find a hd video capture that i can connect to use my laptop screen as a monitor for my ps4. Most of the hd video captures are not for linux. If i use code weaver will there be lag when i try to display a game on my laptop screen?

---

### Post by TheFu on 2014-11-06
I don't know of any low-cost 1080p external capture solutions that work with Linux. That doesn't mean there aren't any, just that they are $400+ or I don't know about them.

I use a Hauppauge 1512 (cough, under Win7).

Very few laptops have video INPUT capabilities. How do you plan to get the video into the laptop from the PS4? Does it already have a capture device?  The exact vendor, model you plan to use would be helpful. I'm confused as to how a WINE solution can help with video capture, but I'm slow in that way.

---

### Post by kccv42 on 2014-11-07
The wine would be for running the program on that streams the video to my laptop.

---

### Post by TheFu on 2014-11-07
> **kccv42 said:**
> The wine would be for running the program on that streams the video to my laptop.

Sorry, guess I still don't understand how the video will get to the laptop from the PS4? 
Does it have a video capture card?  I think a video capture device is the only way to record everything beyond the limits that SONY puts on their internal video capture stuff.  Perhaps you can be happy with those limitations?
[https://support.us.playstation.com/app/answers/detail/a_id/5088/~/save-and-share-ps4-gameplay-videos](https://support.us.playstation.com/app/answers/detail/a_id/5088/~/save-and-share-ps4-gameplay-videos)

This [http://www.cinemablend.com/games/PS4-Now-Fully-Supports-Hauppauge-Game-Video-Capture-Devices-63958.html](http://www.cinemablend.com/games/PS4-Now-Fully-Supports-Hauppauge-Game-Video-Capture-Devices-63958.html) describes the way I thought you needed to solve this.

---

### Post by kccv42 on 2014-11-08
Can the Hauppauge 1512 be used with linux?

---

### Post by TheFu on 2014-11-08
> **kccv42 said:**
> Can the Hauppauge 1512 be used with linux?

Not the last time I checked, hence my first reply about Linux devices costing more.
You have to figure out the inputs, the software and the outputs (both physical and video codecs) that are possible.

There are many non-HiDef options for Linux. I have a Plextor ConvertX PX-M402U - which claims Linux support. It is old and supports only s-video and RCA-video as input. Never tried it with Linux and SD doesn't interest me anymore. Also have a Hauppauge 950Q somewhere - meh.  Before these, had an ATI TV-Wonder bt787.

The 1512 supports 1080p HDMI, but is Windows only. A few years ago, everyone used the 1212 ... not HDMI, but component, which can be just as good, but with lots of extra, thick cables and optical audio - meh.

Most TV tuner devices will do s-video without issue and there are many supported by Linux. I'd check the MythTV compatible cards and stick with those.

For standard-def stuff ... there are probably 50 $50-$150 options.

For HiDef .... I think there are only 2 choices.
* Hauppauge 1212 [http://www.mythtv.org/wiki/Hauppauge_HD-PVR_1212](http://www.mythtv.org/wiki/Hauppauge_HD-PVR_1212)
* Blackmagic Intensity Pro/Shuttle $200 [http://ubuntuforums.org/showthread.php?t=1333927](http://ubuntuforums.org/showthread.php?t=1333927)  and [https://www.blackmagicdesign.com/products/intensity/models](https://www.blackmagicdesign.com/products/intensity/models)  Plus other non-free software may be required.

These are Windows only:
* Hauppauge 1512 Windows only
* Hauppauge Colossus - Windows only [http://www.mythtv.org/wiki/Hauppauge_Colossus](http://www.mythtv.org/wiki/Hauppauge_Colossus)

For me, the $80 difference in price was enough that Windows became viable. Also, 18 months ago, I don't think the Blackmagic Intensity Shuttle existed. I don't want any PCI-whatever in my video capture workflow. 

So - the first question is what output connections does the PS4 support that will also put out the resolution and audio you want?  Can the cheaper 1212 work or do you need the more expensive Blackmagic stuff?

Oh .. and you'll need a video editor too. For my needs, none of the Linux options works. I can do everything on Linux except easily remove commercials from recorded items. There is a $50 tool for Windows which makes this trivial. I looked again this morning for any Linux-based option - none found. There are a few great F/LOSS Linux video editors, but they each lack the 1 thing I need - interactive EDL verification and cutting.

---

### Post by kccv42 on 2014-11-21
If i used codeweaver, will that make it able to run  on linux.

---

### Post by TheFu on 2014-11-23
> **kccv42 said:**
> If i used codeweaver, will that make it able to run  on linux.

If codeweaver is WINE, I don't know, but don't think it likely.  However, I honestly do not know.  I do know that WINE worked with Quicken using a number of "winetricks" to get to "bronze" level.  Check the appdb at WINEHQ for the best knowledge.  WINE is NOT 100% implementation of the win32 API - especially where video is concerned.

---

