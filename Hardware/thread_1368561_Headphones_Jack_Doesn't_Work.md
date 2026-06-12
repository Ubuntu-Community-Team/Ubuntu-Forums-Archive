---
title: "Headphones Jack Doesn't Work"
date: 2009-12-30
forum: Hardware
---

### Post by guitarhero183 on 2009-12-30
I have installed Ubuntu 9.1 onto an HP G61-322NR notebook and everything works except for the headphones jack. When I plugged headphones in, the speakers keep playing and no sound comes out of the headphones. I have already searched for an answer and found nothing.

---

### Post by manco on 2009-12-30
Just to confirm, the speakers do work with or without the headphones plugged in?  If so, your sound card is good but Ubuntu isn't recognizing your headphone jack.

---

### Post by guitarhero183 on 2009-12-30
The laptop speakers work. When I plug headphones into the jack though the speakers keep playing and nothing comes out of the headphones.

---

### Post by manco on 2009-12-30
Well, at least your sound card isn't the problem.

I'd try poking around "Sound".  Right-click the sound icon in the upper-right corner of the Ubuntu desktop, select "Sound Preferences"

I think one of the settings under "Output" has something like "stereo output with stereo input".  Something like that.

---

### Post by guitarhero183 on 2009-12-30
I have already tried changing all the settings in Sound Preferences but nothing worked. I have also tried changing the output to Analog Headphones but the speakers went off and nothing came out of the headphones.

---

### Post by manco on 2009-12-30
I just Googled "ubuntu laptop headphone jack" and found this post:

[[SOLVED] Laptop headphone detection in Karmic solution]("http://ubuntuforums.org/showthread.php?t=1319424")

Hopefully that will help

---

### Post by guitarhero183 on 2009-12-31
After a few computer restarts the headphones jack works now. Not sure what the problem was but now it is fixed so it doesn't really matter. Thanks anyway.

---

### Post by Nerdfest on 2010-08-21
I had a similar problem and neither of these solutions worked. What did was adding options "snd-hda-intel model=hp-m4 enable_msi=1"[COLOR=Purple][SIZE=6][COLOR=Black][SIZE=2] to "/etc/modprobe.d/alsa-base.conf". 
[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by king james II on 2010-08-24
> **Nerdfest said:**
> I had a similar problem and neither of these solutions worked. What did was adding options "snd-hda-intel model=hp-m4 enable_msi=1"[COLOR=Purple][SIZE=6][COLOR=Black][SIZE=2] to "/etc/modprobe.d/alsa-base.conf". 
[/SIZE][/COLOR][/SIZE][/COLOR]

Hey I have the same problem on a Toshiba satellite. I am brand new to linux and really need a headphone jack. What do you mean by adding options? thanks!

---

### Post by lidex on 2010-08-26
> **king james II said:**
> Hey I have the same problem on a Toshiba satellite. I am brand new to linux and really need a headphone jack. What do you mean by adding options? thanks!
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

