---
title: "Sandy Bridge IGP 1080p with the integrated graphics on Ubuntu 11.04"
date: 2011-05-05
forum: Hardware
---

### Post by unityemissions on 2011-05-05
Hey All,

I just put together a small rig which is running Ubuntu 11.04. 

It's the i3-2100T Sandy Bridge processor, and I'm running off the integrated graphics controlled, hd2000. 

I installed the system and attempted to upgrade the graphics to latest 185 version in the software center, but I couldn't get xorg to load. The screen is simply blank after restarting. 

So it doesn't seem to be a problem leaving it with the default settings on. My monitor defaults to 720p, which is okay, and it plays high bitrate videos with ease. The issue is that my monitor is full 1080p, and without having official support for the graphics, the monitor won't toggle to 1920x1080 resolution, so I can't watch 1080p until this is resolved. 

Has anyone figured out how to get the integrated graphics controller that comes on sandy bridges to work properly with ubuntu?!

I can follow whatever terminal commands someone might give, I'm just not techie enough to go reading books to figure this all out. Appreciate any support someone may offer. 


Thanks! .

---

### Post by unityemissions on 2011-05-05
Solved!

I used this guide to add more resolution options for the HDMI port:

[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

Now I'm off to save ./profile so it auto sets res to 1080p upon login

---

### Post by Jared Norris on 2011-05-16
Thank you so much for reporting how it went.

As someone who is very interested in purchasing this processor for a low powered desktop replacement I was wondering if you could spare some time to test a couple of things for me (if you haven't already tried these).

1) Does it handle 1080p video ok on the integrated video?
2) Does it handle *shudder* flash on websites ok (even HD content?)

Do you think (or can you test) if it could play low end games like Urban Terror (native linux games are awesome) with the integrated graphics?

Thanks so much for your time.

---

### Post by turqoisehex on 2011-06-03
The method described works OK, however it doesn't address the root of the problem, which is the video drivers. What worked for me, is to update the integrated drivers to 7.11 (7.10 is what ships with Natty) by doing the following:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

Then restart the computer (or just X with Alt+PrintScrn+K)

Then make sure "share image on all monitors is unchecked"

And the new drivers should detect the monitors correctly (along with being able to display better than 2D graphics)

---

### Post by stoumpos on 2011-06-05
Hi, I tried the same ppa, but I still cannot change resolution.
What do you mean by version 7.11? I only see the following:

> 
sudo apt-cache policy xserver-xorg-video-intel
xserver-xorg-video-intel:
  Installed: 2:2.15.0+git20110531.340cfb7f-0ubuntu0sarvatt2~natty
  Candidate: 2:2.15.0+git20110531.340cfb7f-0ubuntu0sarvatt2~natty
  Version table:
 *** 2:2.15.0+git20110531.340cfb7f-0ubuntu0sarvatt2~natty 0
        500 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) natty/main amd64 Packages
        100 /var/lib/dpkg/status
     2:2.14.0-4ubuntu7.1 0
        500 [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) natty-updates/main amd64 Packages
     2:2.14.0-4ubuntu7 0
        500 [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) natty/main amd64 Packages


---

