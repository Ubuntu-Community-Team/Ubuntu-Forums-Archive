---
title: "Can't use my headphones on Ubuntu."
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by mva.led on 2006-12-19
Hi all,

I have found that plugging my headphones into the laptop while running Ubuntu does not work as I expect. The sound keeps going through the laptop speakers.  I try it with Windows XP and it does right. 

So I figure my chipset needs to be instructed to send the sound output to the desired device.

The laptop is a HP Pavilion dv2025nr.

Best regards,
Manuel.

---

### Post by jimbren on 2006-12-19
I use Kubuntu, so the volume control applet is different, but they may work in a similar way.  If you double click on the icon, you get a "mixer" like view with volume controls for multiple outputs.  

I've noticed that I can control different outputs independantly of the main volume control.  Does that make sense?

Let me give an example. With the main volume muted, I can still use my headphones because their volume control can be made separate from the main. 

Gnome might be similar.

Could be something as simple as your headphone volume being muted or something.

your milage may vary.

And I hope I didn't talk about what you consider obvious.  I wasn't meaning to insult.

jimbo

---

### Post by olavjunior on 2007-02-14
Having the same problem here!

It's not a sound-control thing as mentioned above. There's no sound on the headphones or the spdif. 

I have a hp pavilion dv2130. I guess it's because of lacking drivers for the sound card?

It's so sad, cause everything else worked right out of the box, screen, quick play, wifi ect...
And now I cannot use linux cause of the soundcard! That would be ashame. Seems I'm never gonna get to know linux.... :(

Or can anyone help?

---

### Post by Andre_44 on 2007-03-04
I have the HP Pavilion dv8320.  Different laptop, but the solution is probably the same.
(in fact, my headphones work fine, my problem was extremely low volume)  the fix however... is updating alsa and specifying the correct model for your card.
Edgy currently uses alsa 1.0.12rc1
I tried the latest stable version of alsa which is 1.0.13 and that still didn't work for me, (but may work for you) I had to install 1.0.14rc2
regardless of the alsa version. the instructions are the same.
**download alsa & extract**
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.13.tar.bz2
wget ftp://ftp.alsa-project.org/pub/driver/alsa-lib-1.0.13.tar.bz2
wget ftp://ftp.alsa-project.org/pub/driver/alsa-utils-1.0.13.tar.bz2
wget ftp://ftp.alsa-project.org/pub/driver/alsa-tools-1.0.13.tar.bz2
tar xvjf alsa-*
```
Note: I installed all four of these packages, they may not all be necessary. YMMV

**compile alsa-drivers**
```
cd alsa-driver-1.0.13
./configure --with-cards=hda-intel --with-oss=yes \
  --with-sequencer=yes --with-kernel=/lib/modules/`uname -r`/build \
  --with-debug=full
make && sudo make modules-install && sudo depmod -e

```

**specify the model as an option to snd-hda-intel**
add the following line in /etc/modprobe.d/alsa-base
```

options snd-hda-intel model=hp

```

**Installing the other packages**
change into each of the other alsa directories and install them using:
```

./configure
make && sudo make install

```

**reboot**
Sound should be working fine on your next reboot.

---

