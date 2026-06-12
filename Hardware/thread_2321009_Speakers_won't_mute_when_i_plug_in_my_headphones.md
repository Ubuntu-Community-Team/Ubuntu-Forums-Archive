---
title: "Speakers won't mute when i plug in my headphones"
date: 2016-04-19
forum: Hardware
---

### Post by michael360 on 2016-04-19
Hello,
I'm having a rough time trying to make the speakers of my ASUS F555U to mute when i plug in my headphones. I've searched in the forums, and everything i've tried, failed. I've tried to fix the problem from the alsamixer menu, i've also donwloaded the gnome-alsamixer, but that didn't work either. I've also found some commands to put in the terminal, but they didn't work. The commands i've tried where the ones found here: [http://askubuntu.com/questions/132440/headphone-jack-not-working](http://askubuntu.com/questions/132440/headphone-jack-not-working) ; [http://askubuntu.com/questions/518851/headphones-not-working-after-update-ubuntu-14-04-1](http://askubuntu.com/questions/518851/headphones-not-working-after-update-ubuntu-14-04-1) .
My ASUS has Ubuntu 15.10 .
I'd really appreciate if someone could help me. Thanks

---

### Post by Yellow Pasque on 2016-04-19
> The commands i've tried where the ones found here
You should undo that (by deleting the lines you added to /etc/modprobe.d/alsa-base.conf).

Once you have removed the lines, reboot and get more information:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

