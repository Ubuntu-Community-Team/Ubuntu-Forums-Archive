---
title: "Startup sound hiss"
date: 2008-08-20
forum: General Help
---

### Post by Progenitor101 on 2008-08-20
After logging in and just before the startup music plays (not the log-in drumroll)...there's this loud hiss that makes you jump out of the chair if you forget the sound is up.
I have absolutely no other sound issues, everything is great.
Is it some kind of system sound test? Anyone else have this?

---

### Post by Progenitor101 on 2008-08-30
no ideas how to get rid of this?

---

### Post by retrovertigo on 2008-08-30
I've not experienced this before... have you tried to rule out it being a speaker issue by plugging different speakers or a pair of headphones into your sound card?

---

### Post by MK27 on 2008-10-01
Hi I'm another Windows to Linux convert (been using it for 2 days now) still use windows for gaming tho...

Back to the problem at hand, i had a similar issue with my new install of Ubuntu. and i was finally able to pinpoint what was cosing it and fix it.

The problem was that every time i boot the PC it would make a very high static noise (white noise) when the loading line underneath the Ubuntu logo almost reaches the end. it would also make that sound but for a longer period of time just before the login music started. Also while using the the system i would get a different kind of static noise (like if u put ur speakers with an amp up to full volume) at low speaker volumes but when the system volume was on full or near it. <<<although this was coused by a different device the solution is pretty much the same

So here what was cosing it in my opinion...
When Linux boots up it enabled every line input on the system twice ones after the booting line is at around 90% and ones just after u log-in but before the login sound. Now i have various devices connected to my PC but the one that always produces static is my TV-TUNER that i never bothered to configure so it constantly outputs the white notice or the static buzz. 
So now we know what cosing the static st startup but what is cosing the constant static noise later. Well i found 4 sources that each contributes to the static it's also sound inputs like line in, mic and such. each one of them produces a certain level of static but when the all un-muted and set to the highest volume it gets really annoying.

And finally [SIZE="6"][SOLUTION][/SIZE] in bold for lazy people who dont want to read the whole post lol

Double click on the speaker icon located on the top panel by default>now go into File>Change Device> and select the device that says Capture: in front of it and mute it (if you have more than one of those devices mute all of them or try to pinpoint which one is causing the problem by muting one at a time and rebooting) now thats the login noise problem solved.

Now go into "File" again and select the rest of the devices one at a time and mute the MIC or FRONT MIC channels, LINE IN, CD, and PC SPEAKER. if you use any of those devices just pull the slider down until the static is gone or less noticeable instead of muting them. do it for all the output devices.
also if u did all this but still hear the static make sure u go into the edit>preferences and check if all the input channels are set to be displayed (needs to be done for each device)

P.S.Thank for reading hope it helps.
P.S.2 if it is hard to make sense of what i wrote (sorry, tried my best :D) admins feel free to edit my post :D .

---

### Post by bigalanisfan on 2009-08-09
I've got this white noise from my tv tuner card (through line-in). I use the card with Tvtime, and the software leaves line-in enabled at maximum volume leading to that loud white noise during next login. I used Ubuntu (Feisty Fawn) (and Tvtime too) in the past with the same config, and there wasn't white noise. I think that the initialization of the tv tuner card happens too late (in the middle of the login sound). What can i do to solve the problem?

---

