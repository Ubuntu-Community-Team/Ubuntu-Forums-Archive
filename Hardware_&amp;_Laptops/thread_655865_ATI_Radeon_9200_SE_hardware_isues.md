---
title: "ATI Radeon 9200 SE hardware isues"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by Flarkis on 2008-01-01
Ok to start the video card i am using is a Radeon 9200 SE PCI. As soon as i atept to run linux from a live CD it fails mid way through loading the bar. I removed my video card so the computer would use the built in chip instead. I was able to successfully install ubuntu without my card in. When i ran ubuntu from the hard drive in recovery mode with the card in it crashed when it got to loading hardware and gave alot of code i didn't understand. So i used envy to install different ati drivers. All of the drivers i installed either gave me the same error messages when i put video card back in. Or it fails to install the driver.

I have been attempting to figure this out for about a week now using other forum posts and other resources. I would greatly appreciate some help.

---

### Post by bwang on 2008-01-02
Can you please post the error messages it gives you?

---

### Post by Flarkis on 2008-01-02
The envy log from:
/var/log/envy-installer.log

```
python pulse.py ati oldest 
root@Bobby:/usr/share/envy# python pulse.py ati oldest
Envy - Version 0.9.9
Ubuntu Gutsy 32bit
ENVY ERROR: ATI's legacy driver does not support your operating system
ENVY: Operation Complete
```

hope that is what you are talking about.

---

### Post by beachedwhale on 2008-01-02
I get the same error (same card as you).  If I choose manual install, I can get past that error, but then it still doesn't work for me (envy does its thing and completes, but I still don't have working video).

All the details are in this thread I started:

[http://ubuntuforums.org/showthread.php?t=655311](http://ubuntuforums.org/showthread.php?t=655311)

---

### Post by Flarkis on 2008-01-02
Yes my big problem though is that i cant even get into linux with my card pluged in. The drivers just decide not to work. I actualy used your topic as a reference when i was trying to figure mine out. 

Where you able to actualy boot into ubuntu with the live CD with out any changes. and if you did have to make some changes would you mind listing them to help me with mine.

---

### Post by beachedwhale on 2008-01-03
The LiveCD booted for me just fine using the generic drivers.  The initial install also worked fine and with the same generic drivers.  Its only when I started trying to make full use of the video card did everything fall apart.  Fortunately, its pretty easy to boot up on text-only mode and switch back to the original xorg.conf each time I broke the video.  But, I have no idea how to solve our problems.  I'm going to order a different video card. I'm not sure what you'd do... having onboard video could be complicating things (but how?  no idea!).

---

