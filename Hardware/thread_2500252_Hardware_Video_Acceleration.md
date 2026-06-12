---
title: "Hardware Video Acceleration"
date: 2024-08-27
forum: Hardware
---

### Post by Shibblet on 2024-08-27
Just out of curiosity... Hardware Acceleration within a browser, has long been the bane of Linux users.

Any ideas as to why it's STILL not available without having to tweak things with dire hope?

---

### Post by TheFu on 2024-08-27
Because most CPUs can handle SW decoding video and that "just works", so the browsers tend to default to SW-decoding to avoid potential issues from the thousands of different video cards.

---

### Post by Shibblet on 2024-08-27
> **TheFu said:**
> Because most CPUs can handle SW decoding video and that "just works", so the browsers tend to default to SW-decoding to avoid potential issues from the thousands of different video cards.

This kinda makes sense.  

Most GPU's have hardware based decoders built in like H.264 / H.265 / AV1 etc.  So, this literally eliminates the burden on your CPU, and allows your GPU to do the decoding.  And now with onboard graphics, this should turn into a no-brainer.  Your CPU has a GPU built in specifically for this purpose. 

This also limits web based applications, specifically streaming services, to using CPU only.

So, on Windows, you can watch your Netflix, and still use your entire CPU...
But on Linux you have to share your CPU with Netflix...  Ugh.

It may seem minor, but there's a real issue here.  This has limited a lot of services from being usable in Linux.

---

### Post by TheFu on 2024-08-27
Netflix is a special case.  It is due to DRM if you have higher than 1080p resolution.  F/LOSS DRM drivers for AMD have been rejected by the HDMI/HDCP standards people multiple times and are required for content over 1080p. I think, I don't have any 4K displays, that when required DRM for 4K content isn't supported, the video driver reduces the resolution to 1080p.  I'm probably wrong about that.

Also, MS-Windows is a dictatorship, not a bazaar like Linux, so the dictator gets to mandate capabilities that a bazaar cannot. This makes it easier for content rights companies to work with 1 company, MSFT, to get everything they want.  That's completely different to the F/LOSS method where standards are expected to be publish and it is up to the software makers to follow those standards.   Clearly, there is one downside to the bazaar development method, but the 10000 bonuses make up for in in nearly every other way.
Ref: [https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar](https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar)

My solution to paid video content after trying to get a service working for over a month was to spend $30 on a streaming device and be done with it.  I put that IoT streaming device on a network by itself, still wired, and let all the people making money watching what we're watching be happy without them seeing any other devices or traffic on our network.  I'm usually the first to say I can stand on my principles, but no individual has ever one in a legal way against big content rights holders.  If you want to see their stuff, follow their rules.  The alternative is to not see their stuff.

BTW, I've never had a Netflix streaming subscription. I did have a Netflix DVD snail-mail subscription for many years. That DVD collection had about 100K+ movies and shows.  Compared to the less than 6K titles in their streaming lineup.  Netflix streaming is a joke compared to their old DVD offer.

---

