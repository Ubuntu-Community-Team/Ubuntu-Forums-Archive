---
title: "My processors are maxing out"
date: 2014-11-25
forum: Hardware
---

### Post by xmjsilverx on 2014-11-25
I am running Ubuntu 14.04 on my HTPC using an Amd A-Series APU A6-6400K  BLK EDT 3900Mhz and 4GB Ram.  I do not have a separate video card.  I  had noticed that the system seemed unusually slow with this set-up from  the beginning but it seems to be getting worse.  When using xbmc it lags  out to the the point where I can't use the directional pad to select  anything for minutes at a time.  I found that usually one of the 2  processors was maxed out at 100% during these issues.  I thought it was  only an xbmc issue and submitted a debug log and got no help.  I was  messing with it outside of xbmc, I played an HD movie that was stored on  the computer and watched another HD video on youtube and they both hit  100%, with just one playing they were around 78%.  The only program I  know running besides these was the myth-tv backend.  From what I had  read, the processor set-up I went with was overboard if anything.  Is it  possible I got a bad processor or is something causing them to bog  down?  Here is a screen shot of the system monitor with 2 HD movies  playing.  On a side note, occasionaly the audio is messed up and sounds muffled and vibraty.  Any ideas on that either?  A restart fixes that.
[IMG]http://i181.photobucket.com/albums/x40/xmjsilverx/20141119_195425_zps8c5f3221.jpg[/IMG]

---

### Post by Yellow Pasque on 2014-11-30
Playing HD videos is going to use the CPU, and if video acceleration isn't working, it's going to use a lot of CPU. Do you max out the CPU when not playing video? If so, use htop to figure out what is causing it.

What video driver are you using (open source or the proprietary Catalyst/fglrx)? If you're using open-source driver, do you have vdpau set up properly? (Look at vdpauinfo):
```
sudo apt-get install vdpauinfo
vdpauinfo
```

---

### Post by xmjsilverx on 2014-11-30
Thanks for the reply.  I was told I went way overboard with my processor for building an HTPC so I assumed playing HD videos would be easily accomplished with it.  I was planning on installing up to 4 tuners which would allow me to watch 4 shows from the same backend.  When I am watching TV using XBMC or really using anything on XBMC I have terrible lag issues and when watching the processors one of them is always hitting 100%.  I am not sure what htop is but I will look into it.  I will look into all of this stuff tomorrow.  Thanks again.

---

### Post by xmjsilverx on 2014-12-01
Ok, I installed and ran htop while playing 1 HD movie.  A few times it spiked to near 100% but stayed around 60-70% the majority of the time.  I am using an AMD proprietary driver for video so I am guessing I don't need to look at vdpauinfo.  I am not sure what everything means when reading the processes on htop so I posted a pic.  This is while the HD movie is playing.  I noticed the top process was always showing 100% or more.  I am not saying you are wrong but from what I read and people I talked to on XBMC, they are saying this processor is overkill so if that is the case, I don't think watching one movie on an HTPC with an overkill processor should be running at 70%, that doesn't really leave room for recording shows and doing anything else like browsing the electronic program guide.  If you are correct and I need a better processor I have no problem going that route, I just want to make sure that is going to fix it.
[IMG]http://i181.photobucket.com/albums/x40/xmjsilverx/20141201_152959_zpsfogbt6wh.jpg[/IMG]

---

### Post by xmjsilverx on 2014-12-01
Ok, I may have figured something out.  I was monitoring xbmc with xbmc system monitor, htop, and ubunutu system monitor.  I noticed that it all seemed fine when I was in the windowed view of xbmc but when going to full screen it all went crazy like usual.  As soon as I entered full screen the processors took truns bouncing off 100% or close to it, you can see it on the xbmc monitor and on the system monitor graph when I exit.  So what does this mean?  Do I just need to reinstall xbmc?
Here is a link to the video.
[http://vid181.photobucket.com/albums/x40/xmjsilverx/20141201_160659_zpskt0krslf.mp4](http://vid181.photobucket.com/albums/x40/xmjsilverx/20141201_160659_zpskt0krslf.mp4)

---

### Post by mastablasta on 2014-12-02
the processor is overthetop. XBMC runs on raspberry Pi with 700Mhz CPU that runs like 350Mhz Pentium 2.

anyway - htop is hswoing many totem processes opened. someone else that is using this would be able to explain if this is normal or not.

but what bothers me is I see you are using unity desktop and then add xbmc desktop to it. I am a bit puzzled as to why you need the desktop if this is HTPC. have you tried installing only xmbc on it? orxbmcbuntu or something like that.

on raspberry pi there is a lot of optimisation needed like turning off the RSS and similar. this shouldn't be needed with this CPU but i am not sure what it means if it has many things from regular desktop running in background.

---

### Post by xmjsilverx on 2014-12-02
I used ubuntu because I am more familiar with it.  I initially installed xmbcbuntu but I felt lost with it.  I got a response on the xbmc forum and he thinks it is a problem with my video driver so I am going to try installing the radeon oss.

---

### Post by Yellow Pasque on 2014-12-05
The proprietary driver could do some decode acceleration through the xvba-vaapi wrapper: [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Using_the_xvba-va_driver_.28VA-API.29](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Using_the_xvba-va_driver_.28VA-API.29)
Supposedly, an upcoming Catalyst release will support VA-API directly and eliminate the need to use the xvba wrapper: [http://www.phoronix.com/scan.php?page=news_item&px=MTg1NTE](http://www.phoronix.com/scan.php?page=news_item&px=MTg1NTE)

It's been a while since I've used the open-source drivers radeon driver to do vdpau on an AMD card, but xbmc devs seem to be happy with them enough to recommend open-source drivers over Catalyst for video playback.

---

### Post by xmjsilverx on 2014-12-05
Ok, so are you saying I should just switch to the open source driver for my AMD?  I went with the proprietary so I could eliminate screen tearing but I'd be willing to try the open source.

---

### Post by Yellow Pasque on 2014-12-05
If you would prefer the proprietary driver, then I would try the advice here first: [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Using_the_xvba-va_driver_.28VA-API.29](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Using_the_xvba-va_driver_.28VA-API.29)
If you can get vainfo to output supported profiles, then you can try it out by setting your video player to use VA-API output. I experimented with using the video decode acceleration on a RadeonHD 4550 a few years ago and it did offload a decent amount of processing to the GPU, even if it's not as good as using VDPAU on an nvidia card.

---

### Post by tokyobadger on 2014-12-05
from [what I'm reading](http://kodi.wiki/view/HOW-TO:Install_XBMC_on_Ubuntu/with_AMD_GPU#Step_7:_Optimizing_XBMC_CPU_use_and_configure_GPU_sensor) you could tweak your config and you should [be using hardware acceleration as opposed to software acceleration](http://mymediaexperience.com/first-htpc-tips/)

As noted by mastablasta your htop is showing a lot of usage by totem so it would be interesting to know what htop would look like if the totem processes were killed (unless it's set up as an external player for xmbc)

---

### Post by Yellow Pasque on 2014-12-06
> **tokyobadger said:**
> you should be using hardware acceleration as opposed to software acceleration

Yes, that is what I'm trying to guide the OP to do.

---

### Post by xmjsilverx on 2014-12-06
Well it looks like it is for sure a driver issue.  I switched back to the open source driver and now I remember why I didn't use it, for some reason it will not output the image correctly through the hdmi to my tv.  It smashes it all up to the top and distorts it.  I plugged in the vga cable and got it to at least show up undistorted.  I tried xbmc and watched the processors and for the most part they stayed right around 40%.  So now I have to switch back to the proprietary driver so I can see the image on HDMI and then try your suggestions unless you know a way to fix the output when using HDMI and open source driver.

---

### Post by Yellow Pasque on 2014-12-07
About the only thing I can suggest with the open-source driver is trying a later kernel and using a PPA for the latest drivers: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers). You may want to try that on another install if you don't feel confident about your ability to undo such things. Or perhaps try Ubuntu 14.10 or another really recent distro (like Fedora 21) on a USB stick to see if the HDMI issue occurs there.

---

### Post by xmjsilverx on 2014-12-08
OK, I will give some things a try.  I really appreciate all of your help.

---

