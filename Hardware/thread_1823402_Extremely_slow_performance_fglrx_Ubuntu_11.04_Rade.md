---
title: "Extremely slow performance fglrx Ubuntu 11.04 Radeon HD 4550"
date: 2011-08-12
forum: Hardware
---

### Post by UCSBGauchosRock on 2011-08-12
I am getting incredibly slow performance on my Radeon HD 4550 using the proprietary fglrx driver.... A little bit better with the open source ati but still pretty bad. Also on bootup, it is just a purple screen with the ubuntu logo located in the top right after a little while. I love the fglrx driver and the fact it supports all of the features that come with the graphics card but is there a fix for this?

EDIT: It is actually performing worse than my GMA950 :(

---

### Post by UCSBGauchosRock on 2011-08-16
bump

---

### Post by coffeecat on 2011-08-16
Hi, I have an ATI Radeon HD4350 which according to this chart:

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Radeon_R700_.28HD_4xxx.29_series](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Radeon_R700_.28HD_4xxx.29_series)

... is the same chipset as yours but with lower specs. Mine meets all my needs in 11.04/Unity. Good compiz, no lagging and full HD video playback - all with the open source driver. However, I do not game, so if you are a gamer your needs would be more demanding than mine. In what way is the performance slow?


> **UCSBGauchosRock said:**
> Also on bootup, it is just a purple screen with the ubuntu logo located in the top right after a little while.

I presume this is with the fglrx driver?

---

### Post by UCSBGauchosRock on 2011-08-17
There is a huge scrolling lag on most websites, with heavier flash. I do play games like Nexuiz too. 

Everything else is relatively manageable, and some images on websites turn black after scrolling. For example like FunnyJunk, and sometimes Imgur and  does that a lot with the higher quality images, and refreshing doesn't help. 

Just extremely annoying that I can't switch what driver I use on the fly otherwise I would switch between open source and proprietary depending on my need quickly but I know one conflicts with the other.

---

### Post by UCSBGauchosRock on 2011-08-18
So I stopped dealing with ATI graphics and just went and got a NVidia GT520 and problem solved. It's a shame ATI's drivers aren't nearly up to par as NVidia's

---

### Post by Gs Dewd on 2011-08-18
I'm running a ati card. I am using whatever drivers are installed when you install 11.04 and I haven't had any problems what so ever. I haven't seen a need to install any other drivers. I am starting to wonder if it is not so much of the Graphics card drivers causing problems but maybe it being the motherboard chipset drivers causing some of the problems people are having.

---

### Post by coffeecat on 2011-08-19
> **Gs Dewd said:**
> I'm running a ati card. I am using whatever drivers are installed when you install 11.04 and I haven't had any problems what so ever. I haven't seen a need to install any other drivers.

The "whatever" driver is the open source ati driver provided by the xserver-xorg-video-ati package. (Actually - it's a bit more complicated than that - the ati package loads one of the mach64, r128 or radeon drivers depending on your card.) People who need the more demanding 3d performance that many games require usually need to install the proprietary driver. Out of interest, which particular card do you have? Different people's experiences do seem to vary and, as you say, there could be other factors. If you're not sure of your GPU type, run the terminal command:

```
lspci | grep VGA
```

---

### Post by Gs Dewd on 2011-08-19
In one system I have a hd 4890 and in another I have a x1550 xge. And with both I have not had any problems. But I also Don't game under ubuntu, but I do under windows.

---

### Post by coffeecat on 2011-08-20
> **Gs Dewd said:**
> In one system I have a hd 4890 and in another I have a x1550 xge.

Thanks for posting that. My guess is that all the 4*** series should work just OK with the open source driver. I'm sure there must be some other issue apart from the video driver affecting the OP's video card. The x1550 is now of an age where ATI/AMD have stopped releasing a Linux proprietary driver for it, so one has to use the open source one for it. Good to know you are not getting any problems.

---

