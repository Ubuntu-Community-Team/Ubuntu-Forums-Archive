---
title: "microphone problems"
date: 2010-05-08
forum: Hardware
---

### Post by james1415 on 2010-05-08
I have had problems with the microphone not working (the speakers are ok) since I replaced Vista with  Karmic Koala a couple of months ago. I had hoped upgrading to the new release might solve the problem but it has made no difference.

I have a Dell XPS 1530 laptop with integrated Intel sound card and SigmaTel STAC9228 codec (according to ALSA-info) - more details from ALSA-info can be found at
[http://www.alsa-project.org/db/?f=910309d18466fdf0424ff0ff06f620587fde9960](http://www.alsa-project.org/db/?f=910309d18466fdf0424ff0ff06f620587fde9960)
I have tried various suggestions of adding a last line to /etc/modprobe.d/alsa-base.conf like
```
options snd-hda-intel model=dell
```
with various model names, such as auto, and dell-m22 and others I've found in the forum but to no avail. (Having to reboot each time makes it a bit of a pain).

Thanks for any suggestions.

James

ps I notice that for the ALSA drive version 1.0.21 I'm running there is no entry relating to STAC (looking at the file
[http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=bf24429b7a8f22711ac7a4b9ccce4ad26b50b8bd;hb=1cdf06bcd91e0c180efbc43f03ce0a1cf68ae8ec](http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=bf24429b7a8f22711ac7a4b9ccce4ad26b50b8bd;hb=1cdf06bcd91e0c180efbc43f03ce0a1cf68ae8ec)
on alsa's website).  Could that be a problem?   I have found (in the forum) that some versions of alsa do contain mention of STAC.

---

### Post by lidex on 2010-05-09
On those alsa-base.conf options - you want to try one at a time and remove it if it doesn't work. I see the dell option in your alsa-info text. Please remove it.

Your alsa drivers are mismatched:
```
!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


```

I would suggest an upgrade to iron that out. Use the alsa-upgrade-script link in my sig.

---

### Post by james1415 on 2010-05-09
That's great - thanks.  I followed the upgrade script (heart in mouth as  I didn't do the recommended backup), so I have version 1.0.22.1  installed, and the builtin mic now works.

However, the front microphone jack still doesn't work (though the speakers are ok). Am I missing a setting somewhere? If I open alsamixer in a terminal, and press F4 for capture, I get 3 controls labelled Capture, 1 labelled Digital, then 3 slots labelled Input Source  but with no volume control, then 3 controls labelled Mux,  (what's Mux mean?).  The volume controls are all set to high.

James

---

### Post by lidex on 2010-05-11
The slots labelled input source can be toggled. Just highlight and use up/down arrow keys. My options are line/front mic/mic. You may want to use gnome-alsamixer also, sometimes it's easier.

---

### Post by james1415 on 2010-05-12
Yeh - I found that.  Mine are Digital, Front Mic and Mic, and I have one set on each - but there are no volume controls on them.

And now somehow the internal mic works, but I don't think I changed anything. (I installed padevchooser to set Skype to use my USB headset, but that's all.)

Thanks for your help

    James

---

### Post by lidex on 2010-05-12
> **james1415 said:**
> Yeh - I found that.  Mine are Digital, Front Mic and Mic, and I have one set on each - but there are no volume controls on them.

And now somehow the internal mic works, but I don't think I changed anything. (I installed padevchooser to set Skype to use my USB headset, but that's all.)

Thanks for your help

    James

Not a kde user, but isn't there a program called kmix? I would look into that.

---

