---
title: "sony vpcs111fm/s"
date: 2010-01-20
forum: Hardware
---

### Post by MichaelRX8 on 2010-01-20
I saw this laptop at Bestbuy, it has an nVidia card and some pretty nice specs for the price. Has anyone tried it yet? Wondering if it will work well with Ubuntu? I'm real close to buying a new laptop.

                        Thanks,
                            Michael

---

### Post by eblock on 2010-01-20
I am sorry for not answering your question, but I went to the store yesterday and saw that PC with Intel HD Graphics. If you saw it with nVidia, I will be (very) pleasantly surprised. I think that it will run ubuntu very well but that is only a guess.

Thanks,
Elliot

---

### Post by MichaelRX8 on 2010-01-20
Nope, its nVidia. Check out the Sony site under the CW series.

---

### Post by MrBlippy on 2010-01-24
I have the VPC-S111FM/S from Best Buy and it has the newest Intel HD Graphics (on the same physical chip as the CPU). It does **not **have an NVidia GPU. The Vaio CW series does have NVidia GPUs on most models, but the Vaio CW is not the Vaio S1. They are indeed separate models.

The Vaio S111FM/S is a nice notebook and I have been very impressed with the performance of the CPU as well as the integrated GPU. I have not yet tried loading Ubuntu on mine, but will do so very soon. It should run very nicely. :D

---

### Post by MichaelRX8 on 2010-01-24
Dammit...mixed up my notes on those two wile I was at best buy, I do apologize. My face is quite red. So how about the cw series? Anyone tried that one? Also, MrBlippy; you should do it soon and let me know how the 3d support is. Would the push to TV work? I really like the design of the vps111fm/s but am concerned about the integrated chip.

thanks for the responces.

---

### Post by MrBlippy on 2010-01-24
No problem! Just wanted to clarify the GPU specs on the S1 series. To be completely honest with you, I have yet to get the Push2TV working even in Windows. I have the latest (and recommended) drivers and while I can see the Netgear P2TV box, I receive a connection error every time I try to initiate the connection. I can live without Push2TV, as it really was only an added perk when I was considering this Vaio S111FM/S. Given that the Windows support for Push2TV sucks right now, I would say it is a safe bet it is not Ubuntu friendly quite yet.

I also considered the new Vaio CW notebooks Best Buy just brought out, but I ultimately wanted something lighter to carry around than the 5+ lbs CW. Given the specs on the CW, though, I don't think you would go wrong with it. The 1600x900 pixel screen on the CW was hard to pass up--I do wish the S111FM/S had that resolution.

I think I still have my Ubuntu USB key loaded up, so let me fire it up and check it out now. I will try to report back this evening on the 3D support.

---

### Post by MichaelRX8 on 2010-01-24
Thank you sir.

---

### Post by Limitlesschannels on 2010-02-11
Just picked up this glorious machine and I really love it.  Good size, feels solid, illuminated keys = awesome, and it's just comfy.  The only thing I would change is the GPU, but to be honesty I've played around with it and haven't really found anything it can't handle.  As far as IntelGMAs go, this one is pretty great.

Still haven't installed Ubuntu yet, but I think I will in the next few days.  I wanted to wait a little while so it would be better supported, but I might as well take the plunge.  I'll post back when I do and mention what works and what doesn't.

EDIT:  Yeah, the Push2TV support is sporadic, at best.  A little disappointing for an out-of-the-box experience.  It really should work perfect since they come together when you buy them.  When it does work, it holds the connection well and works perfect, however.

---

### Post by jfrorie on 2010-02-20
I picked up one as well.  Put Lucid A2 on it.  I created a wiki as I work through the issues,

[https://wiki.ubuntu.com/LaptopTestingTeam/SonyVaioVPC-S111FM](https://wiki.ubuntu.com/LaptopTestingTeam/SonyVaioVPC-S111FM)

Be interested to see what others are getting to work.

---

### Post by Limitlesschannels on 2010-02-23
> **jfrorie said:**
> I picked up one as well.  Put Lucid A2 on it.  I created a wiki as I work through the issues,

[https://wiki.ubuntu.com/LaptopTestingTeam/SonyVaioVPC-S111FM](https://wiki.ubuntu.com/LaptopTestingTeam/SonyVaioVPC-S111FM)

Be interested to see what others are getting to work.

nice work, man!  I'll definitely help contribute to the wiki.

EDIT: how did you run the tests under Karmic?  It doesn't seem to have video driver support and I couldn't even get it running off the live cd

---

### Post by jfrorie on 2010-02-23
> **Limitlesschannels said:**
> nice work, man!  I'll definitely help contribute to the wiki.

EDIT: how did you run the tests under Karmic?  It doesn't seem to have video driver support and I couldn't even get it running off the live cd

Thanks for reminding me.  I had to change the video options in the startup menu.(F4?)  I can't remember which, but I think it was a failsafe option.  Once installed, Karmic works but for the wireless.  Didn't test extensively for that reason.

---

### Post by Limitlesschannels on 2010-03-05
It looks like Lucid Lynx 10.04 Alpha3 has put in some significant improvements and bug fixes.
  In the case of the S111fm, brightness hotkeys now work as well as panel control.  A couple of the weird crashes I've experienced (i.e. crash on switch to battery power) have stopped, as well.

Still, no sound.

---

### Post by jfrorie on 2010-03-05
> **Limitlesschannels said:**
> It looks like Lucid Lynx 10.04 Alpha3 has put in some significant improvements and bug fixes.
  In the case of the S111fm, brightness hotkeys now work as well as panel control.  A couple of the weird crashes I've experienced (i.e. crash on switch to battery power) have stopped, as well.

Still, no sound.

Sound is in progress.  Go here for a temp fix.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/525149/comments/9](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/525149/comments/9)

There is a google code group that is working a couple of the other issues.
[http://code.google.com/p/vaio-f11-linux/issues/detail?id=2](http://code.google.com/p/vaio-f11-linux/issues/detail?id=2)

My biggest complaints is flakiness of the touchpad.  This appears to be in the generic synaptics driver, which I can't find code for. 

If someone can point me to the REAL synaptics driver, I'd be willing to look at it.  I've found like 6 different versions, and none of them are current.

---

### Post by jfrorie on 2010-03-10
As of latest updates, suspend works.  Audio working with patch.

If things keep going like this, it is going to be a sweet little ubuntu laptop. :)

---

### Post by Limitlesschannels on 2010-03-25
Just loaded up the Beta1 and attempted to apply the audio patch.  This time around I received this error:

> Error: Dependency is not satisfiable: linux-backports-modules-alsa-2.6.32-17-generic
any idea what's wrong?

---

### Post by jfrorie on 2010-03-25
> **Limitlesschannels said:**
> Just loaded up the Beta1 and attempted to apply the audio patch.  This time around I received this error:


any idea what's wrong?


Give it a little time.  It looks a dependency hasn't made into the repos, yet.

---

### Post by cicatrix1 on 2010-05-04
I'm in the market for a new notebook.  I really have a Mac craving right now but I saw this at Best Buy today and it made me stop to consider picking this up instead of the new 13" MacBook pro.  They are similarly priced (but the Sony is a little cheaper now).

The sony is pretty similar, has a Better CPU, but a kind of weak graphics card.  HDMI output is a really strong factor, and Push2TV an interesting perk.  I think I may be able to get over the IGMA though because I'm more looking for a smallish portable laptop for general stuff (media, code, couch surfing, travel, etc) with games being fairly low priority (That's what my desktop is for!).

Do you guys have any updates on how well it's running Ubuntu these days?  Perhaps the official release of Lucid fixed some of the issues you were having?  Hmmm.

---

### Post by jfrorie on 2010-05-04
> **cicatrix1 said:**
> I'm in the market for a new notebook.  I really have a Mac craving right now but I saw this at Best Buy today and it made me stop to consider picking this up instead of the new 13" MacBook pro.  They are similarly priced (but the Sony is a little cheaper now).

The sony is pretty similar, has a Better CPU, but a kind of weak graphics card.  HDMI output is a really strong factor, and Push2TV an interesting perk.  I think I may be able to get over the IGMA though because I'm more looking for a smallish portable laptop for general stuff (media, code, couch surfing, travel, etc) with games being fairly low priority (That's what my desktop is for!).

Do you guys have any updates on how well it's running Ubuntu these days?  Perhaps the official release of Lucid fixed some of the issues you were having?  Hmmm.

Two main problems for me.  Microphone doesn't work, although there is a patch floating around that others have used.  Second is the touchpad.  Synaptic driver is buggy WRT certain events involving two fingers.

Beyond that, it's pretty solid. Suspend even works :)

---

### Post by Limitlesschannels on 2010-05-05
even with the final Lucid release, however, sound doesn't work out of the box.  It works fine with the above mentioned patch, though.

Otherwise, it's fairly solid.  The push2tv works great under windows, just make sure to update everything from sony's driver support page (just download all of the updates)
[http://esupport.sony.com/US/perl/swu-list.pl?mdl=VPCS111FMS](http://esupport.sony.com/US/perl/swu-list.pl?mdl=VPCS111FMS)

I'm still not quite content with it under ubuntu, but it'll take a little more tweaking before I get everything how I want it.  

Also, power management is quite a bit better under windows, there are a few settings sony implemented to give the nice 6 hour battery, including shutting off power to the DVD/CD drive when not in use, etc.

---

### Post by rifak on 2010-06-15
hey everyone,
i just bought this laptop and i love it. however, is anyone experience a lock-up on shutdown/reboot? im getting an error saying, "BUG: soft lock up CPU0 CPU1...." the normal stability of everyday use is great, but when i go to shutdown or reboot (and this only happens sometimes) i get this lock-up...finally having to do a hard reset. anyone else having this?

---

### Post by jfrorie on 2010-06-15
> **ego-sum-deus said:**
> hey everyone,
i just bought this laptop and i love it. however, is anyone experience a lock-up on shutdown/reboot? im getting an error saying, "BUG: soft lock up CPU0 CPU1...." the normal stability of everyday use is great, but when i go to shutdown or reboot (and this only happens sometimes) i get this lock-up...finally having to do a hard reset. anyone else having this?

Seen it occasionally. However, suspend has been so stable that I rarely power down, thus I haven't done it a lot.

---

### Post by rifak on 2010-06-16
i decided to install 64bit 10.04 last night and this seems to have fixed the problem with the CPU lock-up on shutdown. it also has smoothed out some other graphical issues i was having during start-up.

---

### Post by jack24 on 2010-08-18
I've been running Lucid on a VPCS111FM since the last Alpha.  It worked pretty well from the beginning and steadily got better until about two weeks ago.  An update (I think) caused two problems:
[LIST]
[*]can't print on existing printers and can't find new printers
[*]instead of suspending, the computer locks up
[/LIST]
Has anyone else had these issues?

When I plug in a USB printer it shows up in lsusb, but cups can't find it.

Suspend used to work both on delay and shutting the lid.  Now it never works on shutting the lid and only sometimes works on delay.

I can post more information if anyone can help, but I mostly want to find out if these are known issues before I put the time into trying to fix them.

---

