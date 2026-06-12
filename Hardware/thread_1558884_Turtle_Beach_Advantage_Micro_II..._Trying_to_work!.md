---
title: "Turtle Beach Advantage Micro II... Trying to work?!?!"
date: 2010-08-22
forum: Hardware
---

### Post by locoHost on 2010-08-22
I have this USB sound card installed in Lucid. Lucid sees the USB sound card and knows exactly what it is. It's in the sound settings. I disabled my onboard sound and then commented out the options snd-usb-audio index=-2 lines in /etc/modprobe.d/alsa-base.conf. I even started up alsamixer and selected the USB sound card. Saw all this in other posts. I rebooted and of course I still didn't hear any sound. I started up XBMC and fiddled with the sound settings in there a bit and then I started hear intermittent sound! So that was a bit encouraging. I exited XBMC and started up a radio station on Rythmbox. I could hear intermittent music. Long pauses and then music then a long pause, repeating like this sorta random. What does this mean? Is there something else I need to do in alsa-base? Or other?

----------------------
UPDATE: I tried Ubuntu's system test. I just did the audio tests. The test recognizes the USB sound card by name and it's labeled the [Default] sound card! So that's very encouraging. However the test mimics what I heard in the music. I could click the test button repeatedly and I would only hear the test tone intermittently, kinda random.
----------------------

Thanks again for sharing the expertise guys :-)

---

### Post by locoHost on 2010-08-23
Googling, I've found a few people who have said that this USB sound card "works out of the box" with 9.04 and 9.10. If that's true, why not in Lucid?

---

### Post by locoHost on 2010-08-23
Yeah I didn't really think I'd get a lot of replies, but *no* replies?!?! ;-)

Anyway, I've [SOLVED] my problem with this USB sound card! The last one was hard to resolve. Googled for quite a while before finding it.

1. In your bios setup, disable your onboard sound
2. Edit the /etc/modprobe.d/alsa-base.conf file, comment out the line the prohibits the USB sound card from being the defualt card. It's at the bottom. Mine said 'options snd-usb-audio index=-2'. Put a # in front.
3. In terminal run alsamixer and select the USB sound card. It might be the only one, but double check. Reboot.
4. Click the little speaker icon top right. In your sound preferences select the USB sound card in the hardware tab. Select the digital audo output if that's what you want.
5. *Make sure you're using a short optical cable!* Mine was 25' long and this tiny USB sound card does not have enough power to tranmit accurately over that distance. Moved the PC into the audio cabinet and switched to a 1.5 foot cable.

Before I switched to the short cable, my sound would seem like it wanted to work, it would work then pause, then work a second or two, then pause, pretty randomly. Turns out the signal was degrading over the long cable. You wouldn't think that'd be an issue with digital, but it sure is. Especially when the device is very low power like this thing.

Anyway, my sound is thru my A/V amp and it is wonderful now! I hope this helps someone else.

MD :-)

---

### Post by Grim_Fandango on 2011-03-23
[NOTE: the solution of this thread is in comment #3]


Hi locoHost,

Thanx for this useful info that you posted despite the fact that nobody helped you  :D
Now that you've got it working could you tell me if DTS-sound works with this device?
I'm thinking of bying a netbook with decent HD capabilities with HDMI out for video and since my (old) audio receiver doesn't have HDMI I'll have to connect it using Toslink or digital coax.
One other question: you're using the Turtle Beach for audio out, what connection do you use for video out?

Thanx in advance for the info,
Jimi.

---

