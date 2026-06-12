---
title: "HP DV 67xx Conexant HD audio - Interesting discovery"
date: 2008-05-06
forum: Hardware
---

### Post by Vegetarianrage on 2008-05-06
So, along with the rest of the linux world, I'm having issues getting my computer to correctly identify the difference between the jack inputs and outputs and the internal inputs (mic) and outputs (speakers).

My problems are as follows:

**Muting the speakers only applies to the internal speakers, not the headphone jack.** 
So for example, if I have headphones plugged in and I mute the master device output then nothing happens. Volume adjust DOES work.

**Microphone input only works from the jack.** 
No amount of banging or shouting at the internal mic will make it register any sound. I have tried  adjusting literally everything on alsamixer and in pulse. Opening pulse's recording vu meters shows no activity until I plug in an external mic.

My interesting discovery is that ALSA seems to recognize my card, and many other people's, as a CX20561 (Hermosa) instead of a CX20549 (Venice). I've looked at my drivers and at the Conexant website and I'm pretty sure I have the Venice card. I tried adding ```
options snd-hda-intel model=laptop-hpmicsense
``` to  my /etc/modprobe.d/alsa-base file which according to /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz should force it to use the CX5045 drivers but it made no difference. In fact, I couldn't seem to force it to load anything at all. No matter which model I stick in alsa-base it always "correctly" loads the Hermosa drivers.

I know CX20549 (Venice) is the same as CX5045 because if you go here, and search for 20549: [http://www.alsa-project.org/main/index.php...4rc2_v1.0.14rc3](http://www.alsa-project.org/main/index.php...4rc2_v1.0.14rc3)
you will find:> 
hda-codec - More fixes for Conexant HD Audio support

Renamed Conexant 5045 to CX20549 (Venice) per Conexant Documentation
Renamed Conexant 5047 to CX20551 (Waikiki) per Conexant Documentation
Fixed automute on HP Laptops with CX20551 codec.
Fixed recording issues on Toshiba Satelite P100/P105 series laptops
Added HP DV8000, DV2000Z, Fujitsu Si1520 support

More work to be done on CX20549 based systems, but CX20551 Systems are
much better now.


So, is there a way to force it to load the CX5045/CX20549 drivers in place of what it's loading now? I couldn't get it to load anything else no matter what I put into alsa-base. Even when I tried to break my sound by forcing incompatible drivers. What am I doing wrong?

Relevant information:

alsa-info.sh - [http://pastebin.com/f1ffbf68e](http://pastebin.com/f1ffbf68e)
tsalsa - [http://pastebin.com/f6d2a6183](http://pastebin.com/f6d2a6183)

```
lsmod | grep snd:

snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

```

---

### Post by ivanmladek on 2008-06-09
Good discovery vegetarianrage. I have tried your  
> options snd-hda-intel model=laptop-hpmicsense to no avail. My pastebin is at
[http://pastebin.ca/1003159](http://pastebin.ca/1003159) . I have spent so much time on this, it's not funny. I might just get an external mike. Thanks for the detailed digging.

---

### Post by Vegetarianrage on 2008-06-14
I've already got an external mic because I have to use skype quite often. It defeats the laptop however, to have to carry hardware around with me. I can't stand it. There must be some way to force it to detect the correct hardware.

---

### Post by BOYerchen on 2008-06-16
I got the same problem on my HP Pavilion dv9810. Sound is fine except for the microphone.

---

### Post by cbw on 2008-07-03
I have a HP Pavilion dv9000 with Conexant sound card(laptop)

For the first time everything works fine(even the wifi) but the capture part of the recorder.  I have resolved to dual boot for the soul purpose of  audio recording.  It's not a total defeat, though.  I have installed Ubuntu on my desktops in the recording room.  At least there on those units there is recording capability.

But please let me know if there is a breakthrough on those drivers.

:guitar:cbw

---

### Post by cbw on 2008-07-06
so did anyone help you get capture working?
I too have problems with any sort of capture ability.

HP pavillion dv9000 laptop
Conexant venice is what my system shows

---

### Post by Vegetarianrage on 2008-07-07
Yours is recognized as a venice? Would you mind posting your hardware info?
This code downloads a script which checks out your setup and makes a pastebin automatically, courtesy of the people at #alsa on freenode. If you're anxious about running the script I encourage you to go question them about it.

```
wget http://home.cfl.rr.com/infofiles/tsalsa
bash ./tsalsa
```

Then paste the the url printed by tsalsa on here. I just want to see what driver versions you're using and what the id# of your audio device is. Thanks!

Here's mine: [http://pastebin.com/f1b6afbac](http://pastebin.com/f1b6afbac)

Note, if it fails to upload your file to the pastebin service you'll have to do it manually. The text file is found at /tmp/tsalsa.txt

---

### Post by cbw on 2008-07-10
here it is.......

cbw@cbw-laptop:~$ wget [http://home.cfl.rr.com/infofiles/tsalsa](http://home.cfl.rr.com/infofiles/tsalsa)
--11:43:33--  [http://home.cfl.rr.com/infofiles/tsalsa](http://home.cfl.rr.com/infofiles/tsalsa)
           => `tsalsa'
Resolving home.cfl.rr.com... 208.79.153.50
Connecting to home.cfl.rr.com|208.79.153.50|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20,298 (20K) [text/html]

100%[====================================>] 20,298        70.77K/s             

11:43:33 (70.69 KB/s) - `tsalsa' saved [20298/20298]

does that say anything to you?  Don't see much about drivers there.

---

### Post by cbw on 2008-07-10
theres more.


 [http://pastebin.ca/1068247](http://pastebin.ca/1068247)

---

### Post by matthewbpt on 2008-07-10
I have the same laptop, well mines dv9225us, with the same conexant sound card, and my internal microphone worked immediately out of the box, with no change in drivers or tweaking configurations, dont know why yours wouldnt work

---

### Post by Vegetarianrage on 2008-07-10
Well you guys seem to have different hardware after all as alsa is getting different id numbers. 

With that in mind, it may be that there is no real problem with yours, cbw. I noticed that your volume settings are at zero for several capture devices. Try adjusting them. Run alsamixer in a terminal or if that doesn't work try pavucontrol (may need to be installed).

---

### Post by cbw on 2008-07-11
The on board or internal mic can work...
but I like to record digital through the sound card.
I do a lot of recording in what some would call studio settings.

I've been a windows guy forever(days of DOS)
I am just learning in this brave new world called Linux.

side note:
I've tried Fedora,Sam,PCLINUX 2007, Suse....and others even early ubuntu.  This is the only version of Ubuntu that worked right out of the loading gate (after the updates)The other versions just locked up my machine.

Needless to say I'm getting an education thanks to all of you.
Thanks for any and all help.

---

### Post by cbw on 2008-07-11
To be fair.....after reflecting, PCLinux2007 was my favorite.  But I never got the "capture portion"(soundcard) not internal mics to function.  Most of everything worked there.

There were things I liked about all the versions.

---

### Post by AlanB66 on 2008-07-24
I've logged a Bug Report here:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/225926](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/225926)

It's for a Compaq F750US - basically an HP product. Probably the same issue.

Very frustrating!

---

