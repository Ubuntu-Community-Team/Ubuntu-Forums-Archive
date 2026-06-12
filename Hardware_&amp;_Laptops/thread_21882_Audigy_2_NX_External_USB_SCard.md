---
title: "Audigy 2 NX External USB S/Card"
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by Mase Track on 2005-03-24
Has anybody got one? 

And were they successful in getting it to work?

I have on board sound, and the External USB soundcard, which is cool as I can have music etc anyway. But I'm still a bit miffed I got some nice hardware sitting around not being used!

Any info on the subject would be great!

---

### Post by WMCoolmon on 2005-04-09
I've  been able to get mine to work by setting the OSS output plugins to /dev/dsp1 and resampling to 48000 hz. However, I haven't figured out how to fix it for the apps that only use the default OSS settings. What I've been doing is really a workaround...a fix would be great.

---

### Post by WMCoolmon on 2005-04-11
OK, thanks in part to crimsun, I've got the NX working; although the solution will require individually configuring apps, and I'm not sure how to fix the main Gnome sounds to play properly.

Edit: Realized -r should really go in default_options instead of spawn options.

**Part 0: Setting up Esound**
Go into the console and type "sudo gedit /etc/esound/esd.conf". You should see a line labelled default_options, something like this:
```
default_options=
```
Add to that line "-r 96000"
```
default_options=-r 96000
```

To try out your changes, go into the console and issue the command "killall esd". Then, type "esd" followed by the command line options in the spawn_options variable, and an ampersand. So, using the above example, the line would look like this:
```
esd -terminate -nobeeps -as 5 -r 96000 &
```

This will restart the sound server. At this point, you should be able to select the Esound output from an player and have it work fine. Once you reboot your computer, changes will automatically take affect.

Note that the NX must be set as the default card in alsa to use it (See part one), or you must tell esound to use it by adding the "-d" parameter. (Do esd --help for details.)

[color=red]Also note that Esound sounds significantly worse than directly using ALSA to resample[/color]

**Part one: setting the NX as the default card.**
Set your card to have an index of -2 in /etc/modprobe.d; For me, the command was simply:
```
echo "options snd-via82xx index=-2" | sudo tee -a /etc/modprobe.d/alsa-base
```
Replace snd-via82xx with the name of the ALSA driver for your sound card. (Unfortunately I don't know a simple way to find it out as of this writing)

**Part two: resampling the sounds so things sound decent**
This is only necessary if you must use ALSA, and can't use Esound.
Open up .asoundrc in your favorite text editor and paste in the following:
```
pcm.nx {
        type plug
        slave {
                pcm "hw:0,0"
                rate 96000
        }
}
```

**Part three: setting up apps to use the resampler**
Basically, change the ALSA device to "nx". For example, in XMMS, right-click the main display, select "Options->Preferences...". Go to the Audio I/O plugins tab, select the ALSA output plugin, and hit configure. Then, in the "Device" field, enter "nx" (It will not appear in the list). Click OK, then OK again, and start a sound playing. It should sound fine.

**Part four: setting up OpenAL**
Open up .openalrc ("sudo gedit ~/.openalrc"). Add (or replace) the following lines so that they look *exactly* like this (The ' is not a typo):
```
(define devices '(esd alsa))
(define sampling-rate 48000)
```

**But I don't want the NX to be the default card!**
In that case, do cat /proc/asound/cards. Figure out what number the NX is (The number will be just to the left of the "[NX             ]"). Then, in .asound, rather than this:
```
                pcm "hw:0,0"
```
use this
```
                pcm "hw:#,0"
```
Where "#" is the number of your NX.

Then, whenever you want to use the Audigy 2 NX, use the instructions for #3 to tell the application to use it for output.

---

### Post by The Warlock on 2005-05-13
> **WMCoolmon]OK, thanks in part to crimsun, I've got the NX working said:**
> 

Okay, I did that and it works (at least with XMMS, I really don't care which sound card the Gnome desktop sounds use) but I'm getting this buzzing staticy stuff in the backround of my music. Is there any way to fix this?

---

### Post by azumi on 2005-11-16
[QUOTE=The Warlock]Okay, I did that and it works (at least with XMMS, I really don't care which sound card the Gnome desktop sounds use) but I'm getting this buzzing staticy stuff in the backround of my music. Is there any way to fix this?[/QUOTE]

fixed u - ?  buzzing staticy stuff in the backround ? so bit crap sound under linux with this sound card, under windows its ok :P

could som1 help me with it pls?

---

### Post by WMCoolmon on 2005-11-17
I don't know, I've switched back to Windows, after having to spend hours configuring things to get things working not as well as Windows.


I do remember that I was never able to get sound quality quite up to par with Windows...it might just be a limitation with the driver.

---

### Post by azumi on 2005-11-18
[QUOTE=WMCoolmon]I don't know, I've switched back to Windows, after having to spend hours configuring things to get things working not as well as Windows.


I do remember that I was never able to get sound quality quite up to par with Windows...it might just be a limitation with the driver.[/QUOTE]

im beginner but i fixed it :KS

i only compiled/install 2.6.14 Vanilla Kernel (latest) + ck Patchset (Enhanced Performance kernel) ... [http://doc.gwos.org/index.php/2.6.14_Vanilla](http://doc.gwos.org/index.php/2.6.14_Vanilla) and audigy nx 2 USB work fine :D with IBM T41p machine and UBUNTU 5.10

---

