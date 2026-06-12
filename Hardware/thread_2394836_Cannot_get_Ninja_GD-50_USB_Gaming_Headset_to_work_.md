---
title: "Cannot get Ninja GD-50 USB Gaming Headset to work in Ubuntu 16.04 LTS"
date: 2018-06-22
forum: Hardware
---

### Post by nerv-agent on 2018-06-22
I'm gonna come clean. I literally only starting using Linux the start of this week (Sunday), when I finally got my Dell Precision 7520 in the mail. It's Friday, I managed to install some programs and even a Sega Genesis emulator and gamepad drivers despite the learning curve of switching from Windows all my life to Linux.

However, I cannot get something as simple as a USB headset to work in Ubuntu Linux. This is what I have:

[http://gamersdigital.com/products/ultimate-ninja-gd-50-computer-gaming-headset/](http://gamersdigital.com/products/ultimate-ninja-gd-50-computer-gaming-headset/)

This is a really nice headset and even vibrates in response to explosions and stuff in games and movies. It works fine in Windows 7, but I can't get it to work in Ubuntu Linux!

  [IMG]https://s19.postimg.cc/7o6nx17g3/useless_sound_setting.png[/IMG]

I can click "USB Audio Device" all I want, and nothing happens!

I want an immersive gaming and movie experience with this, and I don't wanna go back to Windows.

Is there a way to install drivers for this via Wine or Winetricks? Or are there already some Linux drivers that can get this to work?

UPDATE:

So I had to resort to searching Google and trying things by brute force for hours (screaming, cussing, and yelling at computer may be optional).

So I installed something called PulseAudio Volume Control, and still no sound. Then I thought I could **temporarily** disable speakers. BIG MISTAKE! PulseAudio Volume Control replaces my speakers with "Dummy Audio" or something, the sound on my system became completely inoperable and it wouldn't let me revert back.

Then I searched YouTube, and some person showed something (couldn't hear them, just had to watch the screen and figure out what was going on) about going to Software & Updates --> Additional Drivers, scrolling down to "Intel Corporation: Unknown". There were 2 options, "Use HDA driver blah blah blah audio something dah dah dah", and "Do not use this device".

The YT vid showed to select "Do not use this device" and restart, and this was supposed to work. But it did nothing.

Then I searched Google and found some random command line that supposedly resets everything:

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

Still nothing.

So I went back to "Additional Drivers" and re-enabled "Use HDA driver yo momma audio so bad she broke your speakers" or something, restarted, and the speakers AND headphones work now. You just have to select it from the sound settings, because it won't automatically switch the sound to headphones like in Windows.

I *think* I solved my problem, but who knows what will get screwed up tomorrow.

---

