---
title: "Latest Nvidia driver"
date: 2004-11-25
forum: Hardware &amp; Laptops
---

### Post by Rancoras on 2004-11-25
Up until yesterday, I was using a Geforce FX5200 with no issues with the driver included with Warty.

I need the latest nvidia for my new Geforce 6600GT.  6299 is the driver that ads support for my card.  Right now X hangs while the nvidia splash is on the screen.  When the hang occurs, the splash image breaks up into many pixels (hard to explain) and then everything freezes.  The only thing to do at that point is press the power button.

Has anyone been able to successfully install this driver downloaded from the nvidia web site?  If so, how did you accomplish this?

---

### Post by daniels on 2004-11-25
Could you please test the latest linux-restricted-modules?  I added nVidia's 6629 driver with a couple of patches that allegedly fix this sort of thing.  Unfortunately, I own no nVidia hardware, so it might make things even worse.  Ho hum.

```
deb http://people.ubuntu.com/~daniels/ l-r-m/$(ARCH)/
```

Cheers.

---

### Post by Rancoras on 2004-11-25
Cool, that got me back into X.  So far so good.  I'll let you know if anything changes.

Thanks for the quick reply.

---

### Post by ubuntu-geek on 2004-11-28
[QUOTE=daniels]Could you please test the latest linux-restricted-modules?  I added nVidia's 6629 driver with a couple of patches that allegedly fix this sort of thing.  Unfortunately, I own no nVidia hardware, so it might make things even worse.  Ho hum.

```
deb http://people.ubuntu.com/~daniels/ l-r-m/$(ARCH)/
```

Cheers.[/QUOTE]
 Installed this on my warty box running a nvidia card, when it loads up X the nividia screen never goes away but i can hear the sounds of the gdm screen erroring when i type something...


Thought I would share.. :)

---

### Post by daniels on 2004-11-28
[QUOTE=ubuntu-geek]Installed this on my warty box running a nvidia card, when it loads up X the nividia screen never goes away but i can hear the sounds of the gdm screen erroring when i type something...[/QUOTE]... weird.  Someone replied that they had a similarish issue with plain 6629, but 6629 plus the two patches I included fixed it.  Hooray for binary drivers, eh?

---

### Post by Rancoras on 2004-12-11
Ok, something is wrong.  See this thread:  [http://ubuntuforums.org/showthread.php?t=7635](http://ubuntuforums.org/showthread.php?t=7635)

I hadn't checked any opengl apps yet.  Seems that both DyDx and I have the same problem with the same card and same driver.  Any ideas?

---

### Post by daniels on 2004-12-11
Not really; as I said before, I don't own any nVidia hardware, and while I'm away from home (which I have been for 6 weeks, and will be for almost another 2), all I have is the i855 in my laptop.

---

### Post by Rancoras on 2004-12-11
Well, when I first got the card, I tried getting the headers and source for the kernel I'm running (ubuntu-k7).  I was never able to use the driver that you can download from nvidia's site.  I can't remember the errors I was getting.  Should I try again and post the results?

---

### Post by daniels on 2004-12-11
Probably might help others debugging it, but yeah, I've never used it, and don't have the hardware to do so, so I'm afraid I won't be of much use.

---

### Post by malstx6095 on 2007-05-15
> **Rancoras said:**
> Well, when I first got the card, I tried getting the headers and source for the kernel I'm running (ubuntu-k7).  I was never able to use the driver that you can download from nvidia's site.  I can't remember the errors I was getting.  Should I try again and post the results?


[plants plants Google blood pressure Britney Spears](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---

### Post by Xtsy on 2007-11-28
i have the same problem. The only difference is that during the install everything is working ok, but after the instalation i get a weird funky looking screen. As far as i can tell i have the same problem as you guys. so i have a different question. which linux distribution supports nvidia geforce 6600gt on PCI-E?

---

### Post by PmDematagoda on 2007-11-28
Did you install the Nvidia drivers via the Restricted Drivers Manager?

---

