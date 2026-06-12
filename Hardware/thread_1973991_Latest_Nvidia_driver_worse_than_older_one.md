---
title: "Latest Nvidia driver worse than older one?"
date: 2012-05-05
forum: Hardware
---

### Post by dclement on 2012-05-05
Hello,

I am currently testing Ubuntu 12.04 Precise (on a USB key) against my current Lucid.

I have set up the Nvidia proprietary driver (how much more complicated under Unity!). It installed the brand new (295.40) version. Apparently the driver is working, but I'm disappointed at the results.

My laptop graphics card is a not-so-out-of-date QuadroFX2700M graphics card with 512Mo. glxgears reports about 3200-3500 FPS, whereas on my current setup (driver version 195.36.24) it is consistently around 7000-7500 FPS. The difference is obvious, e.g. under Googleearth.

So, how could I improve? Is it a matter of setup, or is the older 195.x driver definitely better for this card? But if the latter, who could help me to get back the older driver version?

TIA - regards, Daniel

---

### Post by gordintoronto on 2012-05-05
Hi Daniel,

I'm doing the same thing, testing 12.04 by running from a USB flash drive. Installed the nvidia-current driver using Synaptic. I had never run glxgears before.

My graphics card is a cheap 9400 GT, and my CPU is a Phenom II X2 running at 3.1 GHz. Scored 3700+ with the 295.40 driver. 

However, when I Googled "glxgears," the first response was, "glxgears is not a benchmark."

When I get a chance, I will see what glxgears produces with older versions of Ubuntu.

---

### Post by dclement on 2012-05-06
Hi,

It will be interesting to share our results.

Granted, glxgears is not a benchmark. But with a 50% loss in the results you just have to start Googleearth to be convinced. You know, when the program starts and you see the planet Earth closing in, it rather looks like an awkward polyhedron...

Now, while it looks simple to upgrade software, I don't fell as comfortable downgrading it, especially such a sensitive piece of software as a graphics driver.

---

### Post by down_quark on 2012-05-06
There's a [newer version 295.49 as well as a beta 302.07 that have been released]("http://www.nvnews.net/vbulletin/showthread.php?t=179882") you might want to try. You can also try 294.33 with [the patch]("http://www.nvnews.net/vbulletin/showpost.php?p=2546638&postcount=8").

```

mplayer -fs -benchmark matrix_sparring_h10.mkv > bench302_07.txt

``` 
I'm using this file to benchmark [mplayer2]("http://git.mplayer2.org/mplayer2-build/") [10 bit]("http://haruhichan.com/wpblog/index.php/205/hi10p-info-guide.html") playback thanks to andrew.46:
> **andrew.46 said:**
> **Edit:** BTW, stimulated by this thread I have investigated a little and created my own 10bit video from an episode of the Matrix movie. Check it out if you are interested:
```

wget http://www.andrews-corner.org/tmp/matrix_sparring_h10.mkv

``` 
Needs a little tweaking but the basics are in place :).

---

### Post by gordintoronto on 2012-05-07
With the same machine as mentioned previously, I run glxgears in Linux Mint 12 with Cinnamon, with the 280.13 driver, and the score was 4400+, an improvement of almost 20%.

---

### Post by dclement on 2012-05-08
Interesting. It could be that only 295.40 is affected by performance regression. There's been a newer (not beta) 295.49 which is supposed to address that.

I tried the 302.07 beta on a USB install, but I ended up with a blinking cursor. My guess is that the remaining memory on the USB is too low for X to start.

gordintoronto, did you use Unetbootin or startup disk creator to build your persistent USB? Mine was made with the latter, and is is only 4 Gb which might be too small.

---

### Post by gordintoronto on 2012-05-09
> **dclement said:**
> gordintoronto, did you use Unetbootin or startup disk creator to build your persistent USB? Mine was made with the latter, and is only 4 Gb which might be too small.

Neither, it's a real installation on an 8 GB flash drive.

First I used Unetbootin with no persistence on a 4 GB drive, then used that to install to the larger one. It gives me normal access to the files on the flash drive when running from the hard drive.

---

### Post by dclement on 2012-05-09
This is a smart method, I'll sure try it.

As for driver performance, I have come across [_the smxi script_]("http://smxi.org/").

It's a nice script that allows you to test various driver versions. It takes you through step by step instructions to let you choose the driver you want to test.

It's smart enough to stop the X server (necessary for installing) and take care of the download and dependencies.

With its help, I was able to test "for real" the 295.49 and 302.07 (beta) drivers. They perform similarly. glxgears doesn't show much improvement, but however the graphics performance is clearly improved when compared to version 295.40.

So I'm bound to think that this latter version really must be avoided.

Regards, Daniel

---

### Post by gordintoronto on 2012-05-09
To each his own. I don't notice any problem with the default driver, so I'll stick with it.

---

