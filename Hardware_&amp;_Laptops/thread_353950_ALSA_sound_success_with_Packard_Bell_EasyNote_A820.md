---
title: "ALSA sound success with Packard Bell EasyNote A8202"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by mflint on 2007-02-05
All,

(Note: this is not my work, but the details of the solution are scattered through [_this ALSA bugreport_](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1134) - so I thought I'd write them up here, in the hope that other people's googling won't be as frustrating as mine was for months...!)

**Problem**
No sound on Packard Bell EasyNote A8202 - and possibly other Packard Bell EasyNote models, and some BenQ laptops

**Quick solution**
Download ALSA driver from [[ALSA website](ALSA website)](http://www.alsa-project.org/). I used version 1.0.14-rc2.

Extract and configure with:
```

./configure --with-cards=intel8x0 --with-debug=full
```

Build and install ("make", "sudo make install")

Remove all sound modules with "rmmod", then
```

modprobe snd-intel8x0
```

Finally, hack register 5c:
```

echo 5c 0001 > '/proc/asound/card0/codec97#0/ac97#0-0+regs'
```

and use alsamixer to set the sound levels

**Proper solution**
Download and extract alsa-drivers as before. Apply these patches:

```

alsa-driver/alsa-kernel/pci/ac97/ac97_codec.c

 { 0x43525970, 0xfffffff8, "CS4202", NULL, NULL },
 { 0x43585421, 0xffffffff, "HSD11246", NULL, NULL }, // SmartMC II
 { 0x43585428, 0xfffffff8, "Cx20468", patch_conexant, NULL }, // SmartAMC fixme: the mask might be different
+{ 0x43585431, 0xffffffff, "Cx20551", patch_cx20551, NULL },
 { 0x44543031, 0xfffffff0, "DT0398", NULL, NULL },
 { 0x454d4328, 0xffffffff, "EM28028", NULL, NULL }, // same as TR28028?


alsa-driver/alsa-kernel/pci/ac97/ac97_patch.c

+int patch_cx20551(struct snd_ac97 * ac97)
+{
+ snd_ac97_write_cache(ac97, 0x5c, snd_ac97_read(ac97, 0x5c) | 0x01 );
+ return 0;
+}

 /*
  * Analog Device AD18xx, AD19xx codecs
  */


alsa-driver/alsa-kernel/pci/ac97/ac97_patch.h

int patch_cirrus_spdif(struct snd_ac97 * ac97);
int patch_conexant(struct snd_ac97 * ac97);
+int patch_cx20551(struct snd_ac97 * ac97);
int patch_ad1819(struct snd_ac97 * ac97);
```

rmmod and modprobe as above, and set volume levels with alsamixer.

Oh happy days! Huge thanks to the ALSA crew and everyone in [_this thread_](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1134) who hacked the Conexant card into submission! :cool:

Matthew

---

### Post by jam'ez on 2007-02-10
Finally :) Sadly my PB A8 broke and got sent back for repair, never got it back and had a replacement! So never got sound on the old girl :( - Got a Philips X56 now, had linux problems with it (networking) but seems to be going ok now after guidence of Ubuntuforums! :)

---

### Post by pompeyjohn on 2007-03-02
Hi there,

Could you please clarify how to ...

> Remove all sound modules with "rmmod"


Thanks

---

### Post by pompeyjohn on 2007-03-03
SOMEBODY PLEASE HELP HERE!!!!!!!

I have followed the steps above, but I am running into problems at the removing the sound modules stage.

First of all I am not sure what command to use,... I have googled around and found this...

cat /proc/modules|gawk '/^snd-/{print $1}'|xargs -i rmmod {}

... which I think is removing all the sounds modules succesfully.

When trying to modprobe snd-intel8x0 I am getting this error

```
WARNING: Error inserting ac97_bus (/lib/modules/2.6.17-11-generic/kernel/sound/misc/ac97_bus.ko): Invalid module format
```

I have googled for an answer to this for ages and the only two forums that have a hit on the terms are in Polish and what looks like Russian. Regrettably, I speak neither.

Someone please help!

What is really driving me crazy is late last night I had this working on this same laptop. Overjoyed that I could finally used linux with sound I reinstalled Ubuntu this morning and completely wiped M$ off the machine.

I am absolutely desperate for help with this, and if someone can help soon I am more than happy to paypal them a couple of beers.

thanks in advance

---

### Post by joey-morolto on 2007-03-04
Hi pompeyjohn !

first of all sorry for my english... :(

i have an Asus with the same sound card and the same problem!

if you have gnome, go to 
 system-administration-user+groups. 
now you deactivate the permission of your account to start the audio device.
(i have the german version and i hope in english its the same...) 

After that -->restart

now do the same wich is describted above....

now you can stop the module with "rmmod snd-intel8x0"

after that type "modprobe snd-intel8x0"

now i'm not sure... maybe this command works

echo 5c 0001 > '/proc/asound/card0/codec97#0/ac97#0-0+regs'

or this (this is the one for asus)

echo "7a 57c1" > /proc/asound/card0/codec97#0/ac97#0-0+regs

ok...
you can put this script from the website [http://www.lrz-muenchen.de/~tobiasnadler/linux/speakers](http://www.lrz-muenchen.de/~tobiasnadler/linux/speakers) to /etc/init.d/speakers in a new file (it must be "executable"... right click on the file and properties....)


and type this into the terminal:

cd /etc/rc2.d
sudo ln -s ../init.d/speakers S26speakers

---> restart

i hope you understood this... sorry for my english :neutral: 

greetings,

joey

---

### Post by mflint on 2007-04-18
For the avoidance of doubt, this issue has been fixed in Alsa drivers version 1.0.14rc3 . So no patching needed any more.

Matthew

---

