---
title: "HP DV6-2113sa and Skype problem"
date: 2011-04-16
forum: Hardware
---

### Post by foxy123 on 2011-04-16
I have been suffering from an annoying Skype problem on my laptop since I bought it a year ago. The problem involves a few issues:

1. If someone calls me or I call someone, the counterpart cannot hear me. If I make a Skype Test Call first, and then make/receive a call they can hear me OK.

2. As soon as I start video, the other side can see me but not hear.

3. It is impossible to stop Skype after making calls. I have to use 

```
kill -9 XXXX
``` to kill Skype.

Everything works fine on a Dell laptop.

---

### Post by foxy123 on 2011-04-20
OK, I have muted the left channel of the mike (it is configured as stereo for some weird reason) and I can now use the camera while talking. However the quality is still low. When I make a call the sound is garbled and I have to call back.

---

### Post by foxy123 on 2011-04-22
Well, I have removed pulseaudio following [this guide]("http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html") and it seems to fix the problem. Looks like pulseaudio does not play well with this particular laptop. BTW, there are other ways to remove/disable pulseaudio, which can be found on this forum.

---

### Post by dajhorn on 2011-04-26
This works for me. Thanks.

Since upgrading to Natty, Skype randomly hangs and its icon would sometimes disappear from the tray.

Skype becomes reliable on Ubuntu Natty after replacing PulseAudio with Dave Lentz's PPA.

---

### Post by lidex on 2011-04-27
You can actually turn it on and off:
[http://www.linuxplanet.com/linuxplanet/tutorials/7130/2/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/2/)
I hear 2.1 may work better than 2.2(Skype):
[http://ubuntuforums.org/showthread.php?p=10719241#post10719241](http://ubuntuforums.org/showthread.php?p=10719241#post10719241)

---

### Post by foxy123 on 2011-04-28
> **lidex said:**
> You can actually turn it on and off:
[http://www.linuxplanet.com/linuxplanet/tutorials/7130/2/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/2/)
I hear 2.1 may work better than 2.2(Skype):
[http://ubuntuforums.org/showthread.php?p=10719241#post10719241](http://ubuntuforums.org/showthread.php?p=10719241#post10719241)

Thanks a lot for the link. I just do not see any point to have Pulseaudio. Probably I am missing something.

---

### Post by foxy123 on 2011-05-02
OK, now I have a problem, I believe is related to the removal of the pulseaudio. If I switch between user accounts sound stops working. QuodLibet gives me the following error:
```
GStreamer output pipeline could not be initialized. The pipeline might be invalid, or the device may be in use. Check the player preferences.
```
I tried banshee and it crashes:

```
[Error 17:14:58.342] GStreamer core error: StateChange
[Error 17:15:00.007] GStreamer core error: StateChange
[Error 17:15:01.364] GStreamer core error: StateChange
[Error 17:15:02.744] GStreamer core error: StateChange
[Error 17:15:04.150] GStreamer core error: StateChange

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
at Banshee.GStreamer.PlayerEngine.OnAboutToFinish (intptr) <0x00012>
at (wrapper native-to-managed) Banshee.GStreamer.PlayerEngine.OnAboutToFinish (intptr) <0x0006f>

```

I wonder if there is a alternative for PulseAudio.

---

