---
title: "Logitech ClearChat PC Wireless"
date: 2009-04-27
forum: Hardware
---

### Post by Brucevdk on 2009-04-27
I bought this headset Saturday on an impulse and it doesn't work out of the box with ALSA on Ubuntu 8.10 (Intrepid). However, it does work if I configure it to use OSS as such through the GUI (gnome-sound-properties):

[img]http://ubuntuforums.org/attachment.php?attachmentid=111359&stc=1&d=1240825405[/img]

Note that the "Default Mixer Tracks" point to which volume control is controlled with the up/down volume keys on your keyboard and the headset itself.

If I do choose the ALSA variants I will get the usual error when a sound device is not accessible (at least this is what I remember from previous sound issues):

> 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. 


If anybody else is having problems getting sound at all take a look at the controls in gnome-volume-control to make sure you haven't muted anything. The relevant device name is *Logitech Wireless Headset (Alsa mixer)*. You can test the microphone using gnome-sound-recorder, hit record and it will show a meter indicating the voice levels.

I haven't actually dived into the ALSA issue yet but will keep everybody posted with my results when I do. However there are two other unrelated issues with the set:

[list]
[*]The set I bought when connected always emits a consistent white noise 
[*]I can clearly hear myself when talking over the microphone (there doesn't seem to be the option to disable this as there is with normal microphones, see [this thread](http://forums.logitech.com/logitech/board/message?board.id=headsets_general&thread.id=5712&nobounce)). 
[/list]
Especially the white noise problem is a deal breaker for me, it makes it impossible to keep the headset on when listening to nothing. The feedback problem is also quite annoying but seems to be less noticeable with actual usage.

I'm going to ring up Logitech support to verify whether or not these two things should be occurring at all. In any case I will most likely return to the store due to the white noise issue.

Thanks.

[SIZE="4"]Relevant discussions[/SIZE]
[LIST]
[*][Logitech USB Headphones + Mic Do Not Work](http://ubuntuforums.org/showthread.php?p=7157335)
[*][Voice can not be shifted from laptop to headset](http://ubuntuforums.org/showthread.php?p=7155862)
[*][Jaunty & Logitech USB Headset](http://ubuntuforums.org/showthread.php?t=1135182)
[/LIST]

---

### Post by Brucevdk on 2009-04-27
OK, I rang Logitech support this morning and the person I talked to was very helpful. I clearly explained the issue with the white noise and how it occurred even before the operating system had started and asked whether or not this indicated a defect. 

He contacted a sound engineer and informed me that this behavior was not normal and advised me to return this particular set to the dealer. I just returned from the dealer and they were unable to exchange it and simply gave me back my money without any problems.

I'm keeping this thread open for discussion and I might still buy this headset again but at a specialized headset store so I can properly try it out before buying. Either that or I'll be looking at buying another Sennheiser since the one I have ([eH 250](http://www.sennheiserusa.com/media/hiresImages/EH250_hires.jpg)) hasn't disappointed me so far.

---

### Post by soule on 2009-05-11
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Seems to apply to your symptoms. Also do you have plans to update to Jaunty some day? It's only OK to be with Jaunty or Hardy.

Anyhow, good luck,


-soule

---

### Post by Brucevdk on 2009-05-11
> **soule said:**
> Seems to apply to your symptoms. Also do you have plans to update to Jaunty some day?

Some day yes :-) The headset's gone now, but if it ever makes a return and I've upgraded to Jaunty I will take a look at it at the link regarding PulseAudio you just gave. Thanks!

---

