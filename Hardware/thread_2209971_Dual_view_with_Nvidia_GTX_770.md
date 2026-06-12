---
title: "Dual view with Nvidia GTX 770"
date: 2014-03-08
forum: Hardware
---

### Post by SimonErich on 2014-03-08
Hi guys,

I have a PC with 2 Monitors (connected via displayport to a nvidia gtx770 and the other one to the asus z87-pro c2 mainboard)

When I installed Ubuntu 13.10 everything was exactly as i wanted it to be. Both monitors working and the right one extending the left. Both had 2560x1440px.

The only problem I had was the fact, that it seemed that Chromium didn't use hardware acceleration and it told me to install different drivers for my cards to make it work. Also the mouse flickered sometimes (only while hovering special applications - i.e: chromium, sublime text)

So I thought: Maybe I can get more performance out of this if installed the Nvidia drivers. That's exactly what I did. I added the edgers ppa and installed nvidia-current. When I ended up with a blackscreen there I tried bumblebee, ... and everything else (of course I always purged everything before trying something else), optimus, but didn't manage to get my system working.

The only thing that seemed to work a bit, was when connecting both monitors to the nvidia card (one displayport and the other one hdmi) but then I only got a 1080p resultion of one of them.

I already googled a lot and I read this: [Fail to setup Dual Monitor in Ubuntu 13.10 with Nvidia GTX 780]("http://askubuntu.com/questions/378655/fail-to-setup-dual-monitor-in-ubuntu-13-10-with-nvidia-gtx-780")

But how is it possible that Ubuntu manages to do this out of the box and with Nvidia drivers there is no way.

I'd really like to get this to work and not just waste the performance I could have for nothing. Or is there a way to just use better drivers the ubuntu way and use hardware acceleration in chromium. (without just skipping chromiums warnings - as people suggest for this kind of thing, but recommend not to do it)
Also my computer freezes every now and then. At least 4-5 times a day, while I'm working and it seems to be nouveau related.


thanks in advance guys :)


best regards
  Simon

---

### Post by gordintoronto on 2014-03-08
I think Bumblebee and Optimus are intended for laptops, where you can disable the high-performance video adapter, to save battery life and, potentially, overheating.

The cable you use with HDMI affects the results you can see.

What is the brand and model of video card? Have you tried just using the video card, and ignoring the video connectors on the motherboard?

---

### Post by SimonErich on 2014-03-09
Hello gordintoronto,

thank you for your answer.

Oh I did not now, that there are differences between hdmi cables.
I just googled it and found out, that I might need a high speed hdmi cable.
I will order this right away.

My video card is a nvidia GTX 770

I've already tried to connect the hdmi and displayport (these are the two plugs on my card - apart from a dvi)
I will try this with a better hdmi cable, but I guess that this might not be as effective as using 2 different cards with theyr own performance for every monitor, or am I wrong here?

best regards
  Simon

---

### Post by SimonErich on 2014-03-09
So, I just found a dvi cable and tried to connect it to the video card directly.
Both cables are now connected to the video card and everything runs fine. I get full resolution on both monitors and no more flickering. :)
Thank you so much for heading me in the right direction.

---

