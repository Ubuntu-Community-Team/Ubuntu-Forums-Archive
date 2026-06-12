---
title: "Sound issues, no sound at all"
date: 2009-07-05
forum: Hardware
---

### Post by Essar Allen on 2009-07-05
I'm just doing as I'm told.
> 
"This is X-file... Post a thread at laptop and hardware section and mention that we did
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
and added
```
options snd-hda-intel model=hp
```
at the end of file. I just don't get it. This thing worked for me."

Can anyone help me? I've got another guy with what seems to be the same problem, so if you could help us out that would be awesome.

Thanks in advance.

By the way, I don't know about the other guy but I'm running 9.04 Jaunty on an HP tx2000

---

### Post by Favux on 2009-07-06
Hi Essar Allen,

That line should work.  Have you checked your mixer and made sure all your sliders are up including PCM?

You could try adding "position_fix=1" to the line.  Making it:
```
options snd-hda-intel model=hp position_fix=1
```
You are restarting after modifying alsa-base.conf, correct?

Another thought, highly unlikely is to try:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
instead of:
```
sudo gedit /etc/modprobe.d/alsa-base.conf 
```
when adding the original line.  gksudo is for graphical programs like gedit.  Occasionally using sudo can mess up permissions.

---

### Post by Essar Allen on 2009-07-06
I notice the code is
```
options snd-hda-intel model=hp
```

But what if my device shows up as HDA ATI SB instead of HDA INTEL?

should I edit it to be 
```
options snd-hda-ati model=hp
```?
Or would that just mess everything up?

---

### Post by Favux on 2009-07-06
Hi Essar Allen,

You'd think it would be something logical like that wouldn't you?  But it isn't.  So don't do that, it will mess things up.

You can go read the alsa.org stuff and the alsa wiki.  Then look in your files for "/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz".  Unpack it to ALSA-Configuration.txt.  What you find is for each sound chip there may be one to like 6 or more lines.  You're suppose to try them one by one.  This is all very tedious.  So when you find one that works you share it!

Intel HDA is pretty common.  Your northbridge chip can masquerade as the soundchip.  So to find out:
```
aplay -l
```

Edit:  A user "snd_hda_intel options database" by markbuntu is here:  [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

