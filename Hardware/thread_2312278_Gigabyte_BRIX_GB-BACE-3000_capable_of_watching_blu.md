---
title: "Gigabyte BRIX GB-BACE-3000 capable of watching blu-ray and youtube 1080p with ubuntu?"
date: 2016-02-03
forum: Hardware
---

### Post by ultragamer2 on 2016-02-03
Does anyone have one of these Gigabyte BRIX GB-BACE-3000?
[http://www.gigabyte.com.au/products/product-page.aspx?pid=5569#sp](http://www.gigabyte.com.au/products/product-page.aspx?pid=5569#sp)

If so is it possible to watch 1080p youtube videos and blu-rays without dropping frames in ubuntu?

It uses the Celeron n3000 cpu.

---

### Post by Vladlenin5000 on 2016-02-03
It's absolutely capable for any HD video.
BD support for Linux is far from ideal and require some tweaks. I won't comment on this because it deserves a completely separate discussion.
YouTube should would beautifully. I have tested several less powerful (and older) similar 'bricks' with zero issues.

What issues are you having exactly? What browser are you using for YT? Old Flash or HTML5?

---

### Post by ultragamer2 on 2016-02-03
No issue, but there was one on special for 20% off I believe just for today (probably no one would be able to reply to this in time to decide).

I have an Intel NUC Kit DN2820FYKH and that can't play the youtube 1080p test videos smoothly on linux. So I had decided not to buy the BRIX GB-BACE-3000 because I assume it wouldn't play smoothly either on linux and I don't want to buy windows.
If anyone could confirm that is does work I could buy one today, otherwise I'll leave it and look for something else in the future.

If anyone has a brix GB-BACE-3000 or another system with the Celeron N3000 cpu running linux, could you possibly go to youtube.com and look for "1080p test" and see if it drops frames?

Thanks

---

### Post by Vladlenin5000 on 2016-02-03
Actually the NUC DN2820FYKH has roughly the same specs (or better) as the ones I mentioned before
> I have tested several less powerful (and older) similar 'bricks' with zero issues.
_All 15 unbranded boxes directly imported from some unknown supplier in China via the Alibaba portal, all equipped with small 128GB cheap Chinese SSDs and the cheapest Kingston 1*4GB DDR3L RAM..._
1080P video issues (local MKV file or Youtube): ZERO

As such I can confidently tell you that:
a) Your assumptions are completely wrong.
b) There's something very wrong with your installed Ubuntu* -and/or- with the browser you're using (addons, perhaps?) -and/or- with your Youtube account settings**


* Unless, of course, it's somehow defective with some rare and weird hardware problem. Unlikely because you 'd most likely be experiencing other issues as well.
** HTML5 ONLY!!! Do NOT use the old Flash, especially with Firefox.

---

### Post by ultragamer2 on 2016-02-04
Thanks for the info. The NUC DN2820FYKH I had in another room used for mostly old movie viewing. But I brought it in and connected it to the internet and found playing a youtube video in firefox in Lubuntu (all updated) (not logged into youtube so with default settings) it was dropping a lot of frames when running this video in 1080p that made it unwatchable (at that resolution).
[https://www.youtube.com/watch?v=1-UdWS4RAA4](https://www.youtube.com/watch?v=1-UdWS4RAA4)

I also saw this video review
[https://www.youtube.com/watch?v=t3EFEqiHA8g](https://www.youtube.com/watch?v=t3EFEqiHA8g)
And he says it drops frames (this is another model of course but similar I think it's a similar speed).

It's not too late to get the Gigabyte BRIX GB-BACE-3000 on special if it could watch 1080p youtube videos (and other streaming videos) without dropping any frames or slowdowns with any linux distro (I don't mind which one).



Update: Ok well I ordered one (BRIX GB-BACE-3000) so hope it works ok with 1080p youtube using ubuntu and firefox. Otherwise I can just watch 720p but it would be slightly disappointing if I had to.
Is there any reason Ubuntu would be better at firefox youtube playback than Lubuntu?
Lubuntu didn't detect any additional drivers for the gpu with my intel nuc DN2820FYKH so I hope it can with this Brix. :/

---

### Post by ultragamer2 on 2016-02-11
Ok I got the Gigabyte BRIX GB-BACE-3000.

It can play 1080p youtube videos in Chromium at about 70% - 80% cpu usage but it maxes out the cpu and jumps a lot in firefox. Update: with software rendering it drops frames.
It's a shame because I wanted to use the firefox adblocker, I hope there is one in chromium, I just want to block the video ads from coming up, any ideas? Or I could try another browser if anyone has a good suggestion?

Theres probably no use trying to fix the firefox problem because I wouldn't have the expertise to even guess what could be wrong with firefox in this system. But it's the exact same problem with my intel nuc DN2820FYKH, can't watch 1080p youtube videos with firefox.

I'm using Lubuntu on both computers 8gb of ram in the brix, 4gb in the nuc.

---

### Post by Vladlenin5000 on 2016-02-11
Again, Flash or HTML5?

If you don't know the difference just right-click the video.

---

### Post by ultragamer2 on 2016-02-11
Html5.

---

### Post by Vladlenin5000 on 2016-02-11
Well, nothing to add to post #4.
I'm baffled unbranded miniPCs directly imported from China are performing better than one from such reputable brand (and probably way more expensive). Live and learn...

---

### Post by ultragamer2 on 2016-02-11
Update 2.

I installed some Intel HD drivers with a utility you can get online then I followed an instruction to override software rendering in Chromium flags settings.

After that I think it is made just fast enough to watch nearly all of the few 1080p test videos I watched in chromium. The cpu usage fluctuates between about 75% to 100%, getting near or reaching 100% in the most demanding bits of demanding hd 1080p test videos.

[https://www.youtube.com/watch?v=Eho8HDtkCiU](https://www.youtube.com/watch?v=Eho8HDtkCiU)
In this video it appears to get to 100% usage with the mountain flyover scene, so for general watching it seems just fast enough, maybe just not quite fast enough to never drop any frames but I'll have to do some more tests to be sure. Before without the hardware acceleration it couldn't handle the water bubbles and ripples at all, now it can.

So it's much much better than before when 1080p was unwatchable.

If anyone is running either of these brixs or nucs in windows, could you say what the cpu usage gets to in the mountain flyover in that video.
If it does drop the occasional frame I kind of wish I got one that was just 10% faster.

Anyone know if I could squeeze out a few more percent of cpu usage by using a linux distro that is lighter than Lubuntu but still supports the drivers here?
[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

---

### Post by ultragamer2 on 2016-02-12
Ran lots of test videos, I can't get it to play 1080p without stopping fairly often and maxing out the cpu.

It can only do 720p, that's all with hardware acceleration turned on in Chromium via a complicated workaround.
Apparently the cpus are soldered in so I guess I'm stuck with only 720p until I buy another computer.

Although an interesting observation is that when running in Chromium it takes about 70% - 80% percent of the cpu (with hardware acceleration) to play a 720p video, but if you paste the link into vlc it plays it with only about 25% - 29% cpu usage.
If there is no other reason for this it could indicate that the brix and nuc could maybe be capable of 1080p playback but not with the current browsers (Chromium/Firefox), unless I am forgetting something.

---

### Post by gordintoronto on 2016-02-12
You must have a faster-than-DSL Internet connection to play 1080P videos while online. I was surprised that my 7-year-old desktop played the sample videos quite smoothly fullscreen at 1080P. Standard DSL connection, AMD Phenom II X2 at 3.1 GHZ, Geforce 9400 GT video, driving a fairly new Dell Ultrasharp monitor. 55% CPU usage in Chrome, and the temperature of the video card jumped by 5C.

Sorry, it's irrelevant to your actual question. However, it shows how Intel has concentrated on lower power and more cores, rather than faster CPUs. I don't want 16 cores at 3 GHz, I want 3 cores at 16 GHz!

I use a different test video. I connected to Vimeo and searched for "mobius 1080P" and downloaded the video. Then I play it from the hard drive or a USB flash drive. It really displays the wonders of a great monitor.

---

### Post by Vladlenin5000 on 2016-02-12
+1 to the above post.

Plus any of this "new celeron" based mini PCs runs circles around the any 2014 entry level AMD APU laptop and those also play 1080P Youtube flawlessly as well as any current tablet or other ARM based Android media player. Of course, the latter is comparing apples with oranges but even so...

ultagamer2, the more I think about it the more I'm convinced there's something wrong somewhere with hardware or OS. For the aforementioned 15 I tested standard Ubuntu (with Unity) was used, arguably a more resources intensive DE then the XFCE you'd find in Xubuntu.

---

### Post by ultragamer2 on 2016-02-12
Thanks for all the info.

I was letting the youtube video buffer properly before playing it so I wasn't mistaking slow internet buffering speed for gpu performance, also the cpu was maxing out when it jumped/skipped.

I'm using a standard Lubuntu installation, I have enabled hardware acceleration in Chromium. I seem to be getting much better video performance in VLC than chromium or firefox (assuming it's loading the same stream/codec).
I can't load 1080p videos in any other app than the browser though, I  believe it has something to do with how youtube split up the stream.

I hope maybe there is some issue or with the current drivers/ browser versions, it's no big deal if I can't watch 1080p at the moment and have to wait for some more software updates, I'd just like to think I can watch it at some stage without buying another new computer. :/

Another issue could be the newer VP9 codec (if the cpu's integrated gpu lacks decoding capability) but I tested it with a chromium addon to make it use the older h264 and it was the same performance level (maxing out cpu at 1080p).

I also increased the minimum video memory from 32mb to 512mb but didn't seem to make any difference either.

Also I get almost the exact same performance level from the other intel nuc 2820 I have.

---

