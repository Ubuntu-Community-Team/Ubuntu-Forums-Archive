---
title: "Problem with ALC883"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by [Po]lentino on 2007-08-16
Hello guys,
I'm in trouble with my Realtek ALC 883 high definition audio card. It doesn't work, all the speakers are mute and i don't know how to solve this.
Before telling me *"N00b, read other topics before creating an other one "*, i want to notice i have already read this topic
---> [http://ubuntuforums.org/showthread.php?t=202555&page=1&highlight=snd-hda-intel]("http://ubuntuforums.org/showthread.php?t=202555&page=1&highlight=snd-hda-intel")

And i made all ti was described, without results :(

I think this could be the difference :
the patch has been created for ACER laptop, but mine is an Enface.
I don't know their effective difference, however this is my laptop homepage [www.enface.it]("www.enface.it")

Someone has any idea ?
Thanks :)

---

### Post by eggdeng on 2007-08-16
The solution to this problem is often as simple as adding a line at the end of /etc/modprobe.d/alsa-base along the lines of
```
options snd-hda-intel model=xyz
```
The problem here is that xyz is different for different makes of laptop. For HP laptops, you (usually) need to put 'hp' (no quotes), my LG laptop requires 'lg' (no quotes), other options I have seen are 'asus', 'w180', 'uniwill' (again, no quotes).
You can find one list of possible options in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz. Gunzip it, open with gedit and search for your soundcard chip.
Sample entry from ALSA-Configuration.txt:

```
ALC260
hp HP machines
fujitsu Fujitsu S7020
```

This tells you that if you have an ALC260 chip on a HP laptop, the appropriate value is 'hp'. And so on and so forth.
See thread at [http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

---

### Post by [Po]lentino on 2007-09-08
Sorry eggdeng, but I TRIED EVERYTHING :(
Please help me, this is the last obstacle i have on migrating from win to linux ...

---

### Post by eggdeng on 2007-09-08
Sorry, I don't have any magic bullets - it's always hard to find fixes for the lesser-known vendors. One workaround would be to get a set of usb speakers. I used to have a C-media set which worked OK & I'm sure if you shop around a bit, you'll be able to find something that works for you.

---

### Post by [Po]lentino on 2007-10-02
> **eggdeng said:**
> Sorry, I don't have any magic bullets - it's always hard to find fixes for the lesser-known vendors. One workaround would be to get a set of usb speakers. I used to have a C-media set which worked OK & I'm sure if you shop around a bit, you'll be able to find something that works for you.

WHAT ?
Some days ago i have installed Gutsy, but the problem isn`t still fixed ....
Any other suggestion ?

---

### Post by [Po]lentino on 2008-02-08
SO, this is my situation now:

I have added this line in the */etc/modprobe.d/alsa-base* config file:
```

options snd-hda-intel index=0 position_fix=1 single_cmd=1 model=laptop-eapd

```

By doing this, I can hear sound from the *Front* jack, placed in the rear of my notebook.

If I remove the headphones, i can't listen anything from my front speaker; the same, if i put the headphones in their correct jack.

So, i think that alsa driver is a bit confused about where direct the output audio stream, because it place the stream in the jack designed for the dolby surround (Front,Center,Surround), instead of the Speakers or the headphones jack.

How coul I proceed ???

---

