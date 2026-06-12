---
title: "Headphones problem"
date: 2009-12-06
forum: Hardware
---

### Post by Laucien on 2009-12-06
Ok, I know many ppl had a problem when headphones are not working etc., but my problem is kinda opposite.

My headphones broke and jack got stuck in the laptop. I tried to get it out but it's ******* impossible, so I need a way to make laptop play sounds on speakers instead of headphones. Any ideas?

---

### Post by Laucien on 2009-12-06
Ok, I've seen lotz of ppl use GNOME Alsa Mixer for things like this, is there a way to do it with it? This is what I see when I start it:

[IMG]http://i49.tinypic.com/2zxw3nn.png[/IMG]

---

### Post by JK3mp on 2009-12-06
Disable headphones under switches. There should be an option there somewhere where you can UN check headphones thus it will ignore headphone jack.

---

### Post by Laucien on 2009-12-06
Yeah, that's what I've hoped to do, but there is no option for headphones. This on the picture is all I have to work w/.

---

### Post by JK3mp on 2009-12-06
Hmm... how about when typing alsamixer in terminal?

---

### Post by Laucien on 2009-12-06
[IMG]http://i49.tinypic.com/mbmnpz.png[/IMG]

---

### Post by Laucien on 2009-12-10
Ugh, anyone?

---

### Post by Laucien on 2009-12-11
Why would someone make a help forum where nobody actualy helps?
This sucks :/

---

### Post by RedSingularity on 2009-12-11
Do you have pulseaudio installed?

---

### Post by Laucien on 2009-12-11
Yep.

---

### Post by RedSingularity on 2009-12-11
How about the Pulseaudio device chooser?  Look under Apps>Sound and video.

---

### Post by Laucien on 2009-12-11
I have it too.

---

### Post by RedSingularity on 2009-12-11
Get that running on your taskbar and try selected other options for sound under "Default Sink".

---

### Post by Laucien on 2009-12-11
It asks me to enter a sink name.

---

### Post by RedSingularity on 2009-12-11
Ok click the little icon in the system area and choose "Config local sound server"

Check off the first 3 boxes.  

Then under sink you should be able to choose.

---

### Post by Laucien on 2009-12-11
First, I have two boxes and not three, and second, they aren't even checked, so I can't check them off. :D

---

### Post by RedSingularity on 2009-12-11
Sorry, i meant to say turn them on. :)

---

### Post by Laucien on 2009-12-11
It still asks me to enter name, I can't choose anything...

---

### Post by RedSingularity on 2009-12-11
Ok, go to the icon and select volume control.  Under output devices you should have some choices.

---

### Post by Laucien on 2009-12-11
Ok, I've cecked EVERYTHING possible in 'Config local sound server', and now I have this:
[IMG]http://i49.tinypic.com/kf00nl.png[/IMG]

---

### Post by RedSingularity on 2009-12-11
Make one of those your default output and see if you can hear anything.  When your done reboot the computer.

---

### Post by Laucien on 2009-12-11
Still nothing :(

Maybe I should just uninstall and install everything back :/ (p.s. does gnome alsa mixer have anything with this?)

---

### Post by RedSingularity on 2009-12-11
Yeah....the computer uses alsa for sound.  Pulse is just a server that runs so that you can hear multiple streams of sound.  You cold do a complete reinstall but first try uninstalling pulse and rebooting.

---

