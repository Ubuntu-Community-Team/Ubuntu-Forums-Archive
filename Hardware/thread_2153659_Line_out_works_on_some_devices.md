---
title: "Line out works on some devices"
date: 2013-06-11
forum: Hardware
---

### Post by rghthndsd on 2013-06-11
Background, system information, and things I've tried down below. Thanks for any help or suggestions in advance.

Problem: If I hook my line out (from back of the desktop) to my monitor input, my sound works. Plugging the same thing into my 40" Toshiba TV produces no audio. Removing the aux cable completely from my line out (my desktop has an internal speaker) produces audio.

Background: Wanted a computer to hook up to my TV something nice and cheap, and that's exactly what I got when my neighbor moved out and put an old (e.g. still has AGP) computer curbside. Put in a new graphics card (they still make AGP graphic cards?!?) and wireless card and I was all set to go.

System information: The desktop is hooked up via HDMI and an aux cable from line out into the TV. Running Ubuntu 12.04 LTS. Alsamixer seems to recognize two audio cards: Intel 82801D8-ICH4 and HDA ATI HDMI. Don't know why that is though. Selecting the ATI card in Alsa gives on one thing: S/PDIF while the Intel card has a whole slew of options. So I'm fairly certain my audio is coming from Intel.

Things I've tried:

1. Windows XP: Had the whole rig running fine on Windows XP before I switched over to Ubuntu. Same cables, say hookups, everything.
2. Alsamixer: unmuted and maxed out everything.
3. [This page]("http://pricklytech.wordpress.com/2012/05/26/ubuntu-12-04-dell-vostro-3750-no-sound-when-headphones-are-plugged-in") which had me change some options in analog-output-headphones.conf
4. [Step 1 here]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") running a massive command which I honestly never checked to see what it did...

---

### Post by Yellow Pasque on 2013-06-11
You can probably get audio over the HDMI cable using workaround 1 here:  [https://bugs.launchpad.net/bugs/864735](https://bugs.launchpad.net/bugs/864735)

---

### Post by rghthndsd on 2013-06-13
Perfect! Thanks! While I was aware that HDMI *could* transmit audio, I thought since I was using HDMI out on a video card that there would be no audio to transmit. Thanks again.

---

### Post by rghthndsd on 2013-06-13
I spoke to soon. I get clear audio when I use "Test Sound" in the audio settings, but a crackling noise on Hulu and Youtube. The audio is also significantly higher pitched although not noticeably sped up. Reading around I find similar problems back in 2009 with problems in the default pulseaudio settings, but I can't seem to find anyone saying this with 12.04, nor instructions for fixing it.

Any suggestions?

---

### Post by Yellow Pasque on 2013-06-14
> Any suggestions?
Use the latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
If, after rebooting, it still doesn't work, you can try: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

Other than that, I'm out of ideas.

---

