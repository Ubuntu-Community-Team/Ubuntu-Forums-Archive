---
title: "Sound card issue. Advent 8555gx."
date: 2011-07-22
forum: Hardware
---

### Post by Pyraine on 2011-07-22
Hello, 

I have installed the last 3 versions of Ubuntu on this laptop and with all, the same problem has persisted throughout all versions.

The problem is the laptop has both stereo speakers and a sub woofer. However while running Ubuntu, audio only comes out of the sub woofer. I can't really get the speakers working in Windows, but while on there, I can go into the audio settings and can choose either the sub woofer or the stereo speaker.. I can't get them running alongside each other, but I don't mind only have the mids and highs. 

I have checked the sound preferences in Ubuntu and all the options seem to either mute the audio or restrict it to sub woofer. Music and video really isn't all that fun when you can only hear the bass frequencies.

I have trawled google for a solution to this problem, nobody seems to have the same problem though and all the similar problems yield no results where they have found solutions. I have installed and uninstalled countless audio libraries and software, to the extent I have had to reformat to clear the mess.

Headphones work fine. So it's not a case of the soundcard simply not registering the highs and mids.

I'm not proficient enough to find out the make and model of my soundcard, but the laptop I am using is, as the title states an Advent 8555gx.

If anyone could help me get the stereo speakers working you would be superhuman and I would be eternally grateful, however if you could help me get the sub woofer and stereo speakers working in canon you would be a deity and I would worship you forever.

Thanks in advance

---

### Post by Pyraine on 2011-07-23
Oh, I forgot to mention, I am currently running 11.04 x64 and this problem has always been on 64-bit releases.

---

### Post by Pyraine on 2011-07-24
I'm not entirely sure what the etiquette on bumping posts is on this forum, but I'm becoming desperate. I believe I have thoroughly examined the entire internet and there seems to be nobody with a similar problem, no solutions anywhere.

---

### Post by Pyraine on 2011-07-25
Managed to find a pseudo solution. For the sake of google I will paste the solution here:

In terminal:

```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Paste these lines at the bottom of the file:

```
options snd-hda-intel model=targa-dig
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel probe_mask=1 
```

Save the file and reboot. 

I lost my sub woofer doing this, but like I said in my first post I don't get the sub woofer on Windows either and I imagine this is probably as close a solution there is and I will not press it further!

Good luck!

---

