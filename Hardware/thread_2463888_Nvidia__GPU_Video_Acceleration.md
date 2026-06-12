---
title: "Nvidia / GPU Video Acceleration"
date: 2021-06-20
forum: Hardware
---

### Post by Shibblet on 2021-06-20
I have been following all of the directions on how to get your "Chromium" Browser to work with GPU Acceleration [Here:]("https://www.linuxuprising.com/2021/01/how-to-enable-hardware-accelerated.html"), as well as looking at Arch to see how it's done, or if any of it is applicable, [Here:]("https://wiki.archlinux.org/title/Hardware_video_acceleration")

I have a GTX 780ti, and I know it only works with the "h264ify" Chromium Extension, and with H.264 Video.  It does not work with VP9 via Hardware, so this will be H.264 only.
I did all of these tests with the "Big Buck Bunny" video at 1080p and 60fps.

And I have been able to get it to work... or at least it "says" that it does.

[ATTACH=CONFIG]288700[/ATTACH]

Here is my GPU Monitor when decoding H.264 via YouTube

[ATTACH=CONFIG]288701[/ATTACH]

Then I also downloaded the video, and played it back in VLC which is set for VDPAU output.

[ATTACH=CONFIG]288703[/ATTACH]

As you can see, there is more more CPU usage with H.264, but no where near as much as when played in VLC with VDPAU...  However, the GPU Information is quite different between the two...  

Here is H.264 playback in YouTube:

[ATTACH=CONFIG]288704[/ATTACH]

And here is the VDPAU Playback in VLC:

[ATTACH=CONFIG]288705[/ATTACH]

Anyway, with all of that information, I am not really sure if I am getting HW Acceleration with video playback at all.  Any ideas?

---

### Post by Yellow Pasque on 2021-06-20
You're still using a VA-API->VDPAU wrapper in the browser, so it's not surprising there's some overhead there. It's not going to play as efficiently as native VDPAU. The question is whether it's better than software/CPU accel. I'm not sure what you are getting at here...

---

### Post by Shibblet on 2021-06-21
> **Yellow Pasque said:**
> You're still using a VA-API->VDPAU wrapper in the browser, so it's not surprising there's some overhead there. It's not going to play as efficiently as native VDPAU. The question is whether it's better than software/CPU accel. I'm not sure what you are getting at here...

Here is what it looks like with Video Acceleration on:

[ATTACH=CONFIG]288707[/ATTACH]

And here is what it looks like without Video Acceleration:

[ATTACH=CONFIG]288708[/ATTACH]

Not much of a difference on the CPU.  So, I guess what I am getting at is... Does this actually work, or is it just smoke and mirrors?

---

### Post by CatKiller on 2021-06-21
Video decoding is a set of (usually vector) calculations.

You can do them on any CPU, in software. To hit the speed requirements of doing them in realtime, the processor has to be running quite fast. 

But! CPUs have had specific ASICs and co-processors for doing fast, efficient vector calculations for a long time; that's what AVX, SSE and 3DNow! are all about.

But! GPUs are also really good at doing fast, efficient vector calculations, even more so than CPU co-processors. 

But! GPUs can have their own media decoding co-processors which are even faster and even more efficient. 

All of these except the very first one are "hardware accelerated." Both the last two are "GPU accelerated." 

Your output when you were using the "Video Engine" is when you were using your GPU's media decoding block. The output when you weren't using the "Video Engine" is when you were using just the vector calculation capabilities of your GPU.

---

### Post by Shibblet on 2021-06-21
> **CatKiller said:**
> Your output when you were using the "Video Engine" is when you were using your GPU's media decoding block. The output when you weren't using the "Video Engine" is when you were using just the vector calculation capabilities of your GPU.

So, I want to make sure I am hearing you correctly.  There is really no reason to go through all of this "setup" stuff in order to get Hardware Decoding in the Browser since the GPU is going to be used for vector calculations anyway?

One claims to be "Hardware Accelerated," the other is not.  Both use roughly the same amount of CPU.

So, whether or not HW Acceleration is functioning, it's still going to use the same amount of CPU either way?

What's the point of HW Acceleration then?

---

### Post by CatKiller on 2021-06-21
> **Shibblet said:**
> What's the point of HW Acceleration then?
Battery life. On the desktop it doesn't matter that much - you won't generally want to do it entirely in software, since a slow CPU can't keep up, but as long as you've cleared that hurdle so that it actually works, there's not much advantage in going further. On a mobile device, though, using the dedicated media decoding blocks makes a significant different to power draw.

---

### Post by Shibblet on 2021-06-21
> **CatKiller said:**
> Battery life. On the desktop it doesn't matter that much - you won't generally want to do it entirely in software, since a slow CPU can't keep up, but as long as you've cleared that hurdle so that it actually works, there's not much advantage in going further. On a mobile device, though, using the dedicated media decoding blocks makes a significant different to power draw.

Thanks!  That's probably the best answer I have found yet.

I have done some serious internet searching, and most of the answers seem to be that it's a major difference.  Whereas everything I have done only comes up to a minor difference...

Second question:  I am curious how this works in Windows.  I have some friends who claim their graphics cards take the entire process over, and they get significantly better performance in these cases.  Any ideas why this would be so different in Linux?

---

### Post by CatKiller on 2021-06-21
> **Shibblet said:**
> Second question:  I am curious how this works in Windows.  I have some friends who claim their graphics cards take the entire process over, and they get significantly better performance in these cases.  Any ideas why this would be so different in Linux?
Market share and the iron grip of Microsoft.

Microsoft can mandate that all hardware has to use whatever interface Microsoft likes, and browsers have to support that because of Windows' market share. On Linux, Nvidia uses VDPAU and Intel went with their own VA-API, and browser makers haven't bothered supporting either at all until very recently because of the small market share.

---

### Post by Shibblet on 2021-06-21
> **CatKiller said:**
> Market share and the iron grip of Microsoft.

Microsoft can mandate that all hardware has to use whatever interface Microsoft likes, and browsers have to support that because of Windows' market share. On Linux, Nvidia uses VDPAU and Intel went with their own VA-API, and browser makers haven't bothered supporting either at all until very recently because of the small market share.

Gotcha.

So, in essence, Linux (in general) has "Hardware 'Assisted' Acceleration."

These are the things that cause Linux users to go "back" to Windows.  Things like drivers not working correctly and hardware acceleration issues.  I don't see software really being a big issue much anymore.  Even Windows users are aware of replacement software, such as GIMP for Photoshop, and Only Office for MS Office... 

Anyway...  I am using a desktop, and the gains with "HW Assist" are minimal, as you can see in the screenshots.

How hard would it be to use VDPAU for Video in the Browser instead of VAAPI?

---

### Post by CatKiller on 2021-06-21
> **Shibblet said:**
> How hard would it be to use VDPAU for Video in the Browser instead of VAAPI?
All you'd need to do is convince the browser makers to wire up support for VDPAU. In the meantime there's a VA-API/VDPAU wrapper that turns VA-API calls into VDPAU ones, but it's apparently a bit finicky.

---

### Post by monkeybrain20122 on 2021-06-21
I don't think vdpau works on webm (youtube's default format). There is a frefox addon which plays Youtube videos in .mp4, you can probably achieve the same by messing with about:config  (I haven't tried it) and years ago there was a Firefox mpv addon for which vdpau did work (video streamed through mpv in .mp4 format) but it no longer worked after Firefox retired all nacl plugins.
 
 if you test with downloaded (local) videos,  it is the same. vdpau doesn't work for webm, but works for .mp4 and .mkv. 

If you use vdpau, mpv is a better option than vlc, it is more efficient and works when vlc fails (aside: with mpv you can directly stream without downloading, vlc can do that too but only on Youtube and apparently the resolution is limited to 720p. there is no limit for mpv, but vlc plays 360 deg streams while mpv can't)

So in conclusion, vdpau doesn't work if you watch youtube from browser, it works if you stream through mpv and use .mp4 as your format. It works with streaming through vlc but it is probably not as efficient as mpv and the resolution is limit to 720p. Local videos work if in .mp4 or mkv, but mpv is more efficient and some 4k videos don't work with vlc but work with mpv.

---

### Post by Shibblet on 2021-06-21
> **monkeybrain20122 said:**
> I don't think vdpau works on webm (youtube's default format). There is a frefox addon which plays Youtube videos in .mp4, you can probably achieve the same by messing with about:config  (I haven't tried it) and years ago there was a Firefox mpv addon for which vdpau did work (video streams through mpv in .mp4 format) but it no longer works after Firefox retired all nacl plugins.

Again if you test with downloaded (local) videos, vdpau doesn't work for webm, but works for .mp4 and .mkv. Also, if you use vdpau, mpv is a better option than vlc.

Yeah.  I like MPV quite a bit more, but VLC has the whole kitchen sink baked in... no additional drivers required.  ;-)  My current work-around for YouTube is to copy the link directly into VLC, and just watch it that way.  This way the video runs through VDPAU and uses the HW Video Decoder.  Barely any CPU time is used.  However, this limits my YouTube viewing to 720p, even if the Video is in 1080p (or higher.)  YouTube separates their video and audio when it's over 1080p.  There used to be a way to grab both streams, but it's no longer available...  Oh well, I guess.  Here today, gone tomorrow.

What I am directly attempting to do, is get Stadia working with HW Acceleration.  With Software, the decode time isn't as fast as it could be with H.264 video.  I can run VP9 as well, but it uses more of the CPU, and the decode time is the same.  IMHO, this is one of the best ways to game (for me), due to it being fairly hardware independent, and available on Linux.  But, is slightly disappointing at this point, because of the lack of HW Video Decoding.  

[IMG]https://i.imgflip.com/2jb0fv.jpg[/IMG]

With (True) HW Acceleration, the decode time drops sufficiently, and allows for consistent 1080p streaming.  Without it, or even with "HW Assisted Acceleration" the resolution stays at the 720p area for the proper decode time (speed.)

This was tested in Windows 10 on a friends computer, and it works great.  H.264 is Hardware Accelerated, and it streams at full 1080p (4K if you have it).  The decode time is significantly lower, and it never (seems to) drop from 1080p down to 720p.

So, I am a little bit bummed out that we now have services like Stadia (Luna / GeForce Now / and soon XBox Game Pass) which would eliminate the need for specific hardware and operating systems... but then only quasi-support.

---

### Post by monkeybrain20122 on 2021-06-21
Like I said if you want to stream Youtube with full 1080 or above using vdpau then use mpv. vlc is limited to 720p. You can do it by cutting and pasting url like you do with vlc if you use smplayer as a front end for mpv.

I don't see any problem with having more than one player for different needs, it is not like you have to pay for them anyway and both are light. The default totem player which is pretty useless probably takes up more disk space than either.

If you want all in one type of software that uses hw decoding kodi is another option but it is not light and has too many options for my need.

---

### Post by Shibblet on 2021-06-27
> **monkeybrain20122 said:**
> Like I said if you want to stream Youtube with full 1080 or above using vdpau then use mpv. vlc is limited to 720p. You can do it by cutting and pasting url like you do with vlc if you use smplayer as a front end for mpv.

I don't see any problem with having more than one player for different needs, it is not like you have to pay for them anyway and both are light. The default totem player which is pretty useless probably takes up more disk space than either.

If you want all in one type of software that uses hw decoding kodi is another option but it is not light and has too many options for my need.

As much as I appreciate this new option... it unfortunately doesn't work.  SMPlayer doesn't stream the H.264 version, it streams the VP9 version, which is not supported by my video card.  I'm not quite sure how to get it to "force" the H.264 version like you can with the Chrome Extension "h264ify."  

Regardless... Thank you for the idea.

---

### Post by monkeybrain20122 on 2021-06-30
> **Shibblet said:**
> As much as I appreciate this new option... it unfortunately doesn't work.  SMPlayer doesn't stream the H.264 version, it streams the VP9 version, which is not supported by my video card.  I'm not quite sure how to get it to "force" the H.264 version like you can with the Chrome Extension "h264ify."  

Regardless... Thank you for the idea.

Actually it does but you have to configure it

Open Smplayer go to Preference > Advanced > Mplayer/mpv, put in something like this (modify for your need accordingly)  then it streams the mp4 version if available

Options
```
--ytdl-format=bestvideo[ext=mp4][width<=1920][height<=1080]+bestaudio[ext=m4a]/best[ext=mp4]/best
```

---

### Post by Shibblet on 2021-06-30
> **monkeybrain20122 said:**
> Actually it does but you have to configure it

Open Smplayer go to Preference > Advanced > Mplayer/mpv, put in something like this (modify for your need accordingly)  then it streams the mp4 version if available

Options
```
--ytdl-format=bestvideo[ext=mp4][width<=1920][height<=1080]+bestaudio[ext=m4a]/best[ext=mp4]/best
```

Hey Thanks!  That works great!

Now... how do we make VDPAU work in the Browser for Stadia?

---

### Post by mastablasta on 2021-07-01
what if you used Chrome browser? i mean Google supposedly should support this feature. it porbably does support it on ChromeOS and Android.

have you seen this one: [https://gist.github.com/SalomonBrys/c76637e4ac026466201e6ef14be14002](https://gist.github.com/SalomonBrys/c76637e4ac026466201e6ef14be14002)

---

### Post by Yellow Pasque on 2021-07-01
> **Shibblet said:**
> how do we make VDPAU work in the Browser for Stadia?

Again, chromium (and firefox) don't use VDPAU directly. If you want that, you'll have to write it yourself. So,

1. Make sure 'vainfo' output is correct.
2. Look at chrome://gpu and make sure it says "Video Decode: Hardware Accelerated". If it doesn't, try forcing it on in chrome://flags
3. Make Stadia use H.264 if possible (I don't know anything Stadia, so don't ask me how.)

---

### Post by Shibblet on 2021-07-01
> **mastablasta said:**
> what if you used Chrome browser? i mean Google supposedly should support this feature. it porbably does support it on ChromeOS and Android.

have you seen this one: [https://gist.github.com/SalomonBrys/c76637e4ac026466201e6ef14be14002](https://gist.github.com/SalomonBrys/c76637e4ac026466201e6ef14be14002)

I should show you this...
[https://ubuntuforums.org/showthread.php?t=2464112]("https://ubuntuforums.org/showthread.php?t=2464112")

> **Yellow Pasque said:**
> Again, chromium (and firefox) don't use VDPAU directly. If you want that, you'll have to write it yourself. So,

1. Make sure 'vainfo' output is correct.
2. Look at chrome://gpu and make sure it says "Video Decode: Hardware Accelerated". If it doesn't, try forcing it on in chrome://flags
3. Make Stadia use H.264 if possible (I don't know anything Stadia, so don't ask me how.)

1.  Got it.  Done.
2.  Also done.
3.  There is an extension called "Stadia Enhanced" that will allow you to force H.264.  It unfortunately uses H.264, but doesn't seem as if it uses Hardware Acceleration at all.

I'll harken back to this post in this thread...

> **Shibblet said:**
> Here is what it looks like with Video Acceleration on:

[ATTACH=CONFIG]288707[/ATTACH]

And here is what it looks like without Video Acceleration:

[ATTACH=CONFIG]288708[/ATTACH]

Not much of a difference on the CPU.  So, I guess what I am getting at is... Does this actually work, or is it just smoke and mirrors?

---

### Post by Yellow Pasque on 2021-07-01
*Shrug* Don't know what else to tell you. Maybe the VA-API -> VDPAU wrapper is inefficient and not worth it (or even counterproductive) for H.264 with a modern CPU. It hasn't been touched in almost a decade: [https://github.com/freedesktop/vdpau-driver](https://github.com/freedesktop/vdpau-driver)

---

### Post by Shibblet on 2021-07-01
> **Yellow Pasque said:**
> *Shrug* Don't know what else to tell you. Maybe the VA-API -> VDPAU wrapper is inefficient and not worth it (or even counterproductive) for H.264 with a modern CPU. It hasn't been touched in almost a decade: [https://github.com/freedesktop/vdpau-driver](https://github.com/freedesktop/vdpau-driver)

I agree with you.  Looks like this "old hardware" is being left in the dust.

Most of the streaming services (YouTube / Stadia / GeForce Now / XCloud) all still support H.264 for Legacy equipment.  But their primary feeds are all VP9.  I understand that VP9 offers better compression, higher quality/resolution, etc...  But I'd like to give a huge thanks to these companies that still offer support for H.264.

I'd still like to figure out how to get this to work.  Or at least why Google doesn't even add support for this in their OWN BROWSER?!

---

### Post by Yellow Pasque on 2021-07-01
> **Shibblet said:**
> Or at least why Google doesn't even add support for this in their OWN BROWSER?!

It's not Google's fault. It comes down to Nvidia not supporting VA-API properly, and maybe the devs who wrote the hardware decode accel code insisting on VA-API, when VDPAU would have been better.

---

### Post by monkeybrain20122 on 2021-07-02
> **Shibblet said:**
> I should show you this...
[https://ubuntuforums.org/showthread.php?t=2464112](https://ubuntuforums.org/showthread.php?t=2464112)



1.  Got it.  Done.
2.  Also done.
3.  There is an extension called "Stadia Enhanced" that will allow you to force H.264.  It unfortunately uses H.264, but doesn't seem as if it uses Hardware Acceleration at all.

I'll harken back to this post in this thread...

So if you can somehow get vaapi to work on Nvidia then there is some good news for you
[https://askubuntu.com/questions/1291279/ubuntu-20-10-firefox-82-intel-hd-500-vaapi-hardware-acceleration](https://askubuntu.com/questions/1291279/ubuntu-20-10-firefox-82-intel-hd-500-vaapi-hardware-acceleration)

I followed these steps to enable vaapi decoding on Firefox on and use the h264fy addon   and get it working on an old Toshiba netbook with Ubuntu20.04. I managed to cut cpu usage in half for Youtube on FF.

How do you get vaapi to work on Nvidia? (Chromium and Firefox both use vaapi for hardware decoding) AFAIK you can you a vaapi backend for vdpau in non Navidia hardware via libvdpau-gl1, but I don't know of any method for the other way around.

Edited: Ok use the vdapu-va-driver to run vaapi on Nvidia  But this is not in Ubuntu 20.04's repo, it can be installed from the chromium dev ppa.

---

### Post by monkeybrain20122 on 2021-07-03
More info for enabling vaapi on Firefox, there were some videos that the method above didn't work, but they all work now with the additional editing of about:config in this post, I think setting media.rdd-vpx.enabled to false drastically cuts down cpu usage on some videos that despite neither hd nor full of actions (just some guy talking) but consume a lot of cpu
[https://discourse.ubuntu.com/t/enabling-accelerated-video-decoding-in-firefox-on-ubuntu-21-04/22081](https://discourse.ubuntu.com/t/enabling-accelerated-video-decoding-in-firefox-on-ubuntu-21-04/22081)

Actually the last step on the askuuntu thread from my last post didn't work for me (editing the .desktop file by editing ,desktop file to changeto  EXC=env MOZ_X11_EGL=1 firefox) Neither did putting export MOZ_X11_EGL=1 in .profile. So I am not sure if MOZ_X11_EGL is an environmental variable or an option to start firefox. 

But the following works and is probably more elegant than creating an edited desktop file in .local/share/applications.

Create a script called firefox and place it in $HOME/bin and make it executable, it will override /usr/bin/firefox when firefox is invoked, either from terminal or by launching from .desktop file (if $HOME/bin does not exist, create it, logout and login again for it to take effect)

The firefox script is just

```
#!/bin/bash

MOZ_X11_EGL=1 /usr/bin/firefox "$@"
```

---

### Post by Shibblet on 2021-07-07
> **Yellow Pasque said:**
> It's not Google's fault. It comes down to Nvidia not supporting VA-API properly, and maybe the devs who wrote the hardware decode accel code insisting on VA-API, when VDPAU would have been better.

As much as I don't like that answer... I do actually want to believe that.  However, I have a Chromebook that seems to have Hardware Acceleration built in, that works flawlessly in YouTube, Stadia, XCloud, and GeForce Now.  So, that's a hard pill to swallow for me.

Having said that, the Chromebook does Hardware Acceleration with VP9... and I don't think I've tested it with H.264.

Either way, VP9 Acceleration (on a Core-M3) works AMAZINGLY with all of these services.  It just seems strange that H.264 Acceleration doesn't work AT ALL on a Core i7-3770 or GTX 780ti.

---

### Post by monkeybrain20122 on 2021-07-07
> **Shibblet said:**
> As much as I don't like that answer... I do actually want to believe that.  However, I have a Chromebook that seems to have Hardware Acceleration built in, that works flawlessly in YouTube, Stadia, XCloud, and GeForce Now.  So, that's a hard pill to swallow for me.

Having said that, the Chromebook does Hardware Acceleration with VP9... and I don't think I've tested it with H.264.

Either way, VP9 Acceleration (on a Core-M3) works AMAZINGLY with all of these services.  It just seems strange that H.264 Acceleration doesn't work AT ALL on a Core i7-3770 or GTX 780ti.

Try this [https://github.com/xtknight/vdpau-va-driver-vp9](https://github.com/xtknight/vdpau-va-driver-vp9)

I tested it with chromium 9.1.0 from the beta ppa [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta) (not worked with 9.2.0 in the dev ppa) GTX 1070 with the proprietary driver. It works!


vdpau-va-driver+vaapi doesn't work with Firefox with the Nvidia proprietary driver because the proprietary driver doesn't support DMA-BUF see [https://forum.manjaro.org/t/firefox-nightly-86-and-vdpau-nvidia/48469](https://forum.manjaro.org/t/firefox-nightly-86-and-vdpau-nvidia/48469). But reportedly it works with the nouveau driver.

You may also look at [ff2mpv]("https://addons.mozilla.org/en-CA/firefox/addon/ff2mpv/"), which offers the option of opening video link in mpv.

---

### Post by monkeybrain20122 on 2021-07-07
In Chromium go to about:flags and enable override software rendering then restart it with 

```
LIBVA_DRIVER_NAME=vdpau VDPAU_DRIVER=nvidia chromium-browser --use-gl=desktop --enable-features=VaapiVideoDecoder
```

---

### Post by Shibblet on 2021-07-07
> **monkeybrain20122 said:**
> Try this [https://github.com/xtknight/vdpau-va-driver-vp9](https://github.com/xtknight/vdpau-va-driver-vp9)

I tested it with chromium 9.1.0 from the beta ppa [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta) (not worked with 9.2.0 in the dev ppa) GTX 1070 with the proprietary driver. It works!

How are you able to get that PPA to override the Snap Package.  I still cannot do it...
[https://ubuntuforums.org/showthread.php?t=2464112]("https://ubuntuforums.org/showthread.php?t=2464112")

> **monkeybrain20122 said:**
> You may also look at [ff2mpv]("https://addons.mozilla.org/en-CA/firefox/addon/ff2mpv/"), which offers the option of opening video link in mpv.

That's a good alternative as well.  But the option you helped me with earlier in this thread, MPV (SMPlayer) and adjusting the type of video to get from YouTube seemed to create a workaround for YouTube.  I need to get this working "in-Browser" for streaming services.

Thank you again for all the help!  If I haven't said it before, I will say it again... I really do appreciate it.

---

### Post by monkeybrain20122 on 2021-07-07
> **Shibblet said:**
> How are you able to get that PPA to override the Snap Package.  I still cannot do it...
[https://ubuntuforums.org/showthread.php?t=2464112](https://ubuntuforums.org/showthread.php?t=2464112)

.

Huh? I didn't do anything. The ppa version is 0.91, snap is 0.85, so I just added the ppa and update, install, that was it. Didn't do anything special. Did it on two machines with Ubuntu 20.04. One with intel graphic, one with Nvidia. Chromium vaapi works in both. Firefox vaapi works in intel but not Nvidia with the proprietary driver (but that machine is so powerful that I don't need hardware acceleration for browser anyway) Couldn't get Chrome or Vivaldi to work in either though according to some people they should work with intel card at least if based on Chromium >= 0.90

---

### Post by Shibblet on 2021-07-07
> **monkeybrain20122 said:**
> Huh? I didn't do anything. The ppa version is 0.91, snap is 0.85, so I just added the ppa and update, install, that was it. Didn't do anything special. Did it on two machines with Ubuntu 20.04. One with intel graphic, one with Nvidia. Chromium vaapi works in both. Firefox vaapi works in intel but not Nvidia with the proprietary driver (but that machine is so powerful that I don't need hardware acceleration for browser anyway) Couldn't get Chrome or Vivaldi to work in either though according to some people they should work with intel card at least if based on Chromium >= 0.90

I am running Kubuntu 21.04, and it will not allow me to download the PPA for that Chromium Build.  APT overrides the PPA, and downloads the Chromium SNAP.  Nothing I can do to fix it.

---

### Post by monkeybrain20122 on 2021-07-07
Did you refresh muon after you added the ppa? Or in command line run sudo apt update after you added the ppa.

I made a fresh install of kubuntu 21.04 in a VM and added the ppa, updated then installed chromium-browser. Chromium 91 installed from ppa without problem, it is not the snap (ver 85). See attached. I have not modified the system in anyway other than running the post installation updates. In particular I haven't removed any snap package. 

If you still have problems please post the exact commands you use to install the ppa version of Chromium and the terminal outputs.

---

### Post by Shibblet on 2021-07-08
> **monkeybrain20122 said:**
> In Chromium go to about:flags and enable override software rendering then restart it with 

```
LIBVA_DRIVER_NAME=vdpau VDPAU_DRIVER=nvidia chromium-browser --use-gl=desktop --enable-features=VaapiVideoDecoder
```

OMG!  That worked!  This made YouTube use my built-in Hardware Decoder right in the browser!  I had to change "chromium-browser" to "brave-browser-stable," to accommodate the browser I am using, but it worked!

I have the h264ify extension in the browser as well, to make sure that YouTube sends H.264 Video, but it finally worked!!!

However, it still does not work with Stadia.  I have the Stadia Enhanced Extension, and can force Stadia to use H.264 instead of VP9.  Unfortunately, it still does it in Software.  Any ideas why one would work, but not the other?

---

### Post by monkeybrain20122 on 2021-07-08
> **Shibblet said:**
> 
However, it still does not work with Stadia.  I have the Stadia Enhanced Extension, and can force Stadia to use H.264 instead of VP9.  Unfortunately, it still does it in Software.  Any ideas why one would work, but not the other?

I think h264ify works only on Youtube.

---

### Post by Shibblet on 2021-07-08
> **monkeybrain20122 said:**
> I think h264ify works only on Youtube.

Correct.  Although, the Stadia Enhanced Extension will allow you to force H.264 or VP9.

Either way, Stadia still only runs in Software mode.

---

### Post by monkeybrain20122 on 2021-07-08
Did you try chromium? Many people on forums say it works. I attempted to set up a trial account to test it but they want my payment options so I aborted.

Edited: BTW I just installed the brave-browser and went to Youtube with the same flags, didn't work.

---

### Post by mastablasta on 2021-07-09
> **Shibblet said:**
> 

However, it still does not work with Stadia.  I have the Stadia Enhanced Extension, and can force Stadia to use H.264 instead of VP9. 

would it work with geforce now?

---

### Post by Shibblet on 2021-07-09
> **mastablasta said:**
> would it work with geforce now?

It doesn't work with anything besides YouTube, using the h264ify browser extension.

I have tested Netflix, Hulu, Disney+, and Paramount+, and Amazon Prime for Streaming Video Services.  Strangely enough, the Netflix Previews work, but the actual movie stream does not...
I have also tested Stadia, GeForce Now, and XCloud for Gaming Services.

Stadia uses H.264, but for some reason the browser doesn't decode it with VDPAU.  Stadia runs in H.264 Software Mode.
I assume (loaded term, I know) that the other services are all sending VP9 streams by default.

I wonder if this whole situation would be resolved if I could just get a new Video Card capable of decoding VP9.  But unless I feel like paying Triple the retail price, I am stuck with what I have.  ;-)

---

### Post by monkeybrain20122 on 2021-07-09
> **Shibblet said:**
> 

I wonder if this whole situation would be resolved if I could just get a new Video Card capable of decoding VP9.  But unless I feel like paying Triple the retail price, I am stuck with what I have.  ;-)

According to [Archwiki]("https://wiki.archlinux.org/title/Firefox/Tweaks#Force-enable_hardware_video_decoding") Firefox can be configured to use vaapi decoding if use nouveau instead of the proprietary Nvidia driver (I only use it on an old intel machine, works there) I don't know how old your Nvidia card is but if it is old and you don't need things like cuda maybe it is worth a try. My GTX1070 is capable of decoding vp9 but then the cpus are so powerful that I can handle all streams with ease even without GPU acceleration, so I haven't really experimented with vaapi until reading your threads.

BTW Kodi uses vdpau out of the box. I know you can stream through it for something like Youtube, not sure about the gaming situation.

---

### Post by monkeybrain20122 on 2021-07-09
> **mastablasta said:**
> would it work with geforce now?

The issue is OP has to work through a browser and it seems that on Linux there are very few options for hardware decoding in browsers. AFAIK they all use vaapi and involve hacks that may stop working after an update. 

So far Chromium 91 installed via its beta ppa works both for intel and Nvidia, in Nvidia it uses vdpau-va-driver. In my tests I use the [vdpau-va-driver-vp9]("https://github.com/xtknight/vdpau-va-driver-vp9") version since my GPU is vp9 capable, but now Chromium simply blocks all vp9 contents, that maybe a bug in vdpau-va-driver-vp9. Firefox vaapi works on Intel machines (and presumably ADM too) but not on Nvidia if the proprietary driver is installed (works in Nouveau according to others' experience) 

Chromium is not an optimal solution IMO, it has other issues, it seems sluggish for browsing (instead of watching videos). For a while Chromium based browsers like Chrome, Opera, Vivaldi and Brave [reportedly]("https://www.linuxuprising.com/2021/01/how-to-enable-hardware-accelerated.html") work if compiled against Chromium >=89 but I have tested them and none of them work now (based on Chromium 91) In Chrome's case maybe Google screws us once again, not sure about the others. Brave is supposed to be build on Chromium with vaapi patch so maybe a bug in Chromium (vaapi doesn't work in ver 92 in dev branch ppa)

---

### Post by Shibblet on 2021-07-09
> **monkeybrain20122 said:**
> My GTX1070 is capable of decoding vp9 but then the cpus are so powerful that I can handle all streams with ease even without GPU acceleration, so I haven't really experimented with vaapi until reading your threads.

Again... thank you for the help.  I think we may have got about as far as we can at this point.

Audio Drivers have come to this point.  Sound processing takes us so little CPU cycles, that there is no point (really) to have additional sound processing hardware.  Not unless you are doing sound editing, or need specific equipment.  For basic playback (i.e. what you normally do with music, videos, and games), your CPU can decode in real time with VERY minor usage of the CPU.  Back when MP3's first came out, it was a different story.  Small file size, but it required a lot of CPU usage to decode and playback.

Now, your CPU can decode video with very small amount of CPU cycles, so for most "playback" options, it's not a big deal.  i.e. DVD (480p) Playback can be done on the CPU with little impact.  1080p needs more CPU, but it can do it.  And 4K requires too much CPU to do it on it's own.

This is why video cards like my GTX780ti, have hardware decoding built in.  VDPAU will decode up to 1080p 60fps video on the video card without using the CPU.  This frees up the CPU to do other things like process sound, window management, etc. 

My problem is the "Decode Speed" for game streaming.  It jumps up to 7+ ms, and then drops 1080p down to 720p to keep up.  With Hardware Decoding, the decode speed stays under 2ms, and keeps the picture at 1080p. (Tested on a friends Windows 10 computer)

So, I guess for the time being, I will just have to settle for CPU decoding, and live with 720p, until such time as I can either get a new GPU (at a reasonable price) or whole new computer.  Looking at a Ryzen 5 5000 series with iGPU.

---

### Post by monkeybrain20122 on 2021-07-09
> **monkeybrain20122 said:**
> 
Chromium is not an optimal solution IMO, it has other issues, it seems sluggish for browsing (instead of watching videos). For a while Chromium based browsers like Chrome, Opera, Vivaldi and Brave [reportedly]("https://www.linuxuprising.com/2021/01/how-to-enable-hardware-accelerated.html") work if compiled against Chromium >=89 but I have tested them and none of them work now (based on Chromium 91) In Chrome's case maybe Google screws us once again, not sure about the others. Brave is supposed to be build on Chromium with vaapi patch so maybe a bug in Chromium (vaapi doesn't work in ver 92 in dev branch ppa)

I take this back. Now with further tests it turns out vaapi does work in Google Chrome, Brave and Vivaldi and all don't have the laggy problem of Chromium (Chromium is slow in general and it struggles to load video as if internet is being cut off when vaapi is enabled, not the others!) The reason why they didn't work before appears to be due to crappy libva driver in Ubuntu 20.04.They all work now after upgrading these packages with this[ ppa]("https://launchpad.net/~savoury1/+archive/ubuntu/display"). 

This could be good news for those struggling to install Chromium (and tbh its performance is bad)

The ppa updates xserver-xorg along with other things, so it may be risky. I did it on an old laptop which I can afford to resinstall when it comes to worst, so do it at your own risk.

---

### Post by CatKiller on 2021-07-10
FWIW, the situation is likely to get better in the future. Vulkan is cross-platform and implemented by all modern hardware, and has recently gained the ability to handle decoding video streams. [This blog post](https://blogs.igalia.com/vjaquez/2021/07/09/video-decoding-in-gstreamer-with-vulkan/) has some details about implementing that functionality in GStreamer. I expect that browser developers will pick this up instead of using different paths depending on platform and hardware.

---

### Post by mastablasta on 2021-07-12
> **CatKiller said:**
>  Vulkan is cross-platform and implemented by all modern hardware, and has recently gained the ability to handle decoding video streams. 

let's hope so.

i n the mean time my card doesn't support vulkan, because they sneaked old chip into new card and sold it as new model.

---

### Post by Shibblet on 2021-07-12
> **CatKiller said:**
> FWIW, the situation is likely to get better in the future.
Well, I certainly hope so.  I have been planning on getting a new PC for years now... but the one I currently own still runs like a top!  However, I am starting to run into these little issues here and there, like Hardware Acceleration (hence the thread).  

I'd like to get a Ryzen 5000 Series CPU, but not really sure if Hardware Support for Linux (i.e. VP9 Decoding) will actually work.  I wish there was a way to load up Kubuntu on a PC before I purchased it, so I can see if it actually does what I need it to do.

> **CatKiller said:**
> Vulkan is cross-platform and implemented by all modern hardware, and has recently gained the ability to handle decoding video streams. [This blog post](https://blogs.igalia.com/vjaquez/2021/07/09/video-decoding-in-gstreamer-with-vulkan/) has some details about implementing that functionality in GStreamer. I expect that browser developers will pick this up instead of using different paths depending on platform and hardware.
I really like Vulkan.  And it is a major benefit to the Linux community.  Unfortunately, whenever a great new API comes out, Microsoft tends to fire back with new DirectX implementations that leave things like OpenGL and Vulkan in the dust.

I don't meant technologically.  They may be better API's... but if your game studio wants to make an XBox release of your game... it is going to have to be done in Direct X.  And console releases are where the money is at.  Currently, I think the only console that does support Vulkan is the Nintendo Switch, and they aren't about to share their IP's with ANYBODY.

I just can't wait to see a RayTraced version of Super Mario! (Ahem... Sarcasm)

---

### Post by mastablasta on 2021-07-13
> **Shibblet said:**
> 
I really like Vulkan.  And it is a major benefit to the Linux community.  Unfortunately, whenever a great new API comes out, Microsoft tends to fire back with new DirectX implementations that leave things like OpenGL and Vulkan in the dust.


meh, i just play older games. not so much time at hands anyway. i went to replay some older ones i likes, thinking i will cruise through faster, but it stalled in most of them. i went Arx Fatalis on Opensoruce engine, replayed Morrowind (that one i actually finished main quests) and oblivion i did the Shivering isles and KOTN quests + few sides ones, but main quest is still open, GTA: SA replay is also stuck at about 3/4. i ddi manage to finsih Total war Medieval small camaign. I din't like the game as much as Rome.

i am currently playing CS:GO to relax after work. and also Subnautica (to relax) but this one is getting close to end (i am at 3/4 as well here). During weekend when i have more time we play coop games with kids (Synergy, L4D2, Minecraft...). 

plus many new games don't bring much to the old concepts. ok slightly better graphics, nicer cut scenes, but that's about it. at it's core game is same as previous iteration that might work fine via proton or otherwise. the only one i would like to try from the newer ones is CoD warzone, but i see there are already plenty of cheaters there, so... i also tried Doom 2016 and new Wolfenstein on my kids PC and well graphics are impressive, but games play is kind of boring. maybe Red Dead 2 and Witcher series would be interesting, but i am not sure i have the time to play either. i have a really low end GPU but old games work just fine.

---

### Post by Shibblet on 2021-07-13
> **mastablasta said:**
> meh, i just play older games. not so much time at hands anyway. i went to replay some older ones i likes, thinking i will cruise through faster, but it stalled in most of them. i went Arx Fatalis on Opensoruce engine, replayed Morrowind (that one i actually finished main quests) and oblivion i did the Shivering isles and KOTN quests + few sides ones, but main quest is still open, GTA: SA replay is also stuck at about 3/4. i ddi manage to finsih Total war Medieval small camaign. I din't like the game as much as Rome.

Yeah, I don't get into games as much as I did before.  And my current computer seems to run even more recent titles very well.  This is why I really like the concept of Cloud Gaming.  Just buy and play, no hardware required.  Since we all seem to have amazing internet these days.

> **mastablasta said:**
> plus many new games don't bring much to the old concepts. ok slightly better graphics, nicer cut scenes, but that's about it. at it's core game is same as previous iteration that might work fine via proton or otherwise. the only one i would like to try from the newer ones is CoD warzone, but i see there are already plenty of cheaters there, so... i also tried Doom 2016 and new Wolfenstein on my kids PC and well graphics are impressive, but games play is kind of boring. maybe Red Dead 2 and Witcher series would be interesting, but i am not sure i have the time to play either. i have a really low end GPU but old games work just fine.

Yep.  Agreed.  They don't make nostalgia like they used to. ;-)

I find the same concept with Cell Phones.  Little better camera, quasi-faster processor, iffy battery... just call it the next generation, and people will flock like seagulls to buy it.  i.e. "All hail iPhone! (insert Samsung/Motorola/etc. here)"

There are very few games that I truly enjoy.  Most of the ones I have, I tend to play for a couple of hours, then drop out bored...  The last few that I truly enjoyed were Skyrim, Shovel Knight, Hollow Knight, and Tomb Raider (2016).  I played through "A Plague Tale: Innocence," and I think I didn't get bored of this only because it was short enough to finish before I did.  It is truly an amazing achievement for an indie game though.

Regardless.  I found myself doing something I think we all do currently.  I was purchasing games on Steam that I "wanted" to play.  However, I just never got around to them.  When I say we all do this, I don't necessarily mean with games, we all tend to do it now with Streaming Services like Netflix, Disney, Hulu, Paramount, Amazon, etc...

Disney+ members spend $69.99 a year to WAIT on the next season of "The Mandalorian" (or whatever series) and then binge it in a week.  Same with Paramount+... Still waiting for Season 2 of Star Trek Picard... but I've paid for the service for over a year.  Forget it... I'm done.

My wife and I just had a discussion about which ones of the services we actually use on a regular basis.  We dropped every one except Amazon Prime, since she actually uses the shipping service for her business.

Wow... how do these threads get off point again?  ;-)

---

