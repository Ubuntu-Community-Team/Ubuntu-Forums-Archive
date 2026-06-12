---
title: "need hdmi"
date: 2022-07-14
forum: Hardware
---

### Post by jgw on 2022-07-14
I need a hdmi and am not sure I have one.  I am sending a picture of what looks like a hdmi port but I can't connect to it with an hdmi cable.  The picture also shows what is next to it.  I have no idea what it means.  

Anyway, I need to know how to put an hdmi port on a computer (if this isn't one)

Thank you...............

---

### Post by mikewhatever on 2022-07-14
It's a Display Port, not HDMI. That said, DP++ means Dual-Mode DisplayPort, which supports HDMI or DVI.

---

### Post by jgw on 2022-07-14
thanks for the reply!

So, an hdmi cable should fit.  

I am wondering if I should buy a hdmi card, they aren't much (under 20.00)  my problem is my machine  (Mesa DRI Intel(R) HD Graphics 2000 (SNB GT1)).  better yet I actually already have one.  I might try that but first I gotta get my system to turn on its hdmi and my system doesn't want to do that.  (I have attached a hdmi cord nothing happened.  I will continue my quest)

---

### Post by jgw on 2022-07-14
I got some more info from hardinfo on my system:
HDA Intel PCH HDMI/DP,pcm:3	                                            Iinput device
snd_hda_codec_hdmi                  HDMI HD-audio codec          Loaded module

Apparently this means I have HDMI HD-audio codec loaded?

I have been doing a lot of reading on this hdmi thing.  I went to Softrware and Updates see if I had any additional drivers and it found absolutely none.  There was also a bunch of stuff about drivers.  Now I wonder if I need to get a driver for hdmi although I have never needed one before.  

I have spent hours on this thing and have mode no real progress.  If anybody has a clue about this I would really appreciate some help!

Thank you!

---

### Post by oldfred on 2022-07-14
Because it is Displayport, you need a special cable displayport to HDMI.
[https://www.amazon.com/Amazon-Basics-Uni-Directional-DisplayPort-Display/dp/B015OW3M1W](https://www.amazon.com/Amazon-Basics-Uni-Directional-DisplayPort-Display/dp/B015OW3M1W)

On a previous build, I made a mistake on purchase of motherboard.
Motherboard had HDMI & Displayport out, and monitor had VGA & DVI in.
I had an old nVidia card which had the DVI out, so used it. 
But then found that Intel chips video was a lot better than old nVidia card and found a cable to convert.

---

### Post by jgw on 2022-07-14
thanks for the reply. 

I was told:that what  I t thought was a Display Port, not HDMI. That said, DP++ means Dual-Mode DisplayPort, which supports HDMI or DVI. 

Then I ran pavucontrol and got a list of possibilities.  Every one was unavailable and three were unplugged (example below)
digital video (HDMI) output (unplugged)(uinavailable)

I don't even know if the port even works.  so far there is no indication of that.

I need an hdmi output because that's how I hook into the receiver that takes  my hdmi sound and video from the computer (via hdmi cable) to the tv

I have one other thing and that is installing a video card with a hdmi output.

Thoughts?

---

### Post by mikewhatever on 2022-07-14
> **jgw said:**
> thanks for the reply!

So, an hdmi cable should fit. 
...

Not really sure, but it does not look like it. Oldfred might be right about the adapter.
Wikipedia has more info on DP++...

---

### Post by Yellow Pasque on 2022-07-15
> PCH HDMI**/DP**

See the /DP? That's the important part. DisplayPort. If you want to connect a TV/monitor through HDMI, you'll need an adapter.

---

### Post by jgw on 2022-07-15
Thanks for the replies!

I had another computer and that one is almost there. I turned on the computer after I plugged into the hdmi and, after a couple of minutes I saw the computer in my tv.  My mouse and keyboard are also working.  My sound, however, is none.  My setting for 

My sound settings is "HDMI/DisplayPort Built-in-Audio" and that was arrived at automatically.  There are no other options, tried a test and nothing.  If I have the picture I have to have the sound (they are both in the same cable!)  I am missing something here I think.

Tried pavucontrol.  It started up and then said to wait a minute so it could connection with pulseaudio.  After a bit it just went away and nothing happened.  Getting interesting. 

Any thoughts on this is helpful.

---

### Post by mIk3_08 on 2022-07-16
> **jgw said:**
> I need a hdmi and am not sure I have one.  I am sending a picture of what looks like a hdmi port but I can't connect to it with an hdmi cable.  The picture also shows what is next to it.  I have no idea what it means.  
Anyway, I need to know how to put an hdmi port on a computer (if this isn't one)
Thank you...............
That is DP (Display Port) not HDMI. 
On how to mark this thread as solve,
Please Click the "Solve thread" link below if this thread completely answered your query. Regards and cheers.

---

