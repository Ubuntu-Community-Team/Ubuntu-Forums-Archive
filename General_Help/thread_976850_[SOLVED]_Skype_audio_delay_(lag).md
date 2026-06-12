---
title: "[SOLVED] Skype audio delay (lag)"
date: 2008-11-09
forum: General Help
---

### Post by richbl on 2008-11-09
Hello all,

Recently upgraded to Ibex (8.10) with no significant problems.

I have, however, run into an issue with Skype (2.0.0.72). For some--as yet unidentified reason--I'm getting significant audio delays of up to 15 seconds. Interestingly, receiving (incoming) audio is not delayed, only transmitting (outgoing) audio. In all cases, video appears to fine (<@2 second lag).

As for configuration, the webcam I'm using is a Logitech Quickcam Communicate Deluxe (id 046d:0992), and works fine with other applications.

I've read that there have been ongoing issues with Skype and PulseAudio. To that end, I've tried using Skype 2.0.0.72 static and OSS static builds, but with no success.

[B]Has anyone come across a solution for this problem?

Are there any further diagnostics that I can perform to help further troubleshoot the issue?[/B]

Thanks.

---

### Post by amontero on 2008-11-11
Exact same problem here.

The delay seems to grow and grow throughout the first minute.  At first, there is only a second or two lag...then five, then ten, then it gets so long I give up.

Any ideas?

---

### Post by NMZmaster on 2008-11-11
Ditto (using PulseAudio on my setup); the lag starts out as a second or so and then just grows and grows until conversation is impossible.  Is this a known bug?

---

### Post by richbl on 2008-11-12
Well, much as I hope PulseAudio is the panacea that folks have been talking about, clearly it has not yet matured to that point. Either that, or Skype needs a serious upgrade... Or both!

In any case, the solution (as kindly presented to me on the Skype forum here: [http://forum.skype.com/index.php?s=&showtopic=237601&view=findpost&p=1059071](http://forum.skype.com/index.php?s=&showtopic=237601&view=findpost&p=1059071)) is to change the audio settings in Skype Options/Sound Devices.
[B]
So, in my case, I changed my Sound In setting from "pulse" to USB Device (plughw).[/B]

That solved my interminable lag problem in Skype.

Thanks all.

---

### Post by michal6103 on 2008-11-24
Unfortunately, this is not solution, this is workaround.

---

### Post by andy80 on 2008-11-29
I fixed the problem using this workaround, anyway I'm really getting sick about this ****-proprietary software!

---

### Post by october1917 on 2008-12-06
Just uninstall this terrible pulseaudio and restart. Then go to Skype preferences and chose **default** option for the sound devices.

It will ask you to uninstall ubuntu-desktop too. Don't be afraid. Do it.

The integration of PulseAudio was a BIG mistake for the Ubuntu developers. As the developer of PulseAudio says
> Some distributions did a better job adopting PulseAudio than others. On the good side I certainly have to list Mandriva, Debian[3], and Fedora[4]. **OTOH Ubuntu didn't exactly do a stellar job. They didn't do their homework. Adopting PA in a distribution is a fair amount of work, given that it interfaces with so many different things at so many different places. The integration with other systems is crucial.** The information was all out there, communicated on the wiki, the mailing lists and on the PA IRC channel. But if you join and hang around on neither, then you won't get the memo. To my surprise when Ubuntu adopted PulseAudio they moved into one of their 'LTS' releases rightaway [5]. Which I guess can be called gutsy -- on the background that I work for Red Hat and PulseAudio is not part of RHEL at this time. I get a lot of flak from Ubuntu users, and I am pretty sure the vast amount of it is undeserving and not my fault.At least **in my case** the un-installation of pulseaudio DID solve many problems.

---

### Post by armorsmith42 on 2008-12-11
I would be wary. I did this and It must've removed an Xwindow dependency because when I next tried to login, the session lasted for less than 10seconds and logged out, bringing me back to the login screen.

how I fixed this:
from the login screen hit ctrl-F3
this brought me to a text based login
username:afarrell
password:gullible

and once logged in, I just reinstalled the package:

afarrell@ender$ sudo apt-get install pulseaudio
password:gullible
afarrell@ender$ logout

which brought me back to the normal login screen.

---

### Post by baytuni on 2008-12-13
I still have this problem since I do not have an usb sound drive. Is there any permanent solution or why this post is flagged as solved?

---

### Post by AstroLlama on 2008-12-16
by changing the options to plughw I lose outgoing sound! it doesn't work for me... :(
anyone have any ideas?

---

### Post by crc294 on 2009-01-05
I am having the same lag problem with pulse. When I change the Sound In option to hw or plughw, or default, or headset, or anything but pulse, I get "problem with audio capture". 

Has anyone had success with this workaround?

---

### Post by october1917 on 2009-01-05
I have already answer how i did it in the previous page.

I don't know why armorsmith42 had this problem, but i said IF you are prompted to remove ubuntu-desktop dont' be afraid to do it.

I didn't say to remove all dependecies you are prompted to remove. If armorsmith42 tried to do what i suggested and he was prompted to remove more than ubuntu-desktop, he should better post back a question. :(

I suggest you to follow my instructions of 1st page unconditional.

The choice is yours. Good luck. :D

---

### Post by olskar on 2009-02-05
Is there a bugreport for this?

---

### Post by dmuir on 2009-02-08
Tried uninstalling pulseaudio, but ended up breaking half the applets on my panel (including the fast user switcher). Yes, the only two packages uninstalled were pulseaudio and ubuntu-desktop.

As for using hw or plug-hw. Works for me when doing skype-skype calls, but not skype-out calls. For the latter, it seems to be an issue with the network stack. Still trying to figure part out.

---

### Post by Thorndeux on 2009-03-09
Hey all, I just wanted to quickly report my experience here: I had the same audio lag problem both on SkypeOut and on normal Skype. Now I switched the setting for 'Sound In' in Skype's audio settings from 'pulse' to 'plughw' (here I had several choices and found the right one through trial and error) and at least SkypeOut works flawlessly now. I haven't tried the Skype proper yet.

---

### Post by AstroLlama on 2009-03-16
Yay, I was having lag on skype out calls, very frustrating, but I solved it by setting my skype out to plughw setting. thanks community, less than 10 minutes of internet searching.

edit: haha, forgot that I posted on this thread a while back...

it seems that the problem remains for me, but setting it to plughw makes it happen slower... sigh.

---

### Post by omelette on 2009-04-29
Setting this problem to "Solved" was definitely premature - reminds me of the Opera browser Linux fix of disabling IPv6, only worse! :)

Anyhow, although I've come across many references suggesting that Pulse Audio's performance is somewhat less than stellar, up till now it wasn't an issue for me as everything worked fine.  Unfortunately, the delay amkes Skype completely unusuable and selecting any of the alternatives for 'Sound In' results in either silence, or Skype terminating the call automatically due to a "capture problem".

So, imo, definitely not "Solved"...

---

### Post by theparadoxical on 2009-05-15
I solved it.. by running a vmware with windows ()so.. i not solved it) I am not removing Pulse as I have very bad experience with removing packages, and it is a dependecy in Jaunty

Skype should update its client. If there was a choice I would never use that terrible client again.

---

### Post by neithere on 2009-05-17
Same here. Kubuntu 9.04 with all updates, latest Skype, delay growing forever(?), quickly turning the talk into a monologue.

Only "pulse" settings works for both in and out.

---

### Post by halloween2311 on 2009-05-26
I had the same issue and here is how I fixed it... for me at least! ;)

I went to system-preferences-sound and under audio conferencing set sound playback and sound capture to the device I am using for Skype. (In my case Logitech Wireless headset - OSS.)

Then in Skype audio settings I set my "Sound In, Sound Out, & Ring" from pulse to match what I had set in the system sound preferences (In my case Logitech Headset)

I have tested this on both pc to pc calls and pc to phone with no delay or lag whatsoever. This also allows me to continue to use pulse for my other programs without issue.

Any way, this worked for me, hopefully it will help someone else out too!  :p

---

### Post by mazamazine on 2009-06-03
Hi,
I'm on Jaunty and since I've uprgraded : same problem.
So I want to tell you all that removing pulse worked for me

---

### Post by benbois on 2009-07-10
I confirm.. removing pulseaudio solved the problem with Jaunty.. strange, before to remove this package, it was not possible to get any sound in Skype with the other options than pulse?!

---

### Post by jmjohn on 2009-07-10
I use "pulse" for "Sound Out" and "Ringing" and  for "Sound in" I use the hw device.

Pulse for "Sound in" was giving me massive 30 second delays with Pulse.

Write an email to [email]support@skype.com[/email] and ask for a new Linux release with bugfixes and proper pulseaudio support.

---

### Post by pallabbasu1234 on 2009-07-13
pulse audio sucks, it is still a buggy software.

---

### Post by october1917 on 2009-07-13
In case you refuse to remove pulse, there is [a guide to fix the pulse audio issues](http://ubuntuforums.org/showthread.php?t=789578).

Reboot.

Then open Applications-->Sound & Video-->PulseAudio Volume Control and adjust sound volume to the prefered levels.

After doing all these, go to System-->Preferences-->Sound and select Autodetect in ALL "Sound Playback" field. Select ALSA in "Sound Capture" field.

Then go to Skype options, and select Sound Devices. Set Pulse to "Sound Out" and "Ringing" and play a little with the "Sound In" option, until you find the appropriate configuration. DO NOT FORGET to _un-tick_ the "Allow Skype to automatically adjust my mixer levels" at the same dialogbox.

I hope this helps.

---

### Post by gmorph on 2009-08-12
Just adding my experience. Skype was having +10 seconds delay in conversations. I am running Ubuntu Jaunty (9.04) 64bit on a Dell M1330. My Ubuntu installation history is I upgraded from 8.04 to 8.10 and then 9.04. I followed the instructions on fixing pulse audio as per the link in october1917 post. However, whilst I could now hear the remote end without any delays I still had significant delays communicating with them. In my Sound Devices in Skype I set "Sound In" to "HDA Intel (hw:Intel,0)" and left "Sound Out" and "Ringing" as "pulse" and that solved my problem immediately. I also tried the "HDA Intel (plughw:Intel,0)" option on "Sound In" but that didn't help.

Hope this helps someone else.

---

### Post by life-on-mars on 2009-08-21
> I also tried the "HDA Intel (plughw:Intel,0)" option on "Sound In" but that didn't help.

Choosing plughw devices still routes the sound through Pulseaudio.


-------------

I think Pulseaudio is just not fully matured yet. I'm even running it with realtime support enabled but the problem occurs anyway. However, they made quite some progress since the first time it was integrated into Ubuntu. Once the software and implementation is matured, we will never wish it away again.

---

### Post by m0ar on 2009-09-07
[http://pastebin.com/f2658dda9](http://pastebin.com/f2658dda9)


Is this an okay way to put it to skype? :)
I'm not used to writing formal messages in english, neither am I that into linux :D

---

### Post by rlarrowe on 2010-06-14
for all programs that use alsa do:

pasuspender -s=alsa -- <the program you want to run>

---

