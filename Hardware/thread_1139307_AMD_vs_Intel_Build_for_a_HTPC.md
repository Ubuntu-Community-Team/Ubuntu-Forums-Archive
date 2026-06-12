---
title: "AMD vs Intel Build for a HTPC"
date: 2009-04-26
forum: Hardware
---

### Post by Spectre5 on 2009-04-26
I'm looking at building a computer to use as a web server and for boxee/MythTV/something similar.  I've decided on most components for this computer.  I have two configurations, one of which uses AMD and the other one that uses Intel.

Here are the two builds (the intel build is just $10 more)
AMD:
AMD Athlon 64 X2 5050e Brisbane 2.6GHz 2 x 512KB L2 Cache Socket AM2 45W Dual-Core Processor - Retail
<http://www.newegg.com/Product/Product.aspx?Item=N82E16819103298>
ASUS M3N78-VM AM2+/AM2 NVIDIA GeForce 8200 HDMI Micro ATX AMD Motherboard - Retail
<http://www.newegg.com/Product/Product.aspx?Item=N82E16813131318>

Intel:
Intel Pentium E5200 Wolfdale 2.5GHz 2MB L2 Cache LGA 775 65W Dual-Core Processor - Retail
<http://www.newegg.com/Product/Product.aspx?Item=N82E16819116072>
GIGABYTE GA-73PVM-S2H LGA 775 NVIDIA GeForce 7100 HDMI Micro ATX Intel Motherboard - Retail
<http://www.newegg.com/Product/Product.aspx?Item=N82E16813128072>

I would like the know the following information:

Which would use less power (I know the amd is 45W and the intel is 65W, but including the mobo and actual experience with these)

Which would be more powerful/better for video decompressing, boxee/MythTV, etc, etc?

Is the on-board nVidia 7100 for the Intel build good enough?  How about the on-board nVidia 8200 on the AMD build?  Are both/either/neither good enough for 1080i or 1080p video?  Note also that both of the mobo's have HDMI which is one of my requirements.

I've been unable to find good information comparing these two even though they seem pretty comparable to me...both are close in price, close in frequency, the intel has twice as much L2 cache though.

Thanks for any help!

Note:  This is not intended to be an AMD/Intel flame-war - so please don't say one is better than the other simply because it is AMD or Intel, please provide some reasoning/support/links for the answer.


EDIT:  hm...for the same price (actually $1 cheaper right now), I could get this AMD instead:
AMD Athlon 64 X2 7750 Kuma 2.7GHz 2 x 512KB L2 Cache 2MB L3 Cache Socket AM2+ 95W Dual-Core black edition Processor - Retail
<http://www.newegg.com/Product/Product.aspx?Item=N82E16819103300&Tpk=7750>

Would there be any reason to not do this?? This one seems like it is better than the one in my post above - although it is 95W instead of 45W.

---

### Post by digitalgenicide on 2009-10-17
I just built an HTPC pretty simular to your AMD build and i,ve been having some peoblems with the M3N78-VM MOBO. Video is pretty good thru HDMI but trying to get audio thru the HDMI is a serious pain in the ***. I,ve been trying for like 10 hours now  and i still cant hear a thing. I,ve read alot for other people having the same problems as me. But there were a few success stories. Im not sure how well the Gigabyte board is supported u might want to search it in the forums and see if it works for anyone else.

---

### Post by paulisdead on 2009-10-17
I would tailor the system around the video card and get one that can do VDPAU well, and use it to decode video.  The CPU becomes irrelevant then.  You need at least an 8x00 Nvidia GPU to do it, though not all of them work as well.  There's plenty of info on VDPAU around, so you should be able to find what you need.

The Intel chip will probably run cooler, if that matters to you.  Since it's an htpc build, I'll assume you want low speed fans to keep the noise down.  AMD has Cool N Quiet, so you should still be able to keep the heat to a reasonable level even in a fairly compact case with it.  Both are fine options, but I lean more towards intel if you can spare the cash right now.

---

### Post by sloggerkhan on 2009-10-17
> **paulisdead said:**
> I would tailor the system around the video card and get one that can do VDPAU well, and use it to decode video.  The CPU becomes irrelevant then.  You need at least an 8x00 Nvidia GPU to do it, though not all of them work as well.  There's plenty of info on VDPAU around, so you should be able to find what you need.

The Intel chip will probably run cooler, if that matters to you.  Since it's an htpc build, I'll assume you want low speed fans to keep the noise down.  AMD has Cool N Quiet, so you should still be able to keep the heat to a reasonable level even in a fairly compact case with it.  Both are fine options, but I lean more towards intel if you can spare the cash right now.

I'm a skeptic that a 65 Watt CPU will run cooler than a 45 Watt, though supposedly for intensive tasks the newer intel dual cores do have beter performance/watt, otherwise have to agree that 8x00 or 9x00 series nvidia with VDPAU will be really excellent if the box is going to do decode/render of video itself. (If it's just going to serve data streams, the integrated video won't matter, though.) I think something to consider might be how much time the computer will spend idling.

---

### Post by Spectre5 on 2009-10-18
> **digitalgenicide said:**
> I just built an HTPC pretty simular to your AMD build and i,ve been having some peoblems with the M3N78-VM MOBO. Video is pretty good thru HDMI but trying to get audio thru the HDMI is a serious pain in the ***. I,ve been trying for like 10 hours now  and i still cant hear a thing. I,ve read alot for other people having the same problems as me. But there were a few success stories. Im not sure how well the Gigabyte board is supported u might want to search it in the forums and see if it works for anyone else.

Hey, you just revived a long-dead post!  :)

I actually ended up going with the exact same AMD with that motherboard.  I had the EXACT same problem as you - the HDMI video was great, but I tried EVERYTHING to get the audio to work (spent DAYS) and was never successful (sadly, I borrowed a windows CD from a friend to get it with windows, and it worked right away...so I knew it COULD work).  But with Ubuntu, I could never get it to work and I have zero desire to run windows on it.

I'm sure some of the discussions you read about it on the forums involved me...I was involved in a number and I tried everything that people suggested, and any mix of them as well.  I must have re-installed ubuntu/xubuntu/several other linux distros a couple dozen times to make sure I was starting "fresh."  I never got it to work and I ended up just use an audio out to component audio for the TV (the TV lets me choose to use the HDMI audio or component audio).  Good luck - and if you get it to work, PLEASE do re-post here or PM me, I'd be curious as to what you did.

FYI - I noticed that there is another new ALSA driver out now, the 1.0.21, so maybe that will make a different?  I was trying with *.18, *.19, and *.20 without success.

---

### Post by cascade9 on 2009-10-20
> **paulisdead said:**
> I would tailor the system around the video card and get one that can do VDPAU well, and use it to decode video.  The CPU becomes irrelevant then.  You need at least an 8x00 Nvidia GPU to do it, though not all of them work as well.  There's plenty of info on VDPAU around, so you should be able to find what you need.

The Intel chip will probably run cooler, if that matters to you.  Since it's an htpc build, I'll assume you want low speed fans to keep the noise down.  AMD has Cool N Quiet, so you should still be able to keep the heat to a reasonable level even in a fairly compact case with it.  Both are fine options, but I lean more towards intel if you can spare the cash right now.

I agree on the VDPAU. If you've got that, CPU power is far less important. 

If people are interesting in low power though, I would go AMD, get an unlocked CPU (like the X2 7750 black edition), and underclock it to about 1.2Ghz. It will use a lot less power then, and still work fine for a HTPC boxxen.

---

### Post by digitalgenicide on 2009-10-20
I tried for like a day after i posted but i still couldn't get HDMI audio to even make a peep. I ended up just installing windows 7 (Never been a fan of Windows and 7 reminded me why). I installed Fluxbuntu in virtual box with only 512 mb of ram and it runs way faster then 7. Audio also worked in virtual box right from install.  Hopefully This issue will be resolved in the up comming release. Ubuntu would make a way better foundation for an HTPC then windows ever could, But Without Audio its meaningless.

---

