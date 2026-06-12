---
title: "New Ubuntu install, video not quite smooth"
date: 2015-09-15
forum: Hardware
---

### Post by ra7411 on 2015-09-15
I just now installed U 14.04 on  a new desktop and everything has gone surprisingly easily, compared to 30 yrs of experience w/ Dos then Windows.

However, the video on Netflix, youtube, and a couple other vid sources is not quite smooth. There's just enough jerkiness to be noticeable. Audio seems fine.
During install,I did opt for the proprietary Java (I think), and I don't think that MS "silver whateveritis" that Netflix uses was put in.

This machine runs an AMD 4 core 3.8mhz, 8 gigs RAM, and a [COLOR=#000000][FONT=Arial]ATI Radeon X300 PCI-e x16 DVI Video Card.

Any ideas on how to fix this and smooth the video?

Thanks


[/FONT][/COLOR]

---

### Post by mikewhatever on 2015-09-15
That's not surprising, given the 11 years old graphics card (according to this wikipedia article: [https://en.wikipedia.org/wiki/Radeon_X300-X600_Series](https://en.wikipedia.org/wiki/Radeon_X300-X600_Series)).
Also, netflicx should work natively in Google Chrome, and does not require Silverlight, as for the proprietary thing, it's probably the codecs.

---

### Post by MAFoElffen on 2015-09-15
> **mikewhatever said:**
> That's not surprising, given the 11 years old graphics card (according to this wikipedia article: [https://en.wikipedia.org/wiki/Radeon_X300-X600_Series](https://en.wikipedia.org/wiki/Radeon_X300-X600_Series)).
Also, netflicx should work natively in Google Chrome, and does not require Silverlight, as for the proprietary thing, it's probably the codecs.

Quoted from the [Wiki]("https://help.ubuntu.com/community/RadeonDriver"):
> 
Fully Supported
All these Radeon(HD) cards and derivatives have good 3D acceleration support. This is not an exhaustive list:
<edited to show what was pertinent to this thread>
RV370                       Radeon X300, M22

But... Agreed that that does not say that model is of a high graphics quality that would be comparable to any Radeon card developed in the last 5 years. For instance, if we were talking another OS... some websites still require DirectX... and that card only supported DirectX 9... Do you have the 64 bit or 128 bit version of that card?

---

### Post by mikewhatever on 2015-09-19
> **MAFoElffen said:**
> Quoted from the [Wiki]("https://help.ubuntu.com/community/RadeonDriver"):

But... Agreed that that does not say that model is of a high graphics quality that would be comparable to any Radeon card developed in the last 5 years. For instance, if we were talking another OS... some websites still require DirectX... and that card only supported DirectX 9... Do you have the 64 bit or 128 bit version of that card?

3d support is good for desktop effects with Compiz, but to pay videos efficiently, you need to have acceleration support for various codecs.
Think June 2004 for a minute. What kind of online video was there?  I doubt any of the video codecs in use today were available back then.

---

### Post by Bucky Ball on 2015-09-19
*Thread moved to **Hardware**.*

---

