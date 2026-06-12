---
title: "Bluetooth Headset"
date: 2008-04-25
forum: Hardware
---

### Post by gattopi on 2008-04-25
Hi,
Ho to use HeadSet Bluetooth in Ubuntu Hardy 8.04 and Skype?

The HeadSet is see by Blueetooth but not Audio profile

Thanks for Help me.

---

### Post by gattopi on 2008-04-26
up

---

### Post by Permafrost91 on 2008-04-26
Having the same problem ... from what I can gather, the btsco module has become obsolete. Pretty much everyone seems to be having problems with bluetooth headsets in Hardy and no one has the answer on how to get it fixed. I can connect my headset, but there's no sound going in or out of it. Maybe the problem is with PulseAudio and not gnome-bluetooth?

---

### Post by oscar on 2008-04-26
What got mine working was simply:
[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

You shouldn't need gnome-bluetooth, btsco, bluetooth-alsa or anything extra but I like having Blueman to manage connecting my headset:
[https://launchpad.net/blueman](https://launchpad.net/blueman)

---

### Post by gattopi on 2008-04-27
Thanks,
	
I have successfully connected the headset but with skype not working. How do?

---

### Post by phreakaholic on 2008-04-27
yeah, now mine works well too, thanks to oscar :)

---

### Post by derailed1 on 2008-04-27
Hi guys,

I don't understand

"modify your ~/.asoundrc to contain"

Where do I find asoundrc.  Is it a file I have to configure or am I totally lost?

Thanks in advance

---

### Post by Gizmonty on 2008-04-27
I'm also having trouble following the instructions on that page.

I had an audio.service file as it said I should. I didn't have a .asoundrc in my home directory though so I created one and added the lines then...

Nothing.

Can anyone explain the steps I need to follow in nicely dumbed down language?

Hardy Heron has impressed me enormously otherwise. If I can get this working, I'll be a 100% convert (although it should be a lot easier).

---

### Post by psyke777 on 2008-05-08
[http://ubuntuforums.org/showthread.php?p=4910397](http://ubuntuforums.org/showthread.php?p=4910397)

---

### Post by Permafrost91 on 2008-05-09
well, I followed the instructions and I even got the arecord/aplay step to work beautifully but Ekiga still can't use my headset! It recognizes it but then complains that it can't read/write to the device. Any ideas? Anyone else having this problem?

---

### Post by Gizmonty on 2008-05-12
psyke777's solution works! Thanks.

---

