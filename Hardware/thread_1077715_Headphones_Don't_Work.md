---
title: "Headphones Don't Work"
date: 2009-02-22
forum: Hardware
---

### Post by screaminj3sus on 2009-02-22
Ok, so my headphones ONLY work if they are plugged in while I boot ubuntu, If at anytime they become unplugged, plugging them abck in does not work, no matter what I do no sound comes from them. To get them to work again I have to restart ubuntu, which is annoying as hell. Is there anyway I can get ubuntu to work with them correctly?

I am running Ubuntu 8.10 64 bit on a  gateway m6862 laptop.

---

### Post by screaminj3sus on 2009-02-23
do people respond in these forums anymore?

---

### Post by screaminj3sus on 2009-02-23
It does not show a headphone jack anywhere in the sound manager:

[http://i39.tinypic.com/29fs37k.png](http://i39.tinypic.com/29fs37k.png)
[http://i44.tinypic.com/8xr9ed.png](http://i44.tinypic.com/8xr9ed.png)

And I've tried unumutingand turning up the volume of everything in there but it has no effect at all.

When I leave my headphones in while my pc boots so they work the "front" channel seems to control the volume of my headphones. It also controls the volume of my laptop speakers when the headphones aren't in.

---

### Post by screaminj3sus on 2009-03-24
???. 

For some reason they've stopped working all together now even when they are plugged in at boot.

---

### Post by sgosnell on 2009-03-25
Run the alsa mixer, and on the Switches tab, make sure the headset box is checked.

---

### Post by screaminj3sus on 2009-03-25
yeah that's my main problem, in alsa mixer of the channels gui there is NO headset/headphones or similar channel. I have tried enabling everything there to no avail, I posted a screenshot in my original post of the channels I get.

---

### Post by sgosnell on 2009-03-25
Click on the speaker icon in the panel.  When that opens, click on the bar that says "volume control".  That opens the alsa mixer, and the dialog should have 3 tabs - Playback, Switches, and Sound Theme.  Click on the Switches tab, and you should see one line, which says "headphones".  Make sure the checkbox is checked, and your headphones should work.  If they don't, you may have a soundcard which isn't supported in Linux.

---

### Post by phantom3113 on 2009-03-25
You have the same problem I do! I haven't gotten my issue fixed yet, although I have posted a bug on launchpad. I have a gateway also, although it's a T-1621. Could you post the output of aplay -l? This will show which sound card your laptop is using and we can hopefully go from there. I'm hoping that since your laptop is a different model that your problem is fixable, but we'll have to see. For the meantime, there is a small series of commands you can run to reload the sound (as if you rebooted the computer, but without rebooting)

```
killall pulseaudio

sudo alsa force-reload

pulseaudio -D
```

You can run this whenever you plug anything into the front jack after booting the computer and it will reload the sound module, or whatever controls (alsa I presume...) A few notes though: make sure you have anything that uses sound closed when you run these as you'll have to close and reopen them anyway. Also, when you do "sudo alsa force-reload" you may get a dialogue box saying that "volume control" has stopped running, or something similar. Leave this alone until you're done. Once you run "pulseaudio -D", you can tell it to reload.

---

### Post by screaminj3sus on 2009-03-26
thanks for responding!
here is that output:
```
brandon@brandon-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
brandon@brandon-laptop:~$ 

```

---

