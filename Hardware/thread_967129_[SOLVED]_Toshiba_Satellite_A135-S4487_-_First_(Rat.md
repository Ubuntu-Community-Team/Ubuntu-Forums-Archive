---
title: "[SOLVED] Toshiba Satellite A135-S4487 - First (Rather Strange) Audio Problem"
date: 2008-11-01
forum: Hardware
---

### Post by -kg- on 2008-11-01
I say in the title that this is a "rather strange" problem because I have never encountered such in the 40+ years that I've been involved in electronics/ham radio/computers.

Normally (unless the plug is the type that doesn't cut audio to the speakers, which this apparently is) when you plug headphones into a system, the audio to the speakers is cut off by action of the headphone jack.  Such is the case for this laptop under Vista.  I plug the headphones in and audio is cut to the speakers and re-routed to the headphones...the normal action for a headphone jack.

Under Ubuntu, however, I plug the headphones in and not only does it not cut off the laptop speakers, there is no audio in the headphones, either.

I had Ubuntu booted and was viewing one of my video files last night, and wanted to hear the sound at a decent volume, so I plugged in the headphones.  I could hardly hear it, so I kept turning everything up until all related volume controls were at max.

Even with this I could hardly hear the audio, and I was thinking that the headphones were not very well served by the drivers, when one of my family members got my attention and asked me to turn the volume down so they could hear T.V.  I took the headphones off and, sure enough, there was audio coming out the speakers.  I put the headphones back on and listened closely, but there was not one peep coming out them.:confused:

Thinking that perhaps I had a hardware failure, I rebooted back into Vista and launched the same video.  I plugged the headphones in and the speakers were cut off and the audio came through the headphones with no problem.  I booted back and forth again, and each time the problem (or lack thereof) was the same.

Anyone here have a similar experience?  Any fixes or things I might look at?  Like I said, normally audio to the speakers is physically cut off at the speaker jack by plugging headphones in, but apparently this isn't the case, at least with *this* laptop.  While this is a minor annoyance, I *do* like to sit on the couch and listen to something on the computer while the rest are watching T.V., and I won't be able to do it until I find a fix for this problem.

Thanks

P.S. -  I just read a post about "USB Headphones" support under Ubuntu.  Could it be possible that my laptop is set up for USB headphone support, with the normal "front panel" headphones jack set up to access this audio feed?

---

### Post by -kg- on 2008-11-06
As a "bump" and an addendum:

I experimented with this a little.  The headphones definitely don't work whatsoever, although they do in Vista.  I did notice one thing, though:

Next to the headphone/microphone jacks is a volume control.  Under Vista this volume control controls the Master Volume for the entire system.  If you pull down the volume control from the taskbar and operate the volume control on the front panel, you can see the slider on the screen move up and down.

Well, under Ubuntu this volume control still works, but it is not linear.  It increases and decreases in steps...rather *large* steps.  For instance, it might be at 58% and you move the volume control a little and it will step up to 77%.

I realize that digital volume (or any "analog to digital" type control) steps rather than adjusts linearly.  In the old wire-wound controls, there was a degree of stepping inherent from the slider going from one winding to the next.  But under Vista you at least have the illusion of linearity...under Ubuntu the steps are very obvious.

---

### Post by gika on 2008-11-06
Hi,

I have the same problem on my Dell 1520 and Toshiba A200. The sound volume is very low. I fixed it by going in Sound Settings and selecting the appropiate sound hardware. It's either OSS, ALSA, etc. Try playing with those settings and pressing the TEST button and you'll hear a clearer sound. Hope it works. It did for me. Good luck! :)

---

### Post by metol on 2008-11-09
I have Toshiba A135-S4666 laptop and had the same headphone issue in Hardy and Intrepid.  The following modification fixed the headphones in both instances:

First make a backup of your alsa-base file in case something goes wrong you can always revert back to the original.

```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.backup
```

Next edit your alsa-base file:

```
gksu gedit /etc/modprobe.d/alsa-base
```

then scroll to the bottom and add the following line..

```
options snd-hda-intel model=lenovo
```

Save the file and then **reboot**.  My headphones worked fine after adding that line.

Now, if this does not work on the S4487, the model=lenovo line may need to be slightly different.  If this does not work for you, let me know and I will try and dig up the site that has a list of alternatives.

Hope this helps,
Metol

---

### Post by -kg- on 2008-11-29
Well, I should really check my posts a little more often.

Metol, I tried your method and it worked almost perfectly!  The headphones now cut the system speakers off and I get good volume through the headphones.

The manual volume control still stair-steps as before, but I'm not too worried about that...I can use the mouse and slide the volume control if I need that fine of control over the volume.

Many thanks to you, and where is the site you mentioned with the alternatives?  I would like to bookmark it for future reference if you can find and post it.

---

### Post by metol on 2008-12-03
Glad to hear that it is working for you.  I disabled the little volume knob on the front of the laptop long ago.  I kept hitting it accidentally and it was driving me crazy.  I just hover the mouse over the volume control icon and use the mouse scroll wheel to adjust the volume - works great.

I searched for that website I found many months ago that had a large list of "options snd-hda-intel model=XXXXXX", but for the life of me I can not find it.  I'll keep looking and let you know if I find it again.  The following Ubuntu forum thread has a few:

[http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")

> **-kg- said:**
> Well, I should really check my posts a little more often.

Metol, I tried your method and it worked almost perfectly!  The headphones now cut the system speakers off and I get good volume through the headphones.

The manual volume control still stair-steps as before, but I'm not too worried about that...I can use the mouse and slide the volume control if I need that fine of control over the volume.

Many thanks to you, and where is the site you mentioned with the alternatives?  I would like to bookmark it for future reference if you can find and post it.

---

### Post by -kg- on 2008-12-06
> I searched for that website I found many months ago that had a large list of "options snd-hda-intel model=XXXXXX",...

I was checking around and found a site.  Could [[COLOR="RoyalBlue"]_this possibly be it?_[/COLOR]]("http://www.alsa-project.org/main/index.php/Main_Page")

There were a lot of good links and information on the link you posted which took me from site to site.  Thanks for the post!

---

### Post by metol on 2008-12-07
> **-kg- said:**
> I was checking around and found a site.  Could [[COLOR="RoyalBlue"]_this possibly be it?_[/COLOR]]("http://www.alsa-project.org/main/index.php/Main_Page")

There were a lot of good links and information on the link you posted which took me from site to site.  Thanks for the post!

Here we go... [http://ubuntuforums.org/showpost.php?p=5131958&postcount=2]("http://ubuntuforums.org/showpost.php?p=5131958&postcount=2").  This is not the exact link, but the content that I was looking for is nearly identical.  At the bottom of this post, you can scroll through a very large list of options for the alsa-base file.

---

### Post by rsun on 2008-12-21
I realized this thread is [SOLVED]. I just want to find out if the manual volume control is working?

Since upgrading to 8.04 from 7.10. My sound and touchpad of my Toshiba Satellite A135-S4656 has never worked the same.

When I bought my notebook, I immediately installed 7.10 with Vista still on. I had very minor issue with the sound, it was very faint, but everything works i.e. plugged in the headphone main speakers transferred to the headphone and I can use the manual control to adjust the volume. Since I upgraded to 8.04 I experienced the same problems as -kg-. Until I saw this thread, sound to my headphone never work. Now it works, I can hear the sound from my headphone and the main speaker is muted. It's working like it supposed to except, the manual volume control still doesn't work.
I've followed metol's links on his last post and tried different modelnames. The closest to making the manual control worked was using the modelname dallas. But transfer from main speakers to headphone did not work.

I have left it as suggested model=lenovo. but these are the problems.
1. Manual volume still does not work
2. Fn Esc to toggle Speakers ON/OFF does not work. It was working before.

The manual volume control is useful to control the volume when the computer is booting up. It's very embarassing when booting the computer in a quiet library. I had to apologize for disturbing the peace.
I was able to use Fn Esc to mute the speaker before, now the only way to mute the speakers is:
1. To remember to turn is down from the soft control before I shut down or
2. Plug in my headphone before I boot up.

Any suggestions?

---

### Post by metol on 2008-12-22
Hello rsun,

You likely just need to reconfigure your keyboard shotcuts.  I'm using 8.10 but I believe the process is identical in rev 8.04.

Go to "System" -> "Preferences" -> "Keyboard Shortcuts"

Under "Sound", you will see that you can assign shortcuts to volume up, volume down, and mute.  So just click the volume up, then move your wheel to the right and it should capture that event.  Then do likewise for the other key assignments.

Hope this helps,
Metol

---

### Post by -kg- on 2009-04-26
This is an addendum for those who might run across this question for solving their own problems.

I have recently started evaluating Jaunty, and while a great many of the problems that I was having with Hardy have been resolved, this problem persisted.  The above coding will work under Jaunty, as well, with a couple of little changes:

```
sudo cp /etc/modprobe.d/alsa-base[COLOR="Red"].conf[/COLOR] /etc/modprobe.d/alsa-base.backup
```

and:

```
gksu gedit /etc/modprobe.d/alsa-base[COLOR="Red"].conf[/COLOR]
```
(Changes in red, of course)

Seems that at some time after Hardy they changed the name of the alsa-base configuration file.  I was kind of concerned because I figured I was going to have to do a bunch of research to come up with another fix for it, but on a lark I navigated down to the /etc/modprobe.d directory and there it was with a .conf tacked on the back of it.

The fix still works the same.

---

