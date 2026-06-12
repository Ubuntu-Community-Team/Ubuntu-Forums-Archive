---
title: "Zepto 6625WD Soundcard spdif output?"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by djcla on 2007-11-01
HI, newbie here to linux plase help me!!!!

before i wipe my PC for Ubuntu I have a quick question .  I know there are driver issues for this laptop with the sound which i hope to resolve with the guides i have found.  What i would like to know is if anyone has got the card working (ALC268 i think but might be wrong) and the headphone/spdif socket works?  I need the optical output to work and want to know if anyone on this model zepto or one similar has the light comming from the spdif socket or even better used it successfully?

---

### Post by nidelius on 2007-11-02
I have the same laptop running kubuntu have not even tried to get the sound working because my CD/DVD drive is not working. But if I do I will post you.

---

### Post by djcla on 2007-11-02
have you tried disabling the cd drive in the bios?  I can install from the cd drive but then it does not work in os until i have disabled in the bios odd i know

---

### Post by Laellis on 2007-11-03
That missing drive is a known issue and easy to go by, seach notebookreviews forums for the solution.

And on the ALC268 output, could someone who actually has made the optical output work post something here. On all other topics people say something like "Yea, that did the trick headphones working" etc. None has said straight they have the little red light coming out. It just doesn't work (TM). :)

---

### Post by nidelius on 2007-11-03
I have read som posts to get the audio to work but have not been succesful so far. Maybe you guys can figure a way out here are some intresting topics


6625WD do I dare? - [http://ubuntuforums.org/showthread.php?t=540424](http://ubuntuforums.org/showthread.php?t=540424)
Specific HDA sound FAQ - [http://forum.notebookreview.com/showthread.php?t=174819](http://forum.notebookreview.com/showthread.php?t=174819)
General 6625WD FAQ for mandriva - [http://wiki.mandriva.com/en/index.php?title=Releases/Mandriva/2008.0/Errata&printable=yes#No_sound_with_Zepto_Znote_6625WD](http://wiki.mandriva.com/en/index.php?title=Releases/Mandriva/2008.0/Errata&printable=yes#No_sound_with_Zepto_Znote_6625WD)
General HDA sound FAQ - [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
General HDA sound FAQ - [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
General HDA sound FAQ - [http://ubuntuforums.org/showthread.php?t=545318&page=2](http://ubuntuforums.org/showthread.php?t=545318&page=2)
Swedish Get 6224WD running guide - [http://www.ubuntu-se.org/drupal/node/345](http://www.ubuntu-se.org/drupal/node/345)
Some ALC268 post - [http://ubuntuforums.org/showthread.php?t=540036&page=2](http://ubuntuforums.org/showthread.php?t=540036&page=2)
Some no sound issue post - [http://ubuntuforums.org/showthread.php?t=555709](http://ubuntuforums.org/showthread.php?t=555709)

---

### Post by nidelius on 2007-11-03
I have also tried these steps with no success. [http://atlas.hasselbalch.com/znote6625wd/](http://atlas.hasselbalch.com/znote6625wd/)
Most posts are for feisty that might be the problem

---

### Post by djcla on 2007-11-03
i have finaly manged to get the sound comming out of my machine compilng the alsa .14r2 drivers and following a guikde i found on here but i have no optical light comming on which is annoying to say the least.  There must be a way or its back to M$ for me...Someone must have it working with alc268 sound card

---

### Post by Ronni Elken Lindsgaard on 2007-11-03
> **djcla said:**
> i have finaly manged to get the sound comming out of my machine compilng the alsa .14r2 drivers and following a guikde i found on here but i have no optical light comming on which is annoying to say the least.  There must be a way or its back to M$ for me...Someone must have it working with alc268 sound card

Do you think you can find that guide again? The closest i got was installing drivers that looked like working, but no sound coming out :(

---

### Post by djcla on 2007-11-03
sure thing
[http://ubuntuforums.org/showthread.php?t=545318&page=2](http://ubuntuforums.org/showthread.php?t=545318&page=2)
i looked at nille post and followed it to the letter on a clean install

---

### Post by nidelius on 2007-11-03
I don't know what I did but I got it to work although without the spdif out but I can manage with headphones for now

grep Codec /proc/asound/card0/codec#*
/proc/asound/card0/codec#0:Codec: Realtek ALC268

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils

and added the famous line to sudo kate /etc/modprobe.d/alsa-base

options snd-hda-intel model=toshiba

then reboot and it worked

---

### Post by djcla on 2007-11-03
i am thinking my headphone would work if i owned any all i want is spdif out so i am annoyed and looking at alternatives for now

---

### Post by Ronni Elken Lindsgaard on 2007-11-03
worked like a charm :) thnanks a lot

---

### Post by djcla on 2007-11-04
hmmm progress i have got the optical output working, but this has in turn broke the internal speakers.

OK here s what i did followed nilie's instructions to the letter [http://ubuntuforums.org/showthread.php?t=545318&page=2](http://ubuntuforums.org/showthread.php?t=545318&page=2) then re ran them with the latest drivers and changed some things see below

downloaded the latest asla drivers

but instead of running sudo ./configure --with-cards=hda-intel --with-oss=yes
i just ran sudo ./configure
sudo make 
sudo make install

same for the utils and lib etc.

If you do not add the  options snd-hda-intel model=toshiba line to the /etc/modprobe.d/alsa-base file and just reboot there are more sound options

I double clicked on the volume icon and selected the switched tab under this you can enable iec958 and then the optical light comes on.   

Now i just need to work out how to get this option available with the toshiba line

---

### Post by Laellis on 2007-11-04
Hell yeah, the optical output is the only sound option I need in Ubuntu, gonna try that later today. Hope it works.

---

### Post by djcla on 2007-11-04
should work mate , taken me 2 days of fidling to get this far.  just post me if youget stuck i will try to help.  All i need to know know is how to get the FN f4 button to work..   Must be a way of getting the external monitor/display to work in ununtu

---

### Post by Laellis on 2007-11-04
Yup that did the trick, had to enabled the IEC958 using alsamixergui but that's almost the same. Finally no real reason to go back to Vista. :)

---

### Post by djcla on 2007-11-04
i am strating to think that too, once i have cracked this external monitor thing, can't seem to get it on the monitor only yet.  But i have manged to seperate desktops so far.  (sorry not related i know)

---

