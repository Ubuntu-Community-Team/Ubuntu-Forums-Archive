---
title: "Logitch Headset + Mic Troubles"
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by Adamaeus on 2007-10-07
Heya, guys. I recently bought a headset/mic combo that was labeled as being Skype certified, but when I plug them in (usb), I get no audio. The headset has an audio control pad and when I press plus or minus, Ubuntu shows that there's audio activity--but the headset isn't playing anything; and I tried recording my voice in Audacity, and got nothing but silence on the line.

What'd I goof up?

---

### Post by linuxwizard on 2007-10-07
in terminal > lsusb post back what is lists

Look over these for mic
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by Adamaeus on 2007-10-08
```

Bus 001 Device 007: ID 046d:0a02 Logitech, Inc. 
Bus 001 Device 005: ID 045e:0053 Microsoft Corp. 
Bus 001 Device 004: ID 07b2:0900 Motorola BCS, Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

Tried the stuff recommended on the sites you listed, but no luck.

---

### Post by linuxwizard on 2007-10-08
What is the model number ? Can't find anything on that ID #

---

### Post by Adamaeus on 2007-10-08
The site tells me it's Premium USB Headset 350. And it's marked as being compatible with Windows and OS X, but nothing on Ubuntu; did I make a bad investment...?

---

### Post by linuxwizard on 2007-10-08
Look through this see if it will help.

[http://ubuntuforums.org/showthread.php?p=3433754](http://ubuntuforums.org/showthread.php?p=3433754)

---

### Post by callan79 on 2007-10-09
> **Adamaeus said:**
> The site tells me it's Premium USB Headset 350. And it's marked as being compatible with Windows and OS X, but nothing on Ubuntu; did I make a bad investment...?

My father in law bought a Logitech 350 headset, and it works great!

You need to look at the options for your volume control, and make sure you click on your Logitech headset from the FILE >> DEVICE menu. Then you can go to EDIT >> PREFERENCES and enable the volume controls for audio capture.

I have a Plantronics headset and I get just the sliders for PLAYBACK and RECORDING, and beneath the RECORDING one is a little icon of a microphone, make sure this does not have a red cross on it.

Good luck and please post back here if you find the solution to your problem.

Rgds,
Callan

---

### Post by Adamaeus on 2007-10-09
I've tried all the stuf recommended, like tweaking the sound options; but it doesn't seem to work at all. I've been told Logitech just doesn't work with Linux for whatever reason, and that sucks, 'cause I really wanted to use Skype. 

And I am very certain that my Vista laptop has permanently died. How pitiful. :(

---

### Post by callan79 on 2007-10-09
> **Adamaeus said:**
> I've tried all the stuf recommended, like tweaking the sound options; but it doesn't seem to work at all. I've been told Logitech just doesn't work with Linux for whatever reason, and that sucks, 'cause I really wanted to use Skype.

Hi,

I can confirm, per my post above, that Logitech headset DO work with Linux - my father in law has (I think) the Logitech 350, and sister in law has (I think) a Logitech 250 or similar.

Both work just fine in Skype

Things I'd try from here :

1. Check volume control settings again per my post above, make sure you are selecting the right device

2. Make sure your Skype settings (options >> sound devices) are all set to use the USB headset

3. Just in case some settings are messed up, download FEISTY live CD, boot with the live CD, grab skype, plug in your headset and see what happens.

4. Just in case, try the live CD on someone else's computer


Good luck, and like I said, I have two people using Logitech USB headsets so I know they work, both using Ubuntu 7.04.

Let me know how you go!

Cheers
Callan

---

### Post by Adamaeus on 2007-10-11
Well, now certain audio will play through my headset--like the sound effects on Gaim when someone posts a message--but others, like music played through VLC, play through my computer's speakers. 

And my mic STILL isn't capturing, and I've played with the volume controls to no end. 

I am incompetent.

---

### Post by callan79 on 2007-10-11
> **Adamaeus said:**
> Well, now certain audio will play through my headset--like the sound effects on Gaim when someone posts a message--but others, like music played through VLC, play through my computer's speakers. 
And my mic STILL isn't capturing, and I've played with the volume controls to no end.

Hi,

On your system menu, under preferences and then sound, what are all your devices set to there?

On my father in law's machine I didn't have to touch any of that stuff as we only use the headset for Skype (so we choose 'USB Device' in the skype options), but if you're having issues with some sounds coming from different places, maybe this is messed up?

Also did you try booting from the live cd?

Cheers
Callan

---

