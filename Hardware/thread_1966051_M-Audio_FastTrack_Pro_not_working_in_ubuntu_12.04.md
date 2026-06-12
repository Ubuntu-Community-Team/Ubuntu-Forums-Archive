---
title: "M-Audio FastTrack Pro not working in ubuntu 12.04"
date: 2012-04-26
forum: Hardware
---

### Post by psychok7 on 2012-04-26
hi there, i just did a fresh install of ubuntu 12.04 and noticed my m-audio fasttrack pro stopped working..

everything worked fine in 11.10 , 11.04 and 10.04

can anyone help me? i completely lost my audio on my Desktop

---

### Post by psychok7 on 2012-04-26
> **psychok7 said:**
> hi there, i just did a fresh install of ubuntu 12.04 and noticed my m-audio fasttrack pro stopped working..

everything worked fine in 11.10 , 11.04 and 10.04

can anyone help me? i completely lost my audio on my Desktop

problem fixed.

installed pavucontrol , disabled all sound cards and only enabled m-audio (duplex channel) and it started working

---

### Post by psychok7 on 2012-04-26
> **psychok7 said:**
> problem fixed.

installed pavucontrol , disabled all sound cards and only enabled m-audio (duplex channel) and it started working

ok false alarm.. it was working but then after a while the card "disconected".. neither pavucontrol or ubuntu default sound software are recognizing m-audio

---

### Post by psychok7 on 2012-04-26
i did a restart and they got recognized again.

lets see wht happens now

---

### Post by psychok7 on 2012-04-28
ok so basically when i restart the computer sometimes it works and sometimes it doesnt (doesnt get recognized). is there a way to force it to always recognize?

---

### Post by zwervertje on 2012-04-30
I have the same issue.  Sometimes it works, sometimes not...
Never had a problem in 11.10 or before.
Turning off and on the device does not help.

---

### Post by oustiti on 2012-05-02
Same problem here with a FastTrack Pro, it doesn't show up in Sound Settings anymore so I can't enable it.

---

### Post by revolvingsoul on 2012-05-03
I'm having the same problem too, it worked fine in 11.10 but now ubuntu just won't recognise it.

---

### Post by adempewolff on 2012-05-06
I never tried using my Fast Track Pro with Ubuntu before 12.04 because the input channels didn't work.  Instead I used Tango-Studio and the patched kernel for it--which worked great.

However since I knew 12.04 used a 3.2.* kernel which has the FTP patch include I decided to test it out on Ubuntu and it worked out of the box--even the input channels.

Then I got greedy and tried playing with the settings in the Ubuntu Sound Settings dialoge, changed something and everything promptly disapeared.  Restarting got the output channels back but I have never since seen the input channels :(

I'll try installing pavucontrol and see if that helps.

---

### Post by Redeen on 2012-08-06
Same trouble. FT-Pro worked well in previous version running Fiesty. At first it did show up in Jack/Settings, but now it's gone from dropdown menu. Only sign of it is:  

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 47
 1 [Pro            ]: USB-Audio - FastTrack Pro
                      M-Audio FastTrack Pro at usb-0000:00:1d.1-2, full speed

But only HDA is in the dropdown now. Jack was working briefly, but I was having latency issues. MIDI worked, but sound capture was dead or anemic to the point of inaudibility. There are quite a few settings to check, but I've been through most of them.  Ardour level meter shows noise only (and messing around with Jack/Settings, I can get Ardour to produce feedback over the laptop's internal speaker). 

It took a lot of fiddling around to get Jack to work with FTPro the last time around, but seeing so many similar problems doesn't bode well.

---

### Post by Redeen on 2012-08-07
Partly solved: 


[LIST]
[*]Mixers/Mixer Alsa - changing "internal mic" to "mic" got rid of the feedback problem.
[*]Rebooting made the FT Pro visible again.  Crazy, but it seems like it prefers one USB port.
[/LIST]


Have not been able to sort out capture of audio input at all.  Monitors show constant noise (although mixer tweak above helped rid that).  The few times I see the meters jump when a signal is present, record fails.

---

### Post by zwervertje on 2012-08-24
Can't remember where I found it, but this helps for me:

sudo modprobe -r snd_usb_audio
sudo modprobe snd_usb_audio


I keep it in a sh file that I run whenever the ftt does not work on a new reboot...

---

### Post by DreamcasterTM on 2012-09-09
Nothing to do.
Too complicated for me...or just too unstable.
My M-Audio Fast Track Pro keeps disappearing from the audio device list...I managed to hear the audio test just once.
The input NEVER worked.

It hurts booting my netbook back to Win7...

There are no turnarounds...really?

---

### Post by kidoatmeal on 2012-10-14
Have you tried zwervertje's fix? Running the two commands he referenced in Terminal worked for me.

---

### Post by Redeen on 2013-05-19
Tried to no avail. But...earlier, after a recent update, everything worked...until I rebooted. Now I just need to try all eleven million permutations of settings with mysterious names and no clear explanation like "H/W monitor" - because it seems the FTP *can* work as it had in the past (emphasis on "seems").  And then I will never reboot again.

---

