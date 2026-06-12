---
title: "Ubuntu 10.10 Sound issue / no headphone sound / Asus G50vt"
date: 2010-11-17
forum: Hardware
---

### Post by manco1911 on 2010-11-17
I just installed Mint 10, which is base on 10.10. 
AND i also tried with Ubuntu 10.10 liveCD. 

Running on a ASUS G50vt-x2 laptop. 
The thing is that im having sound issues. 
Internal speakes work fine. 

But i cant get any sound on my headphones. At least not if i plug them all the way in. 
If i keep them not fully pluged, but a bit out, i get sound on my headphones and on the internal speakers. 

No clue where to start here.. 
If its of any help, i also dont have working nor the internal microphones or the mic input, or the audio input. (this laptop has 3 spica plugs).

Here is my lshw -c sound:
*-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:48 memory:f9ff8000-f9ffbfff

Just ring if there's any other info i can provide to you guys in order to know whats going on. 

Thanks guys/grls

---

### Post by manco1911 on 2010-11-19
Ok, finally, after a few days of frustrating search with no luck, i got the solution. 
My hardware is in the first post if you need it. 

**SOLUTION:**
Modify the alsa-mixer conf file to recongise your hardware soundcard. 
_file locaton:_ /etc/modprobe.d/alsa-base.conf

_how to edit it:_
sudo nano /etc/modprobe.d/alsa-base.conf       (i use nano for text editing, you can use gedit, vi, or the one you please). 
[U]
At the last line, i added this one:[/U]
options snd-hda-intel model=m51va position_fix=0 

So my alsa-base.conf looks like (note this are only the last lines.. ):
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
**options snd-hda-intel model=m51va position_fix=0**

That's it ! Just reboot and everything is workig as it should. Plug headphones, sound only on headphones, Unplug, sound on internal speakers ! :)

If you need to solve it for another laptop model/brand (these are for intel soundcards), here you have a full list of the alsa options to modify the alsa-base.conf file:

[http://doc.ubuntu-fr.org/audio_intel_hda#acer](http://doc.ubuntu-fr.org/audio_intel_hda#acer)


I have to thank WaroDaBeast, who gave this solution on this [thread.]("http://ubuntuforums.org/showthread.php?t=1597218")

---

### Post by anurak_d on 2010-11-28
Ah! Thank you man. I will try this.

---

### Post by coolnezz on 2010-12-27
This is awesome!  It worked!  Thank you!!!!  :D
:popcorn:

---

### Post by bmdavis on 2011-01-01
Worked for me with my headphone issues! (using dell studio xps 1640). 

Thanks so much!

---

### Post by tonyzhp1987 on 2011-01-02
Hello Manco1911

Serious sound problem! please help me out.

my sound card was fine when i installed ubuntu 10.10, 

but after i saw jsevi83 post, i got huge sound problem, there is no more sound!!! the sound device has gone!
still thanks Jsevi83 a lot, because fixed my other problems.
for example i fixed the wireless LED light, calculator, suspend problems.

please please help me out,right now my world without any sound. my laptop no more sound. 

i checked the lib/modules/2.6.35-24-generic/kernel/sound
there are no more pci file and others.

please Help me!!!!!!!!!

thank you very very much!

---

### Post by lidex on 2011-01-02
> **tonyzhp1987 said:**
> 
my sound card was fine when i installed ubuntu 10.10, 
but after i saw jsevi83 post, i got huge sound problem, there is no more sound!!! the sound device has gone!

You probably borked your alsa install. Can you do this please?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Naes_gregory on 2011-01-04
Tried the code above and it worked perfectly. 

Thanks very much, 

Naes.

---

### Post by khardysius on 2011-01-08
Have had a problem with headphone sense, etc. with my Asus U50f.  Upgraded from 10.04 to 10.10, added a similar line as stated above and in this link:

[http://doc.ubuntu-fr.org/audio_intel_hda#acer](http://doc.ubuntu-fr.org/audio_intel_hda#acer)

I chose the first in the table for Asus (A52F) and it worked fine.  After the upgrade to 10.10 it shows that I have Intel IbexPeak HDMI (which is not what it said or read in 10.04).  10.10 seems to be easier at resolving this issue; upgrade if it's feasible.

Now on to the touchpad problems!

---

### Post by yax51 on 2011-01-12
Thanks! the head phone issue was resolved! however, did you find anything to fix the mic? mine still doesn't want to work. Thanks!:)

---

### Post by bwitt on 2011-01-15
Has anyone found a fix for this for Asus K60IJ? I've tried most of the suggested edits to alsa-base.conf and none of them worked.

Thanks.

---

### Post by kcode on 2011-03-14
Thanks a lot, it did help.

---

### Post by tsarprodigy on 2011-03-18
> **manco1911 said:**
> Ok, finally, after a few days of frustrating search with no luck, i got the solution. 
My hardware is in the first post if you need it. 

**SOLUTION:**
Modify the alsa-mixer conf file to recongise your hardware soundcard. 
_file locaton:_ /etc/modprobe.d/alsa-base.conf

_how to edit it:_
sudo nano /etc/modprobe.d/alsa-base.conf       (i use nano for text editing, you can use gedit, vi, or the one you please). 
[U]
At the last line, i added this one:[/U]
options snd-hda-intel model=m51va position_fix=0 

So my alsa-base.conf looks like (note this are only the last lines.. ):
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
**options snd-hda-intel model=m51va position_fix=0**

That's it ! Just reboot and everything is workig as it should. Plug headphones, sound only on headphones, Unplug, sound on internal speakers ! :)

If you need to solve it for another laptop model/brand (these are for intel soundcards), here you have a full list of the alsa options to modify the alsa-base.conf file:

[http://doc.ubuntu-fr.org/audio_intel_hda#acer](http://doc.ubuntu-fr.org/audio_intel_hda#acer)


I have to thank WaroDaBeast, who gave this solution on this [thread.]("http://ubuntuforums.org/showthread.php?t=1597218")


[SIZE=3]FOR WHOEVER HAS ISSUES WITH gedit or nano showing blank text files after doing this command, its ok! this will still work.  

all you have to do is take that blank gedit/nano window, go to file>open and navigate to /ect/modprobe.d/ and click on alsa-base.conf and click open. THIS should make the file show up, rather than appearing blank! :D [SIZE=1]thanks for reading this lol i wanted to make sure people saw it, so i put it in a large font size. :D[/SIZE][/SIZE]

---

### Post by sovichet on 2011-08-04
Awesome! I have fixed it now with this solution. Thank you!

---

