---
title: "How to disable secondary HDMI display output but maintain sound?"
date: 2016-01-31
forum: Hardware
---

### Post by mikee2 on 2016-01-31
[COLOR=#111111][FONT=Ubuntu]I know that sound & video are naturally bundled together with HDMI, but I need to figure out a way to disable my secondary monitor without disabling the sound that is being used by the HDMI. 

Essentially, Ubuntu is acting like there is a secondary monitor when I use the HDMI out of the computer to my digital audio receiver. The result is making my desktop environment tricky to use, as Unity thinks there is secondary monitor and thus is creating multiple desktops despite that I am only using one monitor (my TV)
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If I disable the secondary monitor in system prefs, the audio is no longer passed out the HDMI port.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Is there way to get Ubuntu to only utilize the HMDI to use audio, and not recognize the receiver as a display monitor?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]thanks[/FONT][/COLOR]

---

### Post by mikee2 on 2016-01-31
[COLOR=#111111][FONT=Ubuntu]Is there a way to disable Unity from creating a secondary desktop if I have two monitors plugged in?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My secondary monitor is actually a receiver for sound, so there is no need to have a desktop assigned to it.

Using Ubuntu 14.04 64 bit[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2016-01-31
One really simple way is having mirrored desktops instead of extended desktop -and- to make sure the location of the launcher option is set explicitly to the 'real' monitor. This settings make it behave exactly like it were using/detecting a single monitor.

---

### Post by grahammechanical on 2016-01-31
I think that this is happening because you are using the HDMI out of the graphic adapter. The system is doing what it is programmed to do. Can you not use another audio output, perhaps from the motherboard instead.

Is this HDMI out from the graphic adapter going to the monitor? Or direct to the digital audio receiver? If the HDMI is going to the monitor, does the monitor itself have a digital audio output that can be used.

I am a bit confused by you saying that you want to disable the secondary monitor. Do you have 2 monitors? Or is this the imaginary monitor that Unity thinks you have?

Regards.

---

### Post by gordintoronto on 2016-02-01
"My secondary monitor is actually a receiver for sound..." I suspect most people can't figure out what this means, which is why you have not received an answer to your question.

---

### Post by mikee2 on 2016-02-01
> **gordintoronto said:**
> "My secondary monitor is actually a receiver for sound..." I suspect most people can't figure out what this means, which is why you have not received an answer to your question.

Understanable. Let me clarify this for people:

 Most audio receivers are now built with HDMI ports which process both sound & video signal. Video signals are passed out from the receiver to the television/monitor/projector. Since the inception of this technology, computers or HTPC units that are linked to these receivers see them & treat them as though they are visual displays, as they process video signals and are even capable of changing monitor resolution. 

So to get back to my question now:

How to get UBUNTU to not see this receiver as a monitor? Or I might ask how to get Ubuntu to not assign a workspace to this receiver?
It is creating an extra desktop that I cant actually use.

---

### Post by Vladlenin5000 on 2016-02-01
I already explained a workaround in your other thread. Please do not open multiple threads for the same question/issue.
(reported)

---

### Post by Bucky Ball on 2016-02-01
And 

*Threads merged.*

 Please do not post duplicates about the same issue, even if they are reworded or expanded upon. Just edit your first thread and if you don't get action for twelve hours or so, just post 'bump' in the thread.

---

### Post by mikee2 on 2016-02-01
> **Vladlenin5000 said:**
> One really simple way is having mirrored desktops instead of extended desktop -and- to make sure the location of the launcher option is set explicitly to the 'real' monitor. This settings make it behave exactly like it were using/detecting a single monitor.

I like this simple solution except that the secondary monitor is what becomes mirrored, forcing my TV into a resolution I can not tolerate. 

Is there way to make it so the Primary is mirrored and not the secondary ?

im not sure this is possible with the current setup, as the receiver does not support the resolution of the TV.

---

### Post by mikee2 on 2016-02-01
> **Bucky Ball said:**
> Please do not post duplicates about the same issue, even if they are reworded or expanded upon. Just edit your first thread and if you don't get action for twelve hours or so, just post 'bump' in the thread.

Sorry about that. While the issues are related I decided to keep them separate because the workarounds I was looking for seemed to be different enough.

---

### Post by mikee2 on 2016-02-01
> **grahammechanical said:**
> I am a bit confused by you saying that you want to disable the secondary monitor. Do you have 2 monitors? Or is this the imaginary monitor that Unity thinks you have?.

There is no secondary monitor in reality. It is a digital audio receiver that Ubuntu is treating as a monitor. I send the audio out of my machine to this receiver via HMI for surround audio. Since Ubuntu thinks this is a monitor as well as a receiver, it has assigned a desktop space to this 'monitor'. This is the problem, because I am not using my sound receiver as display. Normally you would simply output the signal to the TV and you are good to go, but the receiver has limited output resolutions, and therefore I am not using it for a display.

As per your other comment, I am not able to use any other outputs for sound, as there simply arent any on my machine. I am running a NUC that has only HDMI and mini display for sound.

---

### Post by Vladlenin5000 on 2016-02-02
I understood your problem since the beginning and I'm sorry the simple solution doesn't work for you. Indeed, the mirror option must use the best _common_ supported resolution for both, by design. Also by design is the 'ghost' monitor appearing when you connect the surround sound receiver. Those devices weren't designed to be connected directly to a regular video HDMI port; they were designed to be connected to the TV's audio-only output HDMI port for and as part of home theater systems.
I suspect a similar issue would happen in Windows as well and I'm sorry I'm out of suggestions.

---

### Post by mikee2 on 2016-02-03
I was able to 'stack' the desktops on top of each other so Unity acts as though there is only one desktop by using:

**[COLOR=#111111][FONT=Ubuntu]xrandr --output NAME-OF-DISPLAY1 --rate 60 --mode 1920x1080 --fb 1920x1080 --panning 1920x1080* --output NAME-OF-DISPLAY2 --mode 1920x1080 --same-as NAME-OF-DISPLAY1[/FONT][/COLOR]**


, but I dont think this is quite the solution I am looking for, but I am happy with it as a workaround. I saw that others had the same issue with audio receivers being treated like displays and thus allotted desktops, but a working solution might be more advisable, as I foresee more posts like this coming in teh future with people updating their sound systems to more recent technology. 

I would hope that the developers are able to address this quirk at some point.

---

