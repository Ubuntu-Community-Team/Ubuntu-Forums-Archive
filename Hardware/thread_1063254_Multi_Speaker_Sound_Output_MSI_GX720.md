---
title: "Multi Speaker Sound Output MSI GX720"
date: 2009-02-07
forum: Hardware
---

### Post by pYrO1v1aniac on 2009-02-07
This is a brilliant Ubuntu machine, but its 4 speaker + subwoofer speaker set seems to clash with both Ubuntu (8.10) and vista.

At first, both OS played everything through the subwoofer, which gives a dull booming sound, and with configuration I got vista to play through the front two speakers. 

Does anybody know how to configure Ubuntu to play through all 4 speakers+subwoofer? I've never heard the beastly sound from this thing and I know it can be done, I just need some help. 

Thanks :D

---

### Post by kostkon on 2009-02-07
Here is [the guide]("http://ubuntuforums.org/showthread.php?t=795525"). Check which way applies to you, I think the hard way, unfortunately, since you have 4.1?

---

### Post by pYrO1v1aniac on 2009-02-07
Thank you! I'll see how it goes!

---

### Post by pYrO1v1aniac on 2009-02-07
No, gedit on any of the files recommended there brings up blank files.

But it does sound like I need a surround config for these 4.1 speakers

---

### Post by kostkon on 2009-02-07
> **pYrO1v1aniac said:**
> No, gedit on any of the files recommended there brings up blank files.
Strange, it seems like you forgot to copy the *PulseAudio* config files to your *.pulse* folder, i.e. do the following in a terminal:
```
cp /etc/pulse/daemon.conf /etc/pulse/default.pa -t ~/.pulse/
```

---

### Post by RazTaz on 2011-02-26
Guys, I also have this notebook and I had the same problem with the sound. I mean, the sound worked OK in Karmic, Lucid and Maverick but there was no surround sound, and the guide suggested above did not help me.

What fixed the problem was this post by bchurchill [here]("http://ubuntuforums.org/showpost.php?p=7804772&postcount=13"):

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

then add the following lines at the end of the file:
```

options snd-hda-intel model=targa-dig
options snd slots=snd-hda-intel
# u1Nb.u_BNWJ+LvyF:82801I (ICH9 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel

```

Reboot.

I hope this helps.

---

