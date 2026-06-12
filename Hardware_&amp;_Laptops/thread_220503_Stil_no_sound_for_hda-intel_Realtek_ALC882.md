---
title: "Stil no sound for hda-intel Realtek ALC882 ?"
date: 2006-07-21
forum: Hardware &amp; Laptops
---

### Post by didobuntu on 2006-07-21
Hi all,

Until now I cannot get sound on my Asus laptop. It is an intel/realtek chipset, ICH7 with ALC882.](*,) 

Someone succeded to make the sound run for this chipset? however noisy it is? At least it would be better than just a comletely muted laptop .. :mrgreen: 

Thanks

---

### Post by lodp on 2006-07-24
welcome to alsa hell.

i've got the alc883, and no sound as well. started this thread: [http://ubuntuforums.org/showthread.php?t=202555](http://ubuntuforums.org/showthread.php?t=202555) . i also filed a bugreport weeks ago at the alsa project, but there was no response. 

have you tried compiling the latest alsa package (1.0.12rc1)? is your microphone working (on my laptop, it's the only sound thingy that works).

---

### Post by Burkey on 2006-07-25
Do you guys get sound out the headphone jack if you plug in headphones?

I have a similar setup and the headphones work ok but no sound from the builtin speakers (laptop)

---

### Post by didobuntu on 2006-07-25
I don't have sound at all ... non on speakers nor on headphones. I tried many compinations with the different options via the gnome-volume-control. ](*,) 

I recompiled the last alsa 1.0.12rc1 and nothing.

When we see the specification of alsa since version 1.0.11, the chipsets ALC882/883/885 are taken into account, but only in theory. It seems that these hda-intel chipsets related to realtek are a bit more complicated than usual. Is it because they are too new? or there is some licencing problems ...

---

### Post by lodp on 2006-07-25
the alsa guys say they're on it. my bug report is here, if you're interested: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2261](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2261) (you'll have to register for access)

Burkey: i'm getting no sound at all, nothing from the jacks, and nothing from the internal speakers. only the mic jack and internal mic works. what chip (type 'cat /proc/asound/card0/codec#0' to find out) and what alsa version ('cat /proc/asound/version') are you using?

---

### Post by Burkey on 2006-07-27
Ahh, mine are:

Realtek ALC880

and

Alsa version 1.0.10rc3

Pretty much a clean install nothing touched on ALSA drivers from standard Dapper.  I get sound out the headphones but not the speakers, no matter what combination of muting/unmuting I do on the switches in alsamixer.

---

### Post by Stan83 on 2006-07-27
Same on my Acer :/
I guess all we can do is wait for next ALSA release, so patience (sound is just an unnecessary luxury :o , or isn't it?)

---

### Post by lodp on 2006-07-27
Burkey: have you tried the very latest alsa release candidate? as far as i know, ALC880 isn't supposed to be THAT much of a problem..

As for the next ALSA release .. i wouldn't bet my *** on it, but i certainly hope they'll fix it for us poor hda-intel - shmoes.

EDIT: whaddayknow, they've got word censors here..:)

---

### Post by pwaller on 2006-07-27
I'm on the ALC861 and I'm experiencing EXACTLY the same symptoms as described in this thread. Not tried a Mic though. Tried compiling all sorts of things, 

This patch looked promising but didn't seem to have any effect for me :(

Whether I did something wrong in the installation or what I don't know. :s

[http://article.gmane.org/gmane.linux.ubuntu.devel.kernel.general/478](http://article.gmane.org/gmane.linux.ubuntu.devel.kernel.general/478)

- Pete

---

### Post by Burkey on 2006-07-27
I have not tried alsa sources.  Does anyone know if I can get some easy deb's for the latest ALSA?

And if I upgrade do I need to recompile a newer kernel?  I thought the driver is part of the kernel.  If anyone knows a good guide would be handy

---

### Post by Stan83 on 2006-07-28
> **Burkey said:**
> I have not tried alsa sources.  Does anyone know if I can get some easy deb's for the latest ALSA?

You can try to install the package that goes with Edgy, I think it is a bit newer than accessible through repository (didn't help me, but well 1.0.12 isn't helping either).
just download the package and than run dpkg -i name_of_the_package to update what you have now, but it will not work most probably :neutral:

> **Burkey said:**
> And if I upgrade do I need to recompile a newer kernel? I thought the driver is part of the kernel. If anyone knows a good guide would be handy

I don't think you have to recompile the kernel, but most probably you will need kernel sources and headers.
Any way on ALSA page there is a description of how to compile the modules from source.
I hope it helps.

I have asked the manufacturer of my laptop what exactly is the sound hardware I have, and beside the standard response that they do not support Linux they told me that I have ALC260 with my intel chip set, so I am a bit confused since my ALSA mixer claims it is ALC883, and I think I have seen some post claiming the same as for my laptop. And I am not all the way sure how well the technical support 
is informed :] I tried to confirm it either way but there is just no info out there (at least I didn't find anything). So maybe some of you know what it really is, appreciate any help here.
My laptop is: AcerTM4072NLMi

---

### Post by pwaller on 2006-07-28
I just tried the Mic on my laptop and it works. (recorded a .wav and played it back on a different computer.).

Man, this is frustrating.

:(

---

### Post by lodp on 2006-07-28
for compiling the driver from alsa source, you have to do the following:

1. make sure you've got the build-essential and linux-headers packages installed.
2. download the latest alsa-driver package from alsa-project.org
3. unpack it into a directory
4. run ```
./configure --with-cards=hda-intel
sudo make
sudo make install
```

5. Then type
```
sudo modprobe snd-hda-intel
```
to load the driver. to get the driver loaded automatically on startup, add "snd-hda-intel" to /etc/modules

at least that's what i've been doing .. pls correct me if anything's wrong with the above..

Stan83: Alsa reportedly works with the ALC260 -- at least that's what this thread says (they apparently got it going during the course of it): [http://ubuntuforums.org/showthread.php?t=76019](http://ubuntuforums.org/showthread.php?t=76019)

if alsamixer says it's ALC883, it's probably the case..

---

### Post by Stan83 on 2006-07-29
> **lodp said:**
> Stan83: Alsa reportedly works with the ALC260 -- at least that's what this thread says (they apparently got it going during the course of it): [http://ubuntuforums.org/showthread.php?t=76019](http://ubuntuforums.org/showthread.php?t=76019)

if alsamixer says it's ALC883, it's probably the case..

Well, some time I followed this thread, but than what it said didn't work for me, additionally I thought I have a ALC883 (don't really know if there is any good specification of the hardware I have :/, Acer doesn't give it... ), the Acer support says there are two types of chips on my laptop, RealTek ALC833(ALC260), and adds that the one responsible for the sound is ALC260. It might be that the sound chip is recognized as ALC883, while it is not (I am no specialist here...), but I guess it would not work :smile:
Thank you for the reply.

> **lodp said:**
> for compiling the driver from alsa source, you have to do the following:

1. make sure you've got the build-essential and(...)  (...)anything's wrong with the above.. 

I would just add that it might be not a good idea to do make -install in point 4, since the new driver is not a stable version. Instead you may load the new modules (firstly unloading the old ones) this way you don't destroy what you have (even if it is not working :) )

---

### Post by lodp on 2006-07-31
so you just run make and load the modules? how do you unload modules before you load new ones, anyway?

as for the (possible) ALC260 chip -- did you try all the model options for that one? i think i tried "model=acer" once, but it didn't help.

---

### Post by Stan83 on 2006-07-31
> **lodp said:**
> so you just run make and load the modules? how do you unload modules before you load new ones, anyway?

I do this like that:
1. lsmod - note all the modules I wish to check (eg: lsmod | grep snd - find modules with snd in their name), and note them.
2. rmmod one by one, starting with the ones that are not used by anything (no other module is using them), I guess modprobe -r does the same, or even more :), man page should tell you. By the way you might have to turn of all programs  that may use any of the modules you are removing.
3. Now during compilation there should have been created a folder called modules, it is where the modules ware compiled to.
4. Now run modprobe <name_of_the_module.ko> in reverse order than you have them removed.
5.Run lsmod, and see if all is loaded.

I hope I am right in what I have written, as I have done it some time ago already. And I am not sure as to the way. So correct me If I am wrong :)

> **lodp said:**
> as for the (possible) ALC260 chip -- did you try all the model options for that one? i think i tried "model=acer" once, but it didn't help.

I have tried loading sound modules with some options, I don't know if I checked all...
Now I am thinking how to change to ALC260 chip, (does a loading option switches it?) so I can check if this is my problem. Do you know how to do this?

---

### Post by lodp on 2006-08-03
thanks for your instructions -- up til now i just did "modprobe snd-hda-intel" when i had compiled a new version.

as for the ALC260 chip -- check Alsa-Configuration.txt for the appropriate model options (i forget where that .txt file is located). i'm pretty sure it's "model=acer", but there might be other options.

i ran into a new problem when i tried to compile the latest alsa-lib from the hg repository. when i ran > ./hgcompile it says > libtool: link: `cards.lo' is not a valid libtool object
make[2]: *** [libcontrol.la] Error 1
make[2]: Leaving directory `/home/martin/Drivers/alsa-hg/alsa-lib/src/control'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/martin/Drivers/alsa-hg/alsa-lib/src'
make: *** [all-recursive] Error 1


./hgcompile works fine for alsa-driver.

i don't know where to turn with this problem, the alsa project doesn't have any support forums..

---

### Post by Stan83 on 2006-08-06
> **lodp said:**
> 
as for the ALC260 chip -- check Alsa-Configuration.txt for the appropriate model options (i forget where that .txt file is located). i'm pretty sure it's "model=acer", but there might be other options.

I tried those options, but still the alsamixer shows the chip to be ALC883, I think that maybe some other module should be loaded with different option, (maybe snd_hda_codec, but I don't know yet where to find options for this one, if this is the case).

> i ran into a new problem when i tried to compile the latest alsa-lib from the hg repository. when i ran  it says 

I guess ./configure is running with no problem? (It's run by ./hgcompile is it not?), I am not sure if it is possible but maybe try to run ./configure script (if there is any :) ), and than make. Probably wont help, but I have no other ideas.

---

### Post by lodp on 2006-08-06
i'm not sure whether there even are any options for snd_hda_codec (i recently tried to load it with model=acer, but i got an error message).

the ./hgcompile script is something special (involves this libtool thing) -- i'm going to try and get an answer on the alsa mailing list.

looks like this thing could drag out for a while .. i think i'm going to start looking for a suitable USB device -- any suggestions? i'm going to start a new thread on that, though..

man, this whole thing sucks. when i think of all the time i spent fiddling...

---

### Post by er-ku on 2006-08-06
Here's the list of available models:
[LIST=1]
[*]For ALC882:
[LIST]
[*] 3stack-dig
[*] 6stack-dig
[*] arima
[*] auto
[/LIST]

[*]For ALC883:
[LIST]
[*] 3stack-dig
[*] 3stack-6ch-dig
[*] 3stack-6ch
[*] 6stack-dig
[*] 6stack-dig-demo
[*] auto
[/LIST]
[/LIST]

---

### Post by lodp on 2006-08-09
wow - i didn't know about these model options -- where did you get these? which alsa-package do they come with? up to now i only looked them up in ALSA-Configuration.txt (somewhere under /usr/share/doc...), and there were far less of those options..

i tried those options, no success..

anyway, i'm not confident enough about testing these model options to say 100% sure that they're not working for me -- here's how i do it:

1. i kill all artsd processes, and the hda-codec/0 process in ksysguard
2. i unload snd-hda-intel, snd-hda-codec
3. re-load first snd-hda-codec, and then snd-hda-intel, this time with the option.
4. restart alsa (/etc/init.d/alsa-utils restart)
5. try playing a wav file with aplay

anything wrong with that? 

how do i know whether the module was loaded correctly with an option (i noticed that even loading a module with "model=RANDOM NONSENSE" doesn't give you an error message?

do i need to re-load any other modules (from those that show up under "lsmod|grep snd"?

how do i make sure nothing else interferes (apart from checking the alsa-mixer settings every time)

---

