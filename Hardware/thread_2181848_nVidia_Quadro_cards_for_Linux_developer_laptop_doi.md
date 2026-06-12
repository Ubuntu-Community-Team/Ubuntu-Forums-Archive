---
title: "nVidia Quadro cards for Linux developer laptop doing 3d modelling and CAE"
date: 2013-10-19
forum: Hardware
---

### Post by I.Bun.Tu on 2013-10-19
So I'm trying to build a laptop for general purpose developer usage inlcuding music recording, video editing, 3d modelling and running a host of other computer assisted engineering software as well as many other calculation heavy scientific software and simulation software. I will not be doing any gaming on this laptop. My emphasis is much more on detail and graphics quality than on speed.

From my understanding, GeForce cards have faster GPUs than Quadro cards but the drivers disable a lot of features. Quadro cards are preferred by developers because nVidia makes drivers that optimize the card's functionality for particular pieces of software. For example there are more than 4 Quadro drivers available in Windows all for different purposes.

For Linux however there is only one Quadro driver, and that leaves me wondering if most of the benefit of a Quadro card is in the drivers and nVidia doesn't care about Linux users: am I losing out on most of the benefit of buying a Quadro card by using Linux because nVidia is going to try to shiest me on the drivers?

Or does the single Linux Quadro driver just unlock all the features and leave the optimization to the user?

I posted this question under Ask Ubuntu ([http://askubuntu.com/questions/360809/how-do-nvidia-quadro-drivers-for-linux-compare-to-windows-drivers-for-a-develope](http://askubuntu.com/questions/360809/how-do-nvidia-quadro-drivers-for-linux-compare-to-windows-drivers-for-a-develope)) thinking it might be helpful to some other people but it seems that everything I've ever asked on Ask Ubuntu is much more suited to the forums. This is the only place I've gotten a response to my questions. Thanks for reading.

---

### Post by I.Bun.Tu on 2013-10-20
Are there not a lot of Ubuntu users with Quadro cards or not a lot of engineers using Ubuntu or have I been unclear about my question in some way? Please let me know if I can provide any more information. I am buying a new laptop in the next few days. If anyone knows a better place for me to seek advice, please point me in that direction. I figured Ubuntu forums would be best because when you mention Linux outside of Linux communities people tend to freak out and not off support... or even the range of people viewing your post is going to be mostly baren of Linux users.

Thanks so far 92+ viewers!

---

### Post by ragtag on 2014-01-31
I'm looking into this. Currently Nvidia delivers the same driver for both Quadro and Nvidia cards. I tried downloading the driver for Quadro K4000 and GTX 760, and they were binary identical. So there are two alternatives. Nvidia baked their Quadro optimized features into that one driver, or Quadro users on Linux are getting the short end of the stick.

The problem is how to test this. Most reviews and benchmark on the web are run on Windows. I've done some comparison between, K4000 and GTX 760. The results so far:

Blender Cycles CUDA render
GTX 760 = 16.7 sec
K4000 = 24.12 sec

Maya 2013 - viewport 2.0 with 10 million polys
GTX 760 - shaded - 92 fps
K4000 - shaded - 50 fps
GTX 760 - shaded & wire - 36 fps
K4000 - shaded & wire - 25 fps

From a 3D Mark test I found online.
[http://www.videocardbenchmark.net/gpu.php?gpu=Quadro+K4000]("http://www.videocardbenchmark.net/gpu.php?gpu=Quadro+K4000")
GTX 760 - 5009
K4000 - 2806

That's around 60% better performance on average for the GTX 760, which is around half the price of the K4000. In the 3D Mark test a GTX 780 card got a score of 7999, which is around 60% faster than the GTX 760 card again.

The advantages of the Quadro cards are supposedly better support in OpenGL CAD applications, a bit like Maya....but I'm not seeing it here. I tested things like paintFX, weight painting and other features that I figured might cause problem with a gaming card, but everything ran smooth. Another advantage is that they have 10bit output support, but this requires support from the OS, driver, card, screen and software you're using, so gets kind of specialized for most of us.

All this makes me lean towards the GTX cards.

---

### Post by ragtag on 2014-01-31
Running all the tests on [http://www.geeks3d.com/gputest/](http://www.geeks3d.com/gputest/) gives me on average 54% better results on the GTX760.

---

### Post by I.Bun.Tu on 2014-04-09
Thank you for offering some valuable information, Quadro users getting the short end of the stick is exactly what I'm worried about. I ended up finding a good deal on a budget laptop to tide me over in the meantime but I've been doing some research over the past few months.

I'm pretty dead set on using Linux for industry work despite the majority of developers using software that is only mac/windows compatible. I just despise those particular OSes (mainly the lack of admin under-the-hood control) and the idea of closed source too much to give in on any grounds (as in I'll find other contracts for work if I'm forced to use windows software before installing windows on another machine). That being said, nVidia doesn't seem to give too much care towards Linux and the development of their drivers, meanwhile AMD is towing in line with the open source band wagon and releasing their source code. This, their overall better relationship to Linux and the open source community have pushed me in the direction of following AMD and I'm probably going to invest in a FirePro card shortly despire developers being wary of how it holds up to the Quadro. If I'm using Linux it seems like I won't be getting to use my Quadro card really anyway.

Thanks again.

---

