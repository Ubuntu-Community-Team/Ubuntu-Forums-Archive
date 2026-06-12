---
title: "Is it possible to downgrade a laptop graphics card?"
date: 2008-09-25
forum: Hardware
---

### Post by kwilliam on 2008-09-25
Hi, I've got a Dell Inspiron 6400 (aka 1505) laptop with an nVidia GeForce Go 7300 graphics card. Ever since the release of KDE4 and all the ensuing problems with Nvidia graphics cards, I've begun to regret ordering the laptop with the nVidia card. There were three choices when I ordered the laptop: the Intel Graphics Media Accelerator 950, the ATI x1400 HyperMemory and the nVidia GeForce Go 7300. Is it possible to downgrade the laptop to the Intel GMA 950? Or some other way I can get an Intel graphics card to use it's open driver instead of nVidia and it's buggy blob?

---

### Post by phidia on 2008-09-25
Basically no. Laptops have soldered in video-mostly they're part of the motherboard.
You can't change the video configuration now. 

Maybe you can ask Dell if they would exchange that laptop for one with the video you want?

---

### Post by DrMega on 2008-09-25
> **kwilliam said:**
> Hi, I've got a Dell Inspiron 6400 (aka 1505) laptop with an nVidia GeForce Go 7300 graphics card. Ever since the release of KDE4 and all the ensuing problems with Nvidia graphics cards, I've begun to regret ordering the laptop with the nVidia card. There were three choices when I ordered the laptop: the Intel Graphics Media Accelerator 950, the ATI x1400 HyperMemory and the nVidia GeForce Go 7300. Is it possible to downgrade the laptop to the Intel GMA 950? Or some other way I can get an Intel graphics card to use it's open driver instead of nVidia and it's buggy blob?

Are you using the open source nVidia driver or the proprietary one? It may be that one works better than the other with your particular setup.

---

### Post by phidia on 2008-09-25
This sentence > Ever since the release of KDE4 and all the ensuing problems with Nvidia graphics cards, I've begun to regret ordering the laptop with the nVidia card. seems to imply video was working but if it was never set up correctly then check the [video wiki]("https://help.ubuntu.com/community/Video").

---

### Post by kwilliam on 2008-09-26
> **phidia said:**
> This sentence  seems to imply video was working but if it was never set up correctly then check the [video wiki]("https://help.ubuntu.com/community/Video").

I'm using the "nvidia" driver - the open source "nv" driver can't handle 3D accelerated effects. As for whether my card is set up correctly... yes and no. Things work, but there's all sorts of random nVidia specific glitches that KDE4 has helped bring to light, because KDE4 utilizes Xrender a lot and nVidia's support for that is suboptimal. (Examples: scrolling in Konsole results in copied lines everywhere, zooming in and out of Containments is incredibly slow, most 2D effects generally run slower and at lower framerate than on Intel graphics I hear.) Plus, I suspect it of being the culprit in suspend to RAM trouble, just little things like that.

Thanks for the replies guys, even if the answer is disappointing. I doubt Dell would replace the laptop, as it's a model from last year that's been replaced with a newer version.

---

### Post by ManyBeers on 2008-09-26
Is it possible to downgrade a laptop graphics card?

Yes it is. All you have to do is install Ubuntu.. LOL

---

### Post by pelle.k on 2008-09-26
> Yes it is. All you have to do is install Ubuntu.. LOL
Let me say that another way, wich is ultimately the source of the problem.
-"Yes it is. All you have to do is to install that buggy propreitary driver from the company that is nVidia."

---

### Post by phidia on 2008-09-27
Since a lot of people are using the nvidia driver successfully it's an interesting perspective to try to blame nvidia for any problems. 
I think the problems are a little closer and have nothing to do with nvidia.

The two previous posts belong in the community cafe-this is the help forum.

---

### Post by pelle.k on 2008-09-27
> The two previous posts belong in the community cafe-this is the help forum.
You are correct. I couldn't help myself, that's all.
However, it's well known that nvidia's linux drivers are sub-par compared to their linux windows counterpart. That said, i think they work good enough for the most part.

---

