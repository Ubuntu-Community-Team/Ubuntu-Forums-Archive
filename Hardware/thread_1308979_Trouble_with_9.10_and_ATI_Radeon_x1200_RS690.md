---
title: "Trouble with 9.10 and ATI Radeon x1200 RS690"
date: 2009-11-01
forum: Hardware
---

### Post by devehf on 2009-11-01
I've tried everything to get the open source driver to work in Karmic (9.10) for my mother board embedded ATI x1200 graphics processor (RS690 chipset). Seems like it was working pretty good in Jaunty (9.4) but now when X starts on bootup, there is just a black screen. I can run in restricted mode and start up X and things are OK some of the time. Most of the time though the screen flashes on for a second and then goes back to black.

I've tried tweaking xorg.conf, installing new drivers according to other people's suggestions but nothing seems to work. e.g. driver = "radeon" or "radeonhd"., etc. 

Any suggestions for getting this old chipset to work? I would like not to have to upgrade my hardware. This mobo is only a couple of years old.

Thanks in advance,
Dave

---

### Post by restart on 2009-11-01
Try to completely reinstall the system. It works well for me.
I have my /home folder on the its own partition, so it wasn't very hard for me.

P.S.: oh, yes, my chip is Radeon X1600.

---

### Post by devehf on 2009-11-01
I think I will give this a try. I am running Ubuntu Studio so I bitTorrented the 9.10 Ubuntu Studio DVD iso. It doesn't give me the option to run a "Live" session only install. I wonder if I should use the Ubuntu Studio installer to to the repartitioning or if I should use a regular Ubtunu Live-CD with the graphic partitioning tool.

---

### Post by originalsynthesis on 2009-11-03
im very curious about this, myself. I just had the same problems with 9.10 and an ati 780g chipset, though i haven't installed the open source driver yet.... 

I was using amd's fglrx driver and got nothing but a blank screen. actually, for me its a no signal error on my monitor. 

just curious how/if you got it working, devehf, because reinstalls have not done squat for me.

---

### Post by devehf on 2009-11-04
I finally got Studio reinstalled tonight. This involved lots of partition resizing and creating to back up my old home folder. I ended up using the Ubuntu Live CD. Very handy.

This new installation of Studio has the same black screen problem. At least I don't have to enter restricted mode though. It's like I just have to wait for the video chips to warm up.

Odd thing is, when I was repartitioning using the Live CD, I noticed the screen would black out when I would perform an operation that would start the CD spinning in the drive. Like there was something electrical going on.

Looks like I am going to have to get a recently manufactured video card because this 2 year-old one is no longer supported by AMD on this version of X and the open source driver is not 100% compatible. Any suggestions on make model?

originalsynthesis, i would suggest the open source driver. it might work for you.

---

### Post by devehf on 2009-11-05
I posted this bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/475131](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/475131)

I think I am headed back to Hardy Studio. I am pretty sure that the proprietary ATI driver will not support the x1200 on Jaunty.

---

### Post by devehf on 2009-11-07
On the verge of backporting to 8.4.1 Studio.... I had the thought that I should test my HDMI video connection rather than the DVI (my mobo and monitor have both). So far so good! The HDMI port connection is not producing the same intermittent video outage that was occurring with desktop and monitor were connected via DVI port. I can live with that.

I do get a loud "pop" on the main audio output when I open windows intermittently. I wonder if it is because HDMI circuitry also carries an audio signal and again, something electrical is going on. Like a poorly grounded motherboard.

---

### Post by originalsynthesis on 2009-11-08
Seems the opensource drivers ( the mesa glx drivers ) work decently. Cant seem to get anything near full 3d, but, i guess I cant complain. 

which open source drivers were you using? because these mesa drivers are the ones that karmic came down with. 

Been having a lot of other weird stuff on my ati board as well. On the windows xp half of the machine, I was getting nasty feedback loops from my inputs while doing any recording after the first track I laid down. Granted, I had no intention of setting up for surround or a serious hd rig, but I thought it may come in handy. 

 What ended up fixing it was reinstalling the main realtek and hdmi drivers off of ATI's website instead of the mobo disc that came with, as well as an xp audio patch I had never needed before, and some other things. 

Then, on the Karmic side, xruns galore the moment I got the rt kernel working and fired up Jack. And yeah, I had all the limits set to the usuals. even tried tweaking them all to various levels of no effect. It seemed no matter what I did, tweak the NICE percents, memlock, nothing helped with the xruns except adding massive frame/buffer and period settings. 

And besides that, those xruns would start stacking up just from turning on the jack server. Using Ardour was pathetic, two tracks possible for playback, and anymore would cut the connection to Jack. Had to restart Ardour each time that happened.

Prior to that, the vanilla kernel seemed to do just fine with JACK, some xruns here and there, nothing too bad. Not what I was hoping for, but it was doing a good job straight out of synaptic with no tweaks. 

Soon as the rt got activated, both seemed to go haywire with or without jack set for using realtime. Eventually i found a couple threads on the forums here and there mentioning that since Jaunty, the rt kernel was "broken", and that karmic was no better. (dont have the links at the moment, but I could dig em up if you'd like to see) So, I  gave up on the rt kernel and emptied limits.conf, and that seemed to get things back to normal. 

 The main impression I've gotten from all this is that either ati's chipsets (or maybe just my 780g?) are crap for doing audio work in general, or the maybe the hd functionality in particular is poorly implemented and causes crossed datastreams or just a lot of extra processing time somehow. 
 
I haven't had any of this happen with my other box, using an nvidia 630a chipset and 9.10 upgrade, though the rt is not so good either, but still useable.

Did you have anthing like this with your setup, devehf? or did you even get as far as rt?
I didn't want to make such a huge post, not trying to steal the thread, but because I had this *and* problems with Karmic's xorg similar to yours, I wanted to toss this out there. 

no, really, not trying to steal the thread, just curious if this rings any bells for someone working with similar stuff.

---

### Post by devehf on 2009-11-09
Yes, using the mesa drivers. 

I've been a slacker on the audio stuff. Haven't even fired up Jack yet. Finally getting my music collection in order under Amarok and copying to iPod some new stuff I got from my music director at the radio station where I volunteer. 

I need to get the audio recording working again soon so I can record some PSAs.

---

### Post by originalsynthesis on 2009-11-09
Good luck with Jack then, I'd recommend avoiding the realtime kernel unless you end up backporting to Hardy. I'm considering this myself.    

Hell, for PSAs you probably dont need much more than the generic k and a decent Jack setup. 

On that 'pop!' you get on windows, is that happening when you are first booting to desktop? xp? vista? I know that there are a couple patches for xp that fix some hd audio problems caused by using service pack 2, and reinstalling your hdmi and realtek hd drivers off of ati's website may be worth a shot. That helped me quite a bit on the MS side.

it may be unrelated, but that does remind me of the feedback loops i got from recording, like something not so good going on with the way the chipsets handle the various I/O stream types. Besides laggy audio handling, I've noticed small pops on linux when different sound programs take over, and these dont show up on my other machine.

---

### Post by Rumtum Tugger on 2009-11-10
I had the same problems with my MSI (ATI) Radeon HD2600 Pro AGP. I read some place that the 2.6.31 kernel causes the problem and that it'll be fixed in 2.6.32. Since I bought this card, I have been spending an awful lot of time getting it to work, sometimes with success and sometimes without. I have done this under Suse 11.0, 11.1 and 11.2 and Kubuntu 9.04 and 9.10, the latter being totally useless for me so I fell back to 9.04. So I decided to abandon Radeon. Btw, I think the proper driver for this (my) card is the fglrx driver.

Regards,
Tugger

---

### Post by ardinmcallister on 2009-12-15
I hate to be the bearer of bad news, but AFAIK, the Radeon X1200 was taken out of the fglrx driver by ati. This happened when ubuntu moved to the new Xorg which made ati update its driver and they decided that the x1200 was too old to support. I'm stuck on 8.10 until the open source driver better supports the X1200.

---

### Post by devehf on 2009-12-15
Yeah, we know the Radeon X1200 is not supported by the fglrx driver. That's why this thread was started because we are trying to use the open source driver now.

It's been working OK for me since I have switched to an HDMI interface. Every once and a while i have to wait a bit for the graphics to kick in.

---

