---
title: "HP Mini 210HD no external microphone"
date: 2010-04-03
forum: Hardware
---

### Post by b00n on 2010-04-03
Does anybody have an external microphone working with an HP Mini 210HD via the headset jack?

I have an HP Mini 210 with Ubuntu 9.10 installed (not dual-boot).  The mini uses a single socket for both audio in and audio out.  When I plug in a headset, audio out goes to the headset, but audio in is still from the system microphone.  I would like it to come from the headset microphone.

I looked at the "Sound Preferences" GUI and see no option to choose between on-board and headset microphone.

I contacted HP customer "support" and asked if switching is done by software or hardware, and in 20 or so e-mails I have yet to get an answer yes/no/don't know.  (Based on my experiences with customer support so far, I can highly recommend buying a Lenovo or any other brand of computer.)

I installed of the backport drivers (which made WiFi work much better) but the audio problem persists.

As a workaround I can use a USB audio dongle, but this is cumbersome.  If I can get the ordinary audio working it would be more convenient.

---

### Post by b00n on 2010-04-03
After asking over a dozen(!) times HP support finally says when a headset is plugged in the headset jack, the BIOS automatically switches off the built-in microphone.  Since the microphone stays plugged in, this indicates a hardware or BIOS fault, not an OS fault.

BTW, I am using Ubuntu 9.10 x86-64, updated via Synaptic within the last 24 hours, with backports installed, tho' that does not seem to make a difference in the microphone either way.

Since HP support seems to be a little clueless, I would appreciate hearing from HP 210 users if you have or have not gotten the microphone working when plugged in the headset jack.

---

### Post by derekeverett on 2010-04-03
I am an HP desktop user. Despite loads of research and posting multiple threads in these forums I have yet to get my external microphone working with Ubuntu. I have everything set up right, it just won't work. So I feel your pain here.

On this same machine, the microphone works just fine in Windows, so I am convinced it is an Ubuntu, if not a Linux issue.

Wish I had an answer for both of us, but I have been struggling with this for months. Frustrating.

---

### Post by derekeverett on 2010-04-04
Me again... with more information.

On another members advice, I tried a Debian Live CD this evening.

Guess what... my external microphone worked no problem!

I had to go into their sound tool and turn up the volume for "external microphone" but that was it. Sounded great.

Anybody used to Ubuntu won't struggle much with Debian from what I saw. So I'll be switching to Debian in the coming days. Thought I would let you know. 

Hope this helps.

---

### Post by b00n on 2010-04-04
Hey, thanks for the information, that is useful!

I hope to stick with Ubuntu rather than switch to Debian as I am using Ubuntu on several machines and it is otherwise working well for me.

After many more exchanges w/ HP customer "support" somebody says the BIOS is supposed to turn off the internal microphone when an external headset is plugged in, and/but also says MS Windows has a way to change the setting if it is not detected by the BIOS.  I do not see a selection in Ubuntu's "Sound Preferences" to select between microphones.  I poked around in the BIOS settings and see nothing related to sound.

So it sounds like the HP Mini BIOS lacks the ability to detect the headset getting plugged in, and Ubuntu's Sound Preference lacks the ability to connect to an override for whatever sound chip "steering" there is.

---

