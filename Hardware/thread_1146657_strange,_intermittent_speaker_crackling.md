---
title: "strange, intermittent speaker crackling"
date: 2009-05-02
forum: Hardware
---

### Post by Crowder on 2009-05-02
not sure if this is a hardware problem (there is something physically wrong with the hardware) or a problem with engines or drivers or what, but my speakers have been "crackling" lately. 

It's not constant, and they usually sound perfect, but they occasionally crackle on pidgin sounds and other short alert sounds. I'm baffled. There doesn't seem to be any correlation to any specific sounds, and in a pidgin conversation it might happen a few times, but not most of the time.

I run a lenovo t61 with an Intel 82801H HD Audio controller. After upgrading to Jaunty I've left the sound set to "autodetect," but I've since changed the settings to ALSA. 

I also get some popping when the speakers engage, if only about half of the time. Again, nothing is consistent here so I don't really know what to make of it.

EDIT: saw a notification from amarok that read something like "device HDA Intel AD198x analog did not work. Falling back on pulseaudio."
Any help would be greatly appreciated.

---

### Post by svega85 on 2009-05-23
I have this same problem I'll post back if I find the solution.

---

### Post by Mikhail.Glagolev on 2009-06-08
Hello, I'm also experiencing this problem with 82801H, used to crackle in Pidgin and while playing flash video.
Installing kernel 2.6.30-rc7 from kernel-ppa fixed the flash and reduced frequency crackling occurs in pidgin, but hasn't completely solved the problem.

---

### Post by Crowder on 2009-06-09
> **Mikhail.Glagolev said:**
> Hello, I'm also experiencing this problem with 82801H, used to crackle in Pidgin and while playing flash video.
Installing kernel 2.6.30-rc7 from kernel-ppa fixed the flash and reduced frequency crackling occurs in pidgin, but hasn't completely solved the problem.

that's exactly what i'm talking about, and it still happens sometimes.

---

### Post by X-Kent on 2009-06-09
Same here on portage m750 laptop.

---

### Post by airchie on 2009-06-11
Same here on a Kobalt Nexus 15" laptop (clevo 860 IIRC).

EDIT
I solved this (I think, still testing) by uninstalling pulseaudio. through synaptic. :)

---

### Post by Crowder on 2009-06-11
> **airchie said:**
> Same here on a Kobalt Nexus 15" laptop (clevo 860 IIRC).

EDIT
I solved this (I think, still testing) by uninstalling pulseaudio. through synaptic. :)

yeah, but pulse seems to be the only way i can easily have more than one app using sharing the sound card. Still, I'll consider doing it because I really don't like pulse.

---

### Post by X-Kent on 2009-06-17
Any workaround other than disabling pulse ?

---

### Post by svega85 on 2009-06-17
It seems like pulse keeps messing up with every new version of ubuntu if it's not one issue it's another

---

### Post by Crowder on 2009-06-18
> **X-Kent said:**
> Any workaround other than disabling pulse ?

Not that I know of, and I'm certainly not going to come up with it on my own. I'm not even sure that there will ever be one, because we haven't even determined what this problem is or what's causing it.

> **svega85 said:**
> It seems like pulse keeps messing up with every new version of ubuntu if it's not one issue it's another

lol seriously. In Hardy I had to disable it from the beginning to get any sound at all, and in Intrepid it couldn't do any two things at once. ALSA seems to work better.

---

### Post by markmckee6011 on 2009-06-19
I had a similar problem with a M-audio Audiophile 2496, I would get a "pop" from the speakers every so often, even when an application wasn't using audio.

The problem was caused by having the volume maxed out in the mixer, the speakers weren't maxed out.
The problem disappeared when I turned down the volume a small amount in the mixer.

Not sure if this is the same with the Intel 82801H HD Audio but certainly worth a try.

I hope you guys get the problem resolved as I know how irritating it can be.

---

### Post by Crowder on 2009-06-19
> **markmckee6011 said:**
> I had a similar problem with a M-audio Audiophile 2496, I would get a "pop" from the speakers every so often, even when an application wasn't using audio.

The problem was caused by having the volume maxed out in the mixer, the speakers weren't maxed out.
The problem disappeared when I turned down the volume a small amount in the mixer.

Not sure if this is the same with the Intel 82801H HD Audio but certainly worth a try.

I hope you guys get the problem resolved as I know how irritating it can be.
Will definitely give that a try, though I'm not sure it's the same problem. I wouldn't describe the sound I'm hearing as a "pop" so much as a crackle. I've gotten the pop before, but this is more like the sound of an electric chair. It's very loud. 

Also, it seems (for me at least, and maybe a few others here) to only be happening with Pidgin sounds. I may have heard it on an OS alert, but not that I recall. Basically, when an IM is received (or any Pidgin alert sounds) it is almost completely drowned out by a crackling sound. I haven't experienced it when using amaroK or anything else for that matter. I have heard it when an IM was recieved while music was playing.

It seems like this problem is somehow caused by Pulse. I may end up purging Pulse sometime soon.

---

### Post by Crowder on 2009-06-19
Another piece of information - this is definitely not a problem with the speakers. Heard it on externals the other day, so it must be Pulse or some other internal problem.

---

### Post by holotone on 2009-07-30
Same deal over here on a brand-spanking new Dell Inspiron 1545 running Jaunty - The crackling is terrible, particularly at high volume and, as others have mentioned, during Pidgin join / part audio notifications. Oddly enough, it also seems to happen from time to time when I mute the audio, too.

Opening Sound Preferences and switching everything to ALSA helped for the most part, but then I'm back to dealing with certain applications "stealing" the soundcard and not giving it back up when other apps want to use it.

---

### Post by holotone on 2009-07-30
I think [this]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/347544") is our bug.

---

