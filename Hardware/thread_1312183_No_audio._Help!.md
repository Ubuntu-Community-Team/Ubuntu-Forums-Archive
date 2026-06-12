---
title: "No audio. Help!"
date: 2009-11-02
forum: Hardware
---

### Post by Nandus1 on 2009-11-02
Hello all,
I installed 9.10 (64 bit) via Wubi recently. For some reason, I have no sound.

It appears that the driver for the sound card was installed since it is being detected as an "HDA Intel Sound Card". 
Note: This is a Realtek based chip on the card (intergrated).
The card is a: 7.1 channel Audio with Realtek ALC883 (HDA)

I have checked the Sound Preferences and selected all options under the "Hardware" tab, but am still not getting any sound.

The hardware works fine under both Win XP and Win 7.

I did notice that the "ALSA" option is not located in the Sound Preferences as in previous versions of Ubuntu (8.10 and 9.04) on the same hardware.

If I need to install the ALSA driver, how would I go about doing that?

---

### Post by klemes on 2009-11-03
Edit '/etc/modprobe.d/alsa-base.conf' and add this line:

```
options snd-hda-intel model=auto
```

and then give 'asoundconf set-default-card Intel' ,

and finally do a 'sudo alsa force-reload ' in the console as root,
and you are done with!

:popcorn:

---

### Post by Nandus1 on 2009-11-03
Thanks for the reply klemes. I went to edit the file and received a "You do not have permission to edit this file" message.

Guess I needed to do it as root.

But, for some strange reason, when I received the message, I heard a familiar Ubuntu sound.  I now have audio and I don't know why.

I did perform an "sudo alsa force-reload" before trying to edit the file, so that may be why I have sound.

I rebooted and the sound was muted. Upon un-muting, I had sound again.
I guess the issue is resolved for now.

Thanks again for the reply.

BTW, how can I mark this thread as "solved"?

---

