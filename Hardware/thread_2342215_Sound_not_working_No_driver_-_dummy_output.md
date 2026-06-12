---
title: "Sound not working No driver - dummy output"
date: 2016-11-04
forum: Hardware
---

### Post by Blackbug on 2016-11-04
I have kubuntu 16.4.1 After upgrading some packages I started having some sound problems. I was able to resolve them after running command ```
sudo alsa reload
``` and everything started workin correctly. However, I was annoyed that I have to do it everytime I restart my OS thus I looked some fixes online. There were few which suggested to reinstall following packages after purging ```
sudo apt-get install --reinstall linux-sound-base alsa-base alsa-utils libasound2
```

I ran the above command and since then I have no sound in my OS. The sound and audio section shows no driver and just dummy output.

Any help will be appreciated.

Thanks!

---

### Post by Yellow Pasque on 2016-11-05
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Also, you may want to try reinstalling kernel package (and rebooting):
```
sudo apt-get install --reinstall linux-image-`uname -r`
```

---

### Post by Blackbug on 2016-11-06
I have already reinstalled the kernel but doesnt help. Strange thing is I can hear the sound when the OS boots up and the login screen appears. However, once I log in there isnt any sound at all. I have xubuntu, lubuntu and kubuntu DE. Sound doesnt work in any of them. Its quite weird.

The link below has all the info about the sound related configurations..

[http://www.alsa-project.org/db/?f=e6918cc3863a701cf293648ad5b4be569ee5a330](http://www.alsa-project.org/db/?f=e6918cc3863a701cf293648ad5b4be569ee5a330)

---

### Post by Blackbug on 2016-11-06
Quick update:

I installed Gnome DE and sound works there.
However, still no change in kubuntu or any other DE.

---

### Post by Yellow Pasque on 2016-11-06
```
RoarAudio:
      Installed - Yes (/usr/bin/roard)
      Running - Yes
```

I'm not sure why you have roaraudio installed, but it can definitely conflict with pulseaudio and cause the issues you mention. I'm guessing gnome starts pulseaudio before roaraudio which is why sound works there.
[https://ubuntuforums.org/showthread.php?t=2186531](https://ubuntuforums.org/showthread.php?t=2186531)

---

### Post by Blackbug on 2016-11-06
Thanks for the reply.

I uninstall roaraudio but still have to force-reload even in gnome now. Kubuntu and other DE doesnt respond to anything.

---

### Post by Yellow Pasque on 2016-11-06
If you clear the pulseaudio user conf and restart it, does it help?
```
rm -r ~/.config/pulse*
pulseaudio -k
```

Do you think you can get an updated alsa info?

---

### Post by Blackbug on 2016-11-06
Thanks for keeping up.

No, deleting the config files doesnt help. I tried it already before.

New alsa info

[http://www.alsa-project.org/db/?f=9507b502c210d54ce0adecc94b3afc77f154d0c7](http://www.alsa-project.org/db/?f=9507b502c210d54ce0adecc94b3afc77f154d0c7)

---

### Post by Yellow Pasque on 2016-11-06
Now you've got permissions issues that weren't in your first alsa info:
```
APLAY
Home directory not accessible: Permission denied
```

What in the heck are you doing? What were you attempting to do in the first place?

---

### Post by Blackbug on 2016-11-06
ah sorry. I guess I used 'sudo' while executing the alsa-info.sh script. That's why it gave the permission issue.

---

### Post by Yellow Pasque on 2016-11-06
Oh, okay. Do you still have "dummy output" in the sound control?

---

### Post by jeremy31 on 2016-11-06
This is starting to sound like an issue I had while trying to fix bluetooth audio issues.  I messed up a lot of things, so please post results for
```
dpkg -l | grep pulseaudio
```

---

### Post by Yellow Pasque on 2016-11-06
If you're seeing "dummy output", my next suggestion would be to grab a pulseaudio log (before you try reloading alsa): [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)
I'm also still curious how roaraudio ended up on your system (the few times I have seen it involved users following mpd guides). If you use mpd (or other headless audio daemon), I would suspect that first.

---

### Post by Blackbug on 2016-11-07
> **jeremy31 said:**
> This is starting to sound like an issue I had while trying to fix bluetooth audio issues.  I messed up a lot of things, so please post results for
```
dpkg -l | grep pulseaudio
```


```
dpkg -l | grep pulseaudio
ii  gstreamer1.0-pulseaudio:amd64                               1.8.2-1ubuntu0.1                              amd64        GStreamer plugin for PulseAudio
ii  pulseaudio                                                  1:8.0-0ubuntu3                                amd64        PulseAudio sound server
ii  pulseaudio-module-bluetooth                                 1:8.0-0ubuntu3                                amd64        Bluetooth module for PulseAudio sound server
ii  pulseaudio-module-x11                                       1:8.0-0ubuntu3                                amd64        X11 module for PulseAudio sound server
ii  pulseaudio-utils                                            1:8.0-0ubuntu3                                amd64        Command line tools for the PulseAudio sound server



```

---

### Post by Blackbug on 2016-11-07
> **Temüjin said:**
> If you're seeing "dummy output", my next suggestion would be to grab a pulseaudio log (before you try reloading alsa): [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)
I'm also still curious how roaraudio ended up on your system (the few times I have seen it involved users following mpd guides). If you use mpd (or other headless audio daemon), I would suspect that first.

Not sure how but now sound is working without even running force-reload I didnt changed anything. Only problem now is the Kubuntu sound applet is missing and sound cant be changed using the multimedia keys on the keyboard.


I am still skeptical about this. I will keep this thread open for a day or two until just to see if the problem reappears. I am posting the log you asked anyway.


Thanks!

---

