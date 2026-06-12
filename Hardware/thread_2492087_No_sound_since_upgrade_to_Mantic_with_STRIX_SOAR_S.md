---
title: "No sound since upgrade to Mantic with STRIX SOAR Soundcard"
date: 2023-10-30
forum: Hardware
---

### Post by ph82 on 2023-10-30
Hi everyone,

I'm really struggling to find where to file this as a bug in Mantic. My STRIX SOAR sound card worker just fine on Lunar Lobster and after upgrade it no longer works. I can see it as a speaker to select in sound settings, when selected the system thinks it's putting sound out through it, but nothing is heard. I have a USB conference speaker plugged in that I'm using for (dreadful) audio in the mean time, and the sound card works fine when booted to my Windows partition.

I tried a very detailed bug report in alsa-driver, here: [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/708189](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/708189) - but it looks like no one really looks at those.

Has anyone had this problem, or failing that knows where I might be able to get it reported? I waited a couple of weeks to see if a patch came out but haven't seen anything that might affect sound drivers yet (e.g. a pulse, kernel or alsa style package update)

---

### Post by Yellow Pasque on 2023-11-02
Note that Ubuntu 23.10 uses pipewire to replace pulseaudio. Theoretically, users shouldn't notice this, but if you have a soundcard that needs special configuration, you may. I think I would try:
```
mkdir ~/.config/pipewire    
cp /usr/share/pipewire/pipewire.conf ~/.config/pipewire/
vim ~/.config/pipewire/pipewire.conf
```
(If you prefer another text editor rather than vim, use that.)

I would try and allow more sample rates. See: [https://wiki.archlinux.org/title/PipeWire#Changing_the_default_sample_rate](https://wiki.archlinux.org/title/PipeWire#Changing_the_default_sample_rate)
Maybe for a Strix Soar using analog output:
```
default.clock.allowed-rates = [ 44100 48000 88200 96000 176400 192000 ] 
```

I don't know much about pipewire. I just switched to it on my Debian build, and it worked well. All I had to do was allow more sample rates (to avoid unnecessary resampling) and up the resampling quality to 10 for the best experience. 'pw-top','wpctl',and 'pw-cli' might help you figure out what's going on.

EDIT: If customizing ~/.config/pipewire/pipewire.conf causes more problems than it solves, you can always delete it and logout/reboot. The standard system copy in /usr/share should be used then.

---

### Post by ph82 on 2023-11-06
Thank you so much for recommending something, it's frustrating being stuck without sound!

This didn't work for me I'm afraid.

I also tried (unrelated): [https://unix.stackexchange.com/questions/639700/disabling-onboard-sound-so-that-i-can-use-asus-strix-soar-as-default-sound-card](https://unix.stackexchange.com/questions/639700/disabling-onboard-sound-so-that-i-can-use-asus-strix-soar-as-default-sound-card)

... to no avail.

In case it helps with any analysis pw-top shows: [https://imgur.com/a/UEOUzD4](https://imgur.com/a/UEOUzD4)

---

### Post by ph82 on 2024-03-11
I managed to get this working with the stock Noble Numbat build using 'USB Speaker' (with USB sound enabled in the BIOS which I think is the default) - no changes were required apart from making sure that BIOS setting is on. This plays sound out of my STRIX soundcard without actually using the STRIX output in Sound settings. It's a good enough workaround for now.

---

