---
title: "Sound Problems"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by mcgodx on 2007-04-29
Hi guys, I just recently installed Feisty and most everything seems to be working just fine, except for the sound.  I used the "aplay -l" command to see what comes up, and this is what I get:

mylan@mylan-laptop:~$ aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Now past that, I went to System>Preferences>Sound, and tried all the sound playback settings, and nothing seems to be working.

Does anyone have any ideas on how to fix this?

Thanks

---

### Post by mcgodx on 2007-04-29
Any ideas?

---

### Post by mcgodx on 2007-04-30
I used 6.10 in the past and it worked just fine, however now in 7.04 it doesn't work anymore.  Like I said before, it looks like Linux is recognizing my sound card, however it doesn't seem to be working.

Just putting some more info out there.

---

### Post by mcgodx on 2007-05-01
No one has a fix for this?

---

### Post by seanmbarrett on 2007-05-01
i am having the same problem, maybe some can help soon. sean

---

### Post by clueless dave on 2007-05-01
Hey, in the spirit of checking the simple things first, did you

a) make sure the setting isn't muted, through the keyboard, or the sound icon?  Also check the "mute" option when you right-click on the sound icon?

b) make sure that the sound levels are up for the headphones, the speakers, and PCM on the "volume control" (accessed through the pull-down menu after right-clicking on the sound icon)?

I know, I know, you probably checked.  But I thought I lost access to my sound card after installing a bunch of updates to Edgy only to find out that it had somehow just been muted - easily fixed through the GUI.  After upgrading to Feisty,  the sound was way too soft- the problem turned out to be that the volume control setting for the speakers had been re-set (not by me) almost to zero. Now why this would make things so soft through the earbuds is beyond me, esp. when the other settings were OK, but upping the speaker volume made the difference.  Go figure....

Sorry if this doesn't seem relevant to your situation, but it seemed worth mentioning as a possibility before you go nuts in the terminal.

---

### Post by IPAlexander on 2007-05-01
I am also experiencing this problem.

---

### Post by mcgodx on 2007-05-02
Thanks for the tips, I rechecked everything (it did this a few times before in Edgy not sure why) but that wasn't the case.  All the levels are well up there.  I don't hear anything at all :(

I don't know what's going on, it's really strange, usually you'd think things would work better lol.

---

### Post by seanmbarrett on 2007-05-02
hey every one i tried this advice and it worked. o my toshiba a105. heres the kink.[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide) hope this helps. sean

---

### Post by mcgodx on 2007-05-02
Ah the mute got me!  Thank you so much for that link haha.  I did not notice that at all, but my "PCM-2" channel was muted.

---

### Post by unconcrete on 2007-06-16
Hi all, Iìm having too problems with sound card. It can't be a problem of jacks, mute mode or any other can shut up my sounds since If I enter my XP partition my sound card works well as use. I know my windows drivers are Realtek, but the report of hardinfo detects another card:
...
Display
Resolution	1024x768 pixels
OpenGL Renderer	GeForce FX 5500/PCI/SSE2/3DNOW!
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	ICH - SiS SI7012 *****************
Processor
...
Actually the gnome volume control detects two devices:
SiS SI7012 (Alsa Mixer)
Realtek ALC658D (OSS Mixer).
I've tryed both of them but my system is mute now. I have no idea how to set sound card advanced settings. :(:(:(
Have you any suggestion?

Thanks in advance,
unconcrete

---

### Post by unconcrete on 2007-06-16
> **unconcrete said:**
> Hi all, Iìm having too problems with sound card. It can't be a problem of jacks, mute mode or any other can shut up my sounds since If I enter my XP partition my sound card works well as use. I know my windows drivers are Realtek, but the report of hardinfo detects another card:
...
Display
Resolution	1024x768 pixels
OpenGL Renderer	GeForce FX 5500/PCI/SSE2/3DNOW!
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	ICH - SiS SI7012 *****************
Processor
...
Actually the gnome volume control detects two devices:
SiS SI7012 (Alsa Mixer)
Realtek ALC658D (OSS Mixer).
I've tryed both of them but my system is mute now. I have no idea how to set sound card advanced settings. :(:(:(
Have you any suggestion?

Thanks in advance,
unconcrete

Solved!
I've downloaded and installed the Gnome Alsa Mixer utility and I've noticed that some issues where actually set to mute (PCM). Strange, the Gnome sensor that comes with Edgy Eft doesn't see that, or I have enough skillness to use it properly.
Bye soon!

---

### Post by tv0571 on 2007-07-19
For what it is worth, I had problems with my sound upon upgrade from 6.02 to 6.10.  I had previously installed an old Aureal soundcard that I could not get running under Dapper Drake, so I had been using the onboard sound instead.  After upgrade, there was no sound - and yes, I checked all mutes, switches, and the selected soundcard in system / preferences / sound.  I switched the sound plug to the Aureal card, reselected all the Alsa settings to use the Aureal card, and it is now working - which is good, because I think it is better fidelity than the mobo.  

The interesting thing now is that the mute and volume controls on the keyboard don't seem to affect the sound, although they trigger the normal "graphic" events on the screen.  Haven't worked on that problem yet...

---

### Post by seanmbarrett on 2007-07-19
hi,
that is what i did too. worked fine. never fixed the the keyboard and on screen sound control, but still worked great with the manual volume control. sean

---

### Post by gkongk1 on 2007-07-20
Hi, I just installed it but I have sound but it is really muffled with static.  When it boots up, the sound it make is also muffled.  I setup a dual boot with Windows and when i login to the Windows side the sound is fine.  I have a toshiba satellite.  Am I missing some drivers or anything?

---

### Post by tv0571 on 2007-07-21
I was only upgrading to Edgy as an easy way to get to Feisty Fox.  I upgraded to that today and it fixed the problem with the keyboard sound controls.  No problems with sound at all now, though I still need to try the mobo digital PCM output which has never worked in the past.

I also need to try to follow HUGMENOT's instructions for getting WMA's to play.

---

### Post by tv0571 on 2007-07-21
You might look for the External Amplifier switch option in the preferences (or switches) of the volume control.  In my Ubuntu 6.01 version (Dapper Drake), it didn't seem to do anything, but in Edgy and Fiesty it cuts about 20Db off the volume.

---

