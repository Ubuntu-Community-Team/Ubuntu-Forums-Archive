---
title: "Is there a USB audio device I can buy so audio on my laptop &quot;just works&quot;?"
date: 2010-12-24
forum: Hardware
---

### Post by clanmackay on 2010-12-24
I've used Linux for years: different distros, hardware, etc.  And as everyone here knows, getting audio to work, and work consistently, is the bugbear of this whole operation.

After tens of hours of playing around with my new machine, to get it to work as well as some of my previous machines worked, I'm sick and tired.  I loathe Windows, but I don't want a hobby operating system right now.

I'm on Maverick.  **Surely** there exists at least one stable combination such that someone can:

1.  Tell me the manufacturer and part number of a USB audio device to buy.
2.  Tell me the audio driver/settings/etc. to use to get it so it works in the way that it works on every commercial operating system: that is, I start up the machine, and audio is on, and it works in every program, and it works simultaneously in multiple programs, and if (say) a movie player crashes it doesn't take the whole system down with it.

Even if the instructions include items such as "set [program1] to ALSA in 'Options'" and "don't use [program2] at all", there has to be an off-the-shelf way to get this to work, in Maverick, with an arbitrary laptop.  There *has to*, right?

(Yes, I'm frustrated at this point.)

---

### Post by Fafler on 2010-12-25
I brought this for an extra sound output to play MP3's around the house. Works just fine. [http://cgi.ebay.com/USB-2-0-MIC-Speaker-5-1-Audio-Sound-Card-Adapter-/110528831748?pt=LH_DefaultDomain_0&hash=item19bc082104](http://cgi.ebay.com/USB-2-0-MIC-Speaker-5-1-Audio-Sound-Card-Adapter-/110528831748?pt=LH_DefaultDomain_0&hash=item19bc082104)

It shouldn't really require any work. Just plug it in. If you onboard sound card is partially supported, claimed by a module but no sound comes out, you should blacklist it from loading during boot. [http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

---

### Post by clanmackay on 2010-12-25
Thank you **@Fafler**.  I've made the purchase.

To mods: Should I mark this "Closed", or leave it open so I can come back to confirm that it worked for me?

Thanks again.

---

### Post by clanmackay on 2011-01-10
OK, I got the device.  At first I couldn't get it working in PulseAudio, so I switched to ALSA and got it running there.  I can confirm that it works in ALSA.  But I wanted to have PulseAudio's fancy channel mixing stuff available.

To get the USB audio device working from a PulseAudio-free Maverick install:

Type:
```
sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter glew-utils
```glew-utils was suggested, so I installed it.  I doubt it's required, though.

Type:

```
gksudo cp /etc/asound.conf /etc/asound.conf.bak
gksudo gedit /etc/asound.conf

```
Replace any text with the following:
```
pcm.pulse {
    type pulse
}
ctl.pulse {c;ocl
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

Save it, save your other work, and restart your system.

Go to Applications --> Sound & Video --> PulseAudio Device Chooser from the main menu.  This will put an icon into your tray.  Left-click it and select "Preferences...".  Select the entry under "Startup" (this will make sure it's there next time you restart), and, if you like, turn on any of the notifications (I turned them all on.)  Click "Close".

Left-click the icon again and select "Manager...".  Go to "Devices" and make sure that your USB device shows up.  Mine shows up as "alsa_output.usb-**XXX**", where **XXX** is a long string.  If it shows up, close this window.

Left-click and go to "Volume control...".  Start some audio playing.  You should see a volume meter running.  Make sure that it's set to your USB device.  It's not clear to me how to tell, in general, which one is your USB device, but there should be a short list to try.

A weird gotcha:  On mine, in the "Output Devices" tab, the USB device has two options, "Analog Speakers" and "Analog Output".  If you switch from "Analog Speakers" to "Analog Output", there seems to be no way to switch it back without unplugging and re-plugging (or otherwise restarting) the USB device.  Don't know why.

Thanks to **@Fafler** and this good guide on [PulseAudio]("https://wiki.ubuntu.com/PulseAudio") for help.

---

