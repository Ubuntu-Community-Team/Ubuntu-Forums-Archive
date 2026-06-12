---
title: "Acer Aspire One d255E-1802 Sound Issues"
date: 2011-01-24
forum: Hardware
---

### Post by besneatte on 2011-01-24
I recently purchased the dual core netbook, acer aod255E-1802. Other than sound, it works flawlessly.

The sound card is an intel HDA, Realtek alc272x.

Headphone out works fine, but built in speakers only play left channel.

In order for the microphone to work, the PCM balance slider has to be all the way to the left.

I tried reloading alsa with all the different models available for the alc272x. The auto configure seems to work the best, but nothing solves the above problems. In alsa-base.conf:

options snd-hda-intel model=auto 

I have tried adding position_fix=1 but that doesn't seem to help. Perhaps it is related to this bug?

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/653266](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/653266)

I tried compiling drivers from source, and when I finally got a set that did compile ( the most recent snapshot from alsa ), installing it completely broke my sound and I ended up reinstalling Ubuntu. 

Does anyone have any suggestions? The option model=acer isn't available for the 272 chip ( see bug link for available models ). Perhaps there is a way I can create my own mapping using an existing one as a guide?

---

### Post by kettlekorn99 on 2011-03-12
BUMP, same exact problem, same model.

---

### Post by thevan on 2011-03-20
My model is basically the same (D255E, but -13405, could be a Canadian thing).

My sound works fine but my mic produces very weak and static-filled sound, and is very difficult to make out. 

Running Ubuntu 10.10 with all the updates. Huge noob on the Linux-scene but I wanted to try it as Windows 7 Starter is really ******* lame.

I have tried the instructions listed [here]("https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne%2FAOD250#Option%20Two%20-%20Update/install%20alsa-driver"), but after entering "./configure --with-cards=all" I get the following error:

"The file /lib/modules/2.6.35-28-generic/build/include/linux/autoconf.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel"

Please let me know if there is a solution for this. Works great otherwise but if my internal mic isn't working then I'm going to have to go back to Windows. Voice calls are important...

Thanks!

---

### Post by thevan on 2011-03-21
Hmm, well I feel silly now. Installed pavucontrol and lowered the mic volume to the "base" line and the background noise is gone. Fairly quiet but it seems okay. Going to try and make a call now...

EDIT: Still doesn't work in Gmail. No sound at all :(

---

### Post by halibaitor on 2011-03-27
> **besneatte said:**
> I recently purchased the dual core netbook, acer aod255E-1802. Other than sound, it works flawlessly.

The sound card is an intel HDA, Realtek alc272x.

Headphone out works fine, but built in speakers only play left channel.


I don't think anything is wrong with the computer.  Acer only claims MONO for the speakers on this unit, NOT stereo...  Examine the specs carefully.  

Do you have any problems connecting with WIFI?  I am thinking seriously about purchasing this machine.

---

### Post by petrosy on 2011-03-31
I have just bought one of these...and at the price point for dualcore atom. I am extremely pleased. 

Running EASYPEASY linux which works well I too have the mic issue but I will sort it out with help of the forum.

If you are goign to upgrade ram or HDD yourself make sure to watch the YOUTUBE vid on howto. It can be tricky and you could end up damaging your device

---

### Post by besneatte on 2011-04-30
> **halibaitor said:**
> I don't think anything is wrong with the computer.  Acer only claims MONO for the speakers on this unit, NOT stereo...  Examine the specs carefully.  

Do you have any problems connecting with WIFI?  I am thinking seriously about purchasing this machine.

I bet you are right about the MONO thing... the headphone jack works fine...

WIFI works great out of the box. LOVE this computer, couldn't recommend it more.

---

### Post by urbandryad on 2011-05-22
How do I set my audio to only output mono then instead of just teh left channel? o.o

---

