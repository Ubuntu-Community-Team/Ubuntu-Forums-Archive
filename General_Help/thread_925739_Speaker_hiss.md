---
title: "Speaker hiss"
date: 2008-09-21
forum: General Help
---

### Post by joekwme on 2008-09-21
Anyone know why my speakers are hissing?

Also, I am not getting signal to my bass/subwoofer.  I am running a sound blaster card.

Thanks

Joe

---

### Post by Pro-reason on 2008-09-21
You may have a microphone or line-in enabled.  If its volume it up high, it will produce hiss even if no real sound goes through.

---

### Post by joekwme on 2008-09-22
Where can I find the volume control?

---

### Post by joekwme on 2008-09-22
Sorry.

I meant to say:

Where can I find the microphone or line-in controls?

Thanks

Joe

---

### Post by Pro-reason on 2008-09-22
There's an applet for that on the GNOME panel.

---

### Post by abhiroopb on 2009-10-21
I am getting an annoying hiss as well. When I plug my external speakers to my iPod there is no hiss whatsoever. However, when I plug my speakers into my laptop headphone port there is a very annoying hiss. As I turn my master or PCM volume up the hiss gets worse.

I am using the mic from my logitech USB camera.

---

### Post by mzilhao on 2009-11-06
> I am getting an annoying hiss as well. When I plug my external speakers to my iPod there is no hiss whatsoever. However, when I plug my speakers into my laptop headphone port there is a very annoying hiss. As I turn my master or PCM volume up the hiss gets worse. 

i'm having the same issue. i'm using karmic and here's the output of lspci
```
 lspci |grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

in my case it doesn't seem to get any better or worse if i turn up or down my master volume.

did you manage to sort this out?

thanks!

---

### Post by DeMus on 2009-11-06
Just fiddle a little with the position of the balance and fade slider in the sound applet. I had the same when using 9.10. Now with 9.04 it's gone. In other words there is something wrong in Karmic.
What it is I don't know, I also had problems with the kernel so it could be that as well.

---

### Post by mzilhao on 2009-11-06
thanks for your reply.
i tried that and it didn't work...
i've also experimented with various different configurations in alsamixer, but still no luck...

---

### Post by abhiroopb on 2009-11-22
In Karmic I have two audio related problems:

1. There are simply too many volume controls. 
Firstly, many apps have their own volume controls (e.g. Amarok) I keep this to 100%
Secondly, there is the PulseAudio individual app volume control (I have this varied depending on the app)
Thirdly, there is the master volume
Fourthly, there is my analog volume control that is on my amplifier.

It is very difficult for me to figure out ideal settings without getting a speaker hiss and hitting the optimal audio quality level.

2. The speakers hiss at very loud volumes. I can get rid of them by lowering the volume but sometimes I like to listen to my music loud. 

Strangely, the hiss has stopped now (with a fairly high volume). If I increase or decrease the volume (effectively change a setting) the hiss returns. It is almost as though the speakers switch off and then come back on.

I have tried muting the Logitech USB camera's internal mic, and I have even pulled out the USB plug. This had no effect. I have also disabled the internal mic (there is a setting in "Sound" where you can disable the mic completely).

Strangely it is absoloutely fine if I use my iPod (i.e. there is no hiss at any volume level). So, I can rule out my speakers, amp, or subwoofer crossing wires or some such problems physical problem. 

In sum, it seems that there is something going on in pulseaudio that is making my speakers hiss. Lowering the volume helps but this is hardly a solution (i.e. it is akin to having my speakers muted all the time!).

Please help!

---

### Post by abhiroopb on 2009-12-03
The speaker hiss is still there and I can only get rid of it by lowering the volume. This solution isn't exactly ideal.

Also the volume in Karmic (using pulse) is generally a little flaky. Sometimes the sound does not work. I get an error when trying to adjust the volume. Sometimes the mic stops working, etc. etc. etc.

---

### Post by smerral on 2009-12-03
I had a similar problem and I fixed it as follows:

edit /etc/modprobe.d/alsa-base.conf

Scroll to the bottom and comment the last line:

options snd-hda-intel power_save=10 power_save_controller=N

by adding # so it becomes:

# options snd-hda-intel power_save=10 power_save_controller=N

Reboot.

Hope this helps! It worked for me.

---

### Post by abhiroopb on 2009-12-03
Do you mind explaining what this does exactly? Thanks

---

### Post by smerral on 2009-12-03
Fair point - it's to do with the power save feature creating speaker feedback, but that's about all I know. Someone else posted it somewhere on these forums. As I say it worked for me. If it doesn't work it's easy to go back and re-edit.

---

### Post by abhiroopb on 2009-12-03
Thanks, I looked up a few bug postings and found it. Just generally easier to know what something will do before doing it.

This seems to solve the random popping that my speakers emit (I guess because of the power save).

---

