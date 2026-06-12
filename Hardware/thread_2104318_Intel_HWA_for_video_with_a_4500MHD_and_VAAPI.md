---
title: "Intel HWA for video with a 4500MHD and VAAPI"
date: 2013-01-12
forum: Hardware
---

### Post by br0adband on 2013-01-12
I'm not sure if this belongs in this subforum or the Multimedia & Video one, but it's specifically related to driver issues so, I guess an Admin or Mod will move it where appropriate which is fine. Now on to the meat and potatoes...

So I've decided that I'd like to use Ubuntu a bit more than I have in the past - it's been installed, removed, reinstalled, removed, and so on dozens of times in the past few years but I never stuck with it for whatever reasons (traditionally that I couldn't find adequate similar apps to their Windows counterparts, and I am and always will be a Windows user even if I get Ubuntu set up properly). But again, recently I did some research, learned about how Google has invested (not monetarily, I mean) in setting up a lot of their working machines with Ubuntu in a lightly skinned derivative they call Goobuntu, and I figured if they find it useful maybe I will if I put a bit more effort into it.

I grabbed Ubuntu 12.04 64 bit and installed it on my Dell Latitude E6400 laptop which has an Intel G45 chipset and hence the Intel 4500MHD (aka X4500) graphics chip on it. This GPU is fully capable of decoding h.264/AVC/VC-1 high definition video stream content, and it works flawlessly under Windows - I use MPC-HC and nothing else (not interested in all the madVR and other types of improvements - MPC-HC and Windows 7 are more than enough for video viewing.

I know people hate hearing "Well it works under Windows, why doesn't it work under Linux?!?!" but that's essentially what this post is going to be about, and yes I'm wordy so forgive me. I got 12.04 installed, fully updated, and then went and did research on getting the very latest Intel driver for the 4500MHD (ha, that's a journey in itself) up and running with support for VAAPI, Intel's video acceleration API which offloads the video decoding from the CPU to the GPU.

And that's where I'm at now. There are dozens if not a hundred or more guides out there specifically about getting the 4500MHD up and running with proper VAAPI support under Ubuntu (and other Linux distros as well), and I've tried a few dozen of them so far and I swear, this is one of those things that just irks me so badly about Linux in general - I'm a patient person, and I hate "giving up" when I strongly feel I can resolve something, but I'm at my wits end and it's past the point of being irritated now.

Whenever I get the driver(s) situated, built, installed, etc, and then I use the vainfo tool to check on the driver status, I always - without fail - end up getting this:

```

vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Intel i965 driver - 1.0.15
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
```

Now obviously that is telling me that I get HWA support for MPEG2 (basic DVD content) and nothing else - what I should be getting (hopefully) is something like this:

```

vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Intel i965 driver - 1.0.15
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
```

Which would be exactly what the 4500MHD is capable of supporting, but of course regardless of what I'm attempting and trying and failing at has been... well, utter failure. :(

I found instructions at [http://www.emmolution.org/?p=192](http://www.emmolution.org/?p=192) that seem - on the surface - that they should work. There's even a person that posts in the comments that it worked for them with 12.04 and yet I just keep slamming into a brick wall.

I could go on and on about this situation, and I've done several searches here at the forum as well as all over the place, even for different distros as well, and yet I am still dead in the water. Is this enough to make me dislike Ubuntu (and Linux in general) so much I won't use it anymore? No, not really since I can and do still watch HD videos on my laptop and they play fine, for the most part (with 50-60% CPU usage due to the lack of working HWA).

But it sure would be nice to actually *get everything working as it's designed to be doing*.

If anyone has any tips or tricks or direct firsthand experience trying to get VAAPI and HWA working correctly on a 4500MHD using Ubuntu 12.04 (or any version, really) I would love to hear your suggestions or thoughts.

Thanks for reading...

---

### Post by br0adband on 2013-01-20
Somewhat of a bump I assume, not meaning to get myself into any trouble but I figured I'd provide an update of sorts.

I noticed earlier, by firing up PowerTOP while doing some testing to reduce battery usage (trying to max out what this machine is capable of, obviously) and was really seriously irked to note 0% GPU usage, *seemingly ever*. I've got the latest i965-va-driver installed (the one from the Ubuntu repositories that's supposed to have at least some hardware acceleration) and apparently there's never any GPU acceleration kicking in regardless of what I'm doing.

Seems a bit odd to me since Unity is supposed to be GPU powered, and I've got Compiz running as well (it sure as heck seems like it is) so now I am completely stumped with this situation.

There are so many sites out there with the same basic instructions of just install the i965-va-driver and wham, it should work, but it's not working at all apparently and I'm somewhat disappointed in all this.

No matter what I put into Linux I swear, there's always one thing - just *one thing* - that always detracts from the experience so much it just sours me on it and I end up going back to Windows.

Looks like this will be the last straw for me at this point. I've grabbed the latest Intel drivers from 01.org and even those provide no acceleration so I guess I'm done with this.

Still hoping for a minor miracle if anyone has any suggestions or something else to try. I've tried to get this functional with Precise and Quantal (haven't tried Raring yet, not really interested and I don't think it'll matter). I know this 4500MHD is considered "old" but, it's fully capable of hardware acceleration and yes it works 100% under Windows - everything I keep reading says it's capable under Linux as well, I just wish I could figure this out. :(

---

### Post by brainwash on 2013-02-03
So, first of all, let me make something clear. VAAPI only provides hardware accelerated video decoding/encoding (if supported). Second, you did not provide much information about how you compiled and installed the specific libraries (default is /usr/local/lib).

However, I'm not sure, if it is actually worth the hassle. Playback of H.264 videos is less CPU intensive, but stutters a lot.

```
vainfo: VA-API version: 0.33 (libva 1.1.1.pre1)
vainfo: Driver version: Intel i965 driver - 1.0.19.pre1
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264Baseline           :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointVLD
```
```
Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

---

### Post by br0adband on 2013-02-04
I appreciate the response but I eventually just said to hell with it and went back to Windows 7. With this OS (Win 7 Pro) I can play videos with ~10% CPU - and I mean some very high bitrate files in the 40-60 Mbps range (test clips done with h.264 compression and in raw VC-1 format) using MPC-HC and the latest Intel video drivers for Windows and this GPU. Heck, I can even play some videos using Windows Media Player and they'll use *even less CPU*, remarkably.

I tried dozens of solutions, dozens of compiles, a dozen or so "custom" video drivers posted in a variety of places, the "pure" Intel drivers and libraries from 01.org (Intel itself) and I never got anywhere, not one step of progress and after 2-3 weeks of tinkering I just said that was enough.

I know the GPU is capable, but because of its age at this point the development to get h.264/AVC acceleration working with those Linux drivers seems to have been just passed over to the "obsolete" side of things that's that.

Seems silly of me to dump Linux in general just because I can't get that one particular thing functional as it should be, but when something doesn't work as it *should* under Linux but works "perfectly" under Windows then I'm going to stick with what works, as most people would (that's the general assumption, of course).

Thanks again...

---

