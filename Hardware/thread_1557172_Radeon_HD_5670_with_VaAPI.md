---
title: "Radeon HD 5670 with VaAPI"
date: 2010-08-20
forum: Hardware
---

### Post by Maletor on 2010-08-20
I recently installed VaAPI onto Lucid with a Radeon 4xxx integrated card onto an HTPC. I installed the latest Catlyst drivers from the ATI website then the vaapi.deb and supporting dbg and dev packages along with XvBA and then installed XBMC from SVN and passed the --enable-vaapi flag.

This worked wonderfully and decoded x264 and played them back using VaAPI. 

Now I'm looking to do the same for my computer. The reason I want to do this is so that I can bitstream HD audio (DTS HD, DOLBY TRUE HD) to my receiver. 

So as far as I know I have to upgrade my graphics card because my NVIDIA 9800 GTX+ as awesome as it is, does not have HDMI which is required for bitstreaming HD audio.

My question is, will all this work. I'm looking into this HIS card [http://www.newegg.com/Product/Product.aspx?Item=N82E16814161319](http://www.newegg.com/Product/Product.aspx?Item=N82E16814161319)

I really hope that Catalyst is good enough to handle this. I noticed it didn't run as nicely as nvidia-settings did, but worked none the less. Also, it had serious tearing issues (and not working altogether) with compiz while trying to playback with VaAPI. So I disabled copmiz grudgingly. It did for some reason work with VDPAU.

Will Maverick have a VaAPI in the repository? I though I saw it in there but I can't find it again.

Let me know your thoughts on this.

Edit: This really just doesn't look ready for prime time. XvBA does not offer "true" video HD decoding (though it does work fine on the HTPC I installed on) -- as described by the guy who wrote it, it's glue. My guess is this would probably work on windows but who really wants to deal with that?  So I guess I'm stuck waiting until XvBA becomes a little better or NVIDIA makes a card that can bitstream.

Edit2: So I just realized they released they NVIDIA 460 which does HDMI 1.4 and bitstreaming HD audio. It's less than $200 and it does everything I need. Also, the drivers so 64 bit linux are out as of just a couple weeks ago. Good timing for me. I hope somebody finds this thread useful.

---

