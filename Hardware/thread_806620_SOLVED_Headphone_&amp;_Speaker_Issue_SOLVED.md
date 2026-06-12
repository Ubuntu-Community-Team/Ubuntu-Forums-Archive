---
title: "SOLVED Headphone &amp; Speaker Issue SOLVED"
date: 2008-05-25
forum: Hardware
---

### Post by davidkyn on 2008-05-25
**SOLVED..**.Headphone & Speaker Issues:
Ussualy effect intel HDA sound cards...Sound comes out both fronts and headphones at same time!

My Solution for Ubuntu8.04.............**Basicaly you just want to add a switch to the volume controll!**
[IMG]http://i181.photobucket.com/albums/x30/davekyn/VolumeControl.png[/IMG][IMG]http://i181.photobucket.com/albums/x30/davekyn/Switch.png[/IMG]

Tell alsa which driver to use for your hda intel sound card. You do this by first looking at the output of 
Code:
head -n 1 /proc/asound/card0/codec*

Mine was:
Codec Realtek ALC888

SO you then issue the command: 
Code:
zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

Look for the subtitle "Module snd-hda-intel".
In this subsection look for the name of codec &#8220;you&#8221; aquired from the output above...Mine was Realtek ALC888...so after locating  the list for  &#8220;Module snd-hda-intel&#8221; I scrolled down further to find:

ALC883/888 then I looked at the options directly under and chose &#8220;_3stack-6ch_   3-jack 6
 channel&#8221; you may have to choose another option or experiment.

Important!!!!Now that you have an option what do you do with it.........1st you only take the part of it...that is the part directly under the listed codec...for me that is &#8220;_3stack-6ch_&#8221; and add it to the following line to get:
[U]
options snd-hda-intel model=3stack-6ch[/U]

Without the underline of course, so that it looks like:

options snd-hda-intel model=3stack-6ch

This is the line that you need to add to /etc/modprobe.d/alsa-base by doing the following:

For Ubuntu:
sudo gedit /ect/modprobe.d/alsa-base

When the new window opens, cut and paste the new line you have just made at the bottom of all the text, save and exit.

Restart and hopefully if you have not buggered up with the spacing as I did you should now have a SWITCH option in your &#8220;Volume Contol&#8221; found in the desktop panel.  Just deselect or select to switch between speakers of headphones as it should have been from the start.

HOW RIDICULOUS FOR something SO ESSENTIAL...TOOK ME ALL DAY TALKING TO MYSELF AND SEARCHING THE NET TO FIX. Oh yea..a special thanks to the guys at the Suse Forum as well :)

HOPEFULLY THIS WILL HELP SOMONE ELSE...I would say it was more a case with the module than it was ever with updating...but then again I dont know that much ecept what I have learnt today...........Persistance Pays I guess!:guitar:

---

### Post by doorman on 2008-05-30
Thank You so much davidkyn for your post!

Solved my problem in 5 mins after browsing a lot on the web!

---

### Post by davidkyn on 2008-05-30
your welcome...took me ages to resolve as well:)

---

### Post by beginnerman on 2008-06-04
I just thought I would mention that my sound is working perfectly on my 64-bit system as we speak as a result of this fix.
I have the ACL262 on a fujitsu laptop, and was able to add the line, restart, and voila!
Excellent advice!
And there's not even a switch necessary afterwards... Jack in, speakers off.
God I love a *working* linux system!

---

### Post by garoth2 on 2008-06-05
options snd-hda-intel model=haier-w66  

Worked for my Asus m50SV-A1. Perhaps we could start a thread to correlate the alsa model parameters with laptop models?

---

### Post by chriskin on 2008-06-07
well the easier way
download alsamixergui and configure everything
easy living :D

---

### Post by Le Rob on 2008-06-08
I can confirm this works on my LG e550, though the headphone switch seems to operate backwards -- if the 'headphone' box is checked, it will play through the speakers, and if it is unchecked, it will play through the speakers only if the headphones are unplugged.

---

### Post by The Cosmic Hobo on 2008-06-08
I've been having similar problems with my laptop's onboard sound (nothing, rather than both, working), and it uses an Intel motherboard and audio processor - so I'll try your solution. Thanks davidkyn, that's both helpful **and** easy to follow :)

---

### Post by wasutton3 on 2008-06-08
i have tried this solution but it appears to not do anything. i still have the same issues. i run hardy on an asus m50, and i noticed there were a few asus tags in the alc880, but the intial command yields an alc888, would there be any downside to trying out something else?

---

### Post by terrax on 2008-06-10
> **wasutton3 said:**
> i have tried this solution but it appears to not do anything. i still have the same issues. i run hardy on an asus m50, and i noticed there were a few asus tags in the alc880, but the intial command yields an alc888, would there be any downside to trying out something else?


I got an Asus M50SA laptop, and I got a "working" headphone switch with the targa-dig model.

---

### Post by garoth2 on 2008-06-10
As I mentioned above, I got my M50Sv with an ALC888 working with the haier-w66 model.

-Jeff

---

### Post by Maxell_lite on 2008-06-12
I have a Fujistu A3130 and I tried putting 'options snd-hda-intel model=fujitsu' into the alsa-base, but upon restart absolutely nothing changed with the speakers playing sound with the headphones plugged in. and it came back with the ALC262 codec.

---

### Post by belevume on 2008-07-03
Is there a way to do this if I get N/A under my codec (AD1983) instead of details within ALSA-Configuration.txt.gz?

I'm able to check the box within Volume Control and mute the front speakers, but I feel like I shouldn't have to do that every time I plug in headphones.

Thanks!

---

### Post by stchman on 2008-07-03
I too had this problem with my older Toshiba laptop.  Installing ALSA 1.0.15 fixed the problem.

If you install Hardy the headphone speaker thing works just fine.  Hardy uses ALSA 1.0.15.

---

### Post by belevume on 2008-07-03
Thanks so much!  Awesome.

---

### Post by Sealbhach on 2008-07-04
```
options snd-hda-intel model=vaio
```


fixed it for my Vaio.

Thank you so much!:guitar:


.

---

### Post by jdash1 on 2008-07-04
mine does not work with this work around


i tried all the option in my laptop



I'm using blue wseries (radon)

my current ver. of alsamixer is v1.0.17rc1


after putting this word
options snd-hda-intel model=hp


i tried it in diff option in the bottom. still no luck. :(

> 
ALC260
	  hp		HP machines
	  hp-3013	HP machines (3013-variant)
	  fujitsu	Fujitsu S7020
	  acer		Acer TravelMate
	  will		Will laptops (PB V7900)
	  replacer	Replacer 672V
	  basic		fixed pin assignment (old default model)
	  test		for testing/debugging purpose, almost all controls can
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)




Any help would be highly appreciated. 
thanks

---

### Post by Sealbhach on 2008-07-05
I think this fix only applies to Intel HDA sound cards. So make sure it is Intel HDA first.

Are you using a laptop?

Try 

options snd-hda-intel model=laptop-hp

or


options snd-hda-intel model=laptop-hpsense

These are other HP options I saw in that list, worth a try until someone else comes along who might know more.


.

---

### Post by jdash1 on 2008-07-05
> **Sealbhach said:**
> I think this fix only applies to Intel HDA sound cards. So make sure it is Intel HDA first.

Are you using a laptop?

Try 

options snd-hda-intel model=laptop-hp

or


options snd-hda-intel model=laptop-hpsense

These are other HP options I saw in that list, worth a try until someone else comes along who might know more.


.



yes i'm using a laptop Blue radon Wseries model its the same ODM of HP so i'm using the Option for "hp"

> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC260 Digital [ALC260 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


that's my aplay -l

ill try that and see.:)

is my version of alsamixer okay ?  **v1.0.17rc1**



THanks for the reply bro.

---

### Post by Sealbhach on 2008-07-06
> **jdash1 said:**
> 

is my version of alsamixer okay ?  **v1.0.17rc1**



THanks for the reply bro.

I really wouldn't know, is it the latest in the repos? If not you'de be safest to update it.

Did you try the other HP module there?

HP 3013  ?


.

---

### Post by loctorn on 2008-07-06
> **wasutton3 said:**
> i have tried this solution but it appears to not do anything. i still have the same issues. i run hardy on an asus m50, and i noticed there were a few asus tags in the alc880, but the intial command yields an alc888, would there be any downside to trying out something else?

you could try this which help'd me and it was instead of 
options snd-hda-intel model=3stack-6ch  
*I used this but had to continuously plug/unplug my headphones before it would work and upon system restart it continued to not work till I started plugging/unplugging it again...would take up to 8 times before it worked.*

I instead used

options snd-hda-intel model=targa-dig

This option worked for me the first go round....system restart and still working.  Might hafta play around with different variation's depending on your system and see what happen's.

I have an MSI EX600 Laptop and this has been the only problem that I've had thus far with Ubuntu and now it's fixed.

Hope this help's someone out there =P

---

### Post by Lord C on 2008-08-18
Tried 
options snd-hda-intel model=targa-dig
options snd-hda-intel model=auto probe_mask=1 position_fix=1
options snd-hda-intel model=lenovo

and lots more.

Whatever I do, I can't stop the speakers playing with I switch to headphones :/

Running a Realtek ACL888

---

### Post by Zero-Override on 2008-08-25
sweet!!!!

targa-dig fixed everything for me :D

good bye final annoyance.. may I never see your mangy *** again :lolflag:

---

### Post by Gabt on 2008-08-25
I just installed Gnome LASA mixer, and unmuted the side speakers, plugged my headset in, and voila :D

Both work at same time, full volume, no swicthes needed. :D

---

### Post by SergeantScar on 2008-09-16
This also worked for me.
Don't like having to switch it every time i plug my headphones in but its better than nothing...

Thanks!

---

### Post by it_col on 2008-09-24
This solution does not work for vaio NR498e. I've try and no result.But it was fixed by only install VLC 0.8.6e.

---

### Post by Dusenberg on 2008-09-27
Worked for me! Thanks.

As standard I had a headphone switch in mixer but it did nothing. Tried several options, only 'hippo' worked as it gave me a headphone slider in the mixer. 

Philips x66 laptop, Realtek AL262 codec, Intel 82801G ICH7
7.1 gutsy

---

### Post by hesion10 on 2008-09-30
wow~~so  I'm really no idea.cause I can't find out the sound card by the list 

beside  windows XP is using the VIA VIA1708,

and here
environment is ubuntu 8.04 
installed in laplop

==> /proc/asound/card0/codec#0 <==
Codec: VIA VIA VT1708

==> /proc/asound/card0/codec#1 <==
Codec: Motorola Si3054

----------

and the /etc/modprobe.d/alsa-base
---------
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
#options snd-hda-intel model=??**	#how do I setting for? thank u~~!**
---------

---

### Post by Pedhead on 2008-10-11
It looks like this is heading me in the right direction. However, when I enter the command-

sudo gedit /ect/modprobe.d/alsa.base

I open a window named- 

*alsa.base (ect/modprobe.d) - gedit

this window is completely blank. But I tried entering the text anyways-

options snd-hda-intel model=vaio

And I get an error message reading-

Could not save the file [i]/ect/modprobe.d/alsa.base[i] unexpected error, file not found

So I close out that window and I have an error message on my terminal, basically saying the same thing... 

I would think that file would be named the same in Mint as in Ubuntu, but maybe I am wrong..? Maybe I am missing something?

EDIT:: OK THE WINDOW HAS TEXT IN IT, ITS JUST HIDDEN!:lolflag: THANKS!!

---

### Post by blackened on 2008-10-15
This worked perfectly for me on a Sony VGN-NR385SE. Used sony-assamd option with Realtek ALC262. Eliminates the need for the headphone switch, speakers turn off when headphones are plugged in.

---

### Post by ayalam30 on 2008-10-23
How did you get it to show the hidden stuff? I can't get my sound or headphones to work either. I have on board sound from a gigabyte ga-p35-ds3l.

---

### Post by shasto on 2008-10-25
HP Pavillion t3610.uk is a 6stack-dell

Working now

---

### Post by Amaroq on 2008-11-03
This is my first build, using an ATI M3A32-MVP Deluxe motherboard with the onboard sound. The output of my aplay -l is:
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

(I think that third is my video card... somehow...)

Does this guideline even apply to my hardware? I've followed it, ending up with 6stack-dig. (Just 6stack outputted the same on aplay -l, but that second device was missing.)

I'm still having the same problems I was having before. No headphone detection. Both the headphone and speaker are always on. If I want to use headphones only, I have to mute the Front slider, but adjusting the volume of that slider still affects my headphones, even though they stay on when it is muted.

---

### Post by Neon Nomad on 2008-11-03
Hi, this worked perfectly on my HP Compaq DX2300 desktop 

I wish I had located your post earlier, it would have saved me a lot of time.

Thanks !!!

---

### Post by slauzinho on 2008-11-07
THanks so much solved my problem :guitar:

---

### Post by linkmaster03 on 2008-11-09
I've tried every single model in this thread, along with auto, 3stack, 3stack-6ch, toshiba, and lenovo. I have a Toshiba Satellite A135-S4727, and I can't even get sound to play out of my headphones AT ALL. After each model change in the alsa-base file, I restarted ALSA and PulseAudio. Headphones channel is up all the way in my mixer...

---

### Post by the1killyou on 2008-11-17
Hey any1 would mind to help me? currently im using a compaq presario v3000 laptop and i need guide to help me solve the headphones problem because i was unable to solve it with previous way

---

### Post by gaixixon on 2008-11-21
DOESn't work on LenovoG410!!
:(:(:(:(:(

---

### Post by seshomaru samma on 2008-11-25
THANK YOU SO MUCH!

found this after hours of googling for a new 8.10 install

---

### Post by dehuszar on 2008-11-27
I'm trying to get the ALC888 chipset in my ASUS M70Sa to mute the speakers when the headphones are plugged in.  I've tried every model variant.  I'm now playing with additional options. 

Has anyone found a combination which works for this laptop?

---

### Post by nmayorga on 2008-11-29
Hi!

I've just installed 8.10 on my new desktop vaio VGC-LV1S. 

$ aplay -l returns ALC889 (not listed anywhere, TTBOMK, on this thread)
$ head -n 1 /proc/asound/card0/codec*
Codec: Realtek ALC889

So, I haven't found any options for my card/codec :-(

BTW, the problem I'm having is that volume control does work Master, PCM and Front do the same and Headphones does not change that effect and plugging the headphones in does not stop front speakers from playing. Furthermore, headphone volume appears to be controlled by those other controls (instead of being changed by the Headphones one).

Any help will be very much appreciated.

Thans in advance,

                     Nacho

---

### Post by dehuszar on 2008-11-29
:guitar:

Booyah!  So it turns out that the haier-w66 is the correct model to use, but the statement also needs the options probe_mask=1 position_fix=1.  So the full statement looks like this:
```
options snd-hda-intel model=haier-w66 probe_mask=1 position_fix=1
```.

Now the headphone mute works for my ASUS M70Sa / ALC888 HDA-Intel chip.

I hope that helps someone else.

Sam

---

### Post by psychoelf on 2008-11-30
Worked on Gateway 6850FX!   :popcorn:

Update:  No longer working. WTF? Today I booted up and plugged in speakers and no sound from external speakers.  Reboot with plugged in and it works.  Unplug and plug back in...not working.  Help please?

---

### Post by windsword on 2008-12-02
My system too works partially, no switching when I plug in the headphone.

when type:  head -n 1 /proc/asound/card0/codec*
I get: Codec: Realtek ALC889A

Under:  zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz 
I don't see an option for this Realtek ALC889A, 
so I tried: model=imac24 

I have a Macbook Pro running Xubuntu 8.10, please let me know if there is a work-around for this.

Thank you

// Sal 

> **Lord C said:**
> Tried 
options snd-hda-intel model=targa-dig
options snd-hda-intel model=auto probe_mask=1 position_fix=1
options snd-hda-intel model=lenovo

and lots more.

Whatever I do, I can't stop the speakers playing with I switch to headphones :/

Running a Realtek ACL888
options snd-hda-intel model=imac24

---

### Post by Senesence on 2008-12-06
I'm having some trouble here.

Output of **head -n 1 /proc/asound/card0/codec***:
```

==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 663

==> /proc/asound/card0/codec#1 <==
Codec: Generic 10de ID 3

```

There is no "ID 663" listed in the **/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz** file.

Is there anything I can do despite that fact?

---

### Post by Sav on 2008-12-08
I can't find a valid option for Dell Studio slim (inspiron 540s): no sound trough spdif.

---

### Post by nightcrawl on 2008-12-11
Great solution!! :guitar:

---

### Post by tricota on 2008-12-21
Great Solution, 
It works for LG E500 notebook running UBUNTU hardy

The point is, why this is not automatic when you plug the headphone??  This should be automatic,  you plug the headphone and the built in speaker should be gone.

I have a dual boot, and I had the same problem in windows (it seems to be a Realtek sound card driver problem),  I update the drivers and problem solved, but it does it automatically, you don't have to tilt anything, by just plug in the headphones it kills the built in speakers automatically.

I hope this is trluy solve in future releases.

THANKS A LOT FOR THE WORKAROUND
Tricota

---

### Post by jobsagoodun on 2009-01-03
> options snd-hda-intel model=haier-w66 probe_mask=1 position_fix=1

Thanks very much for this! This works perfectly on a Fujitsu-Siemens Amilo 3650 Xi.

---

### Post by Schok on 2009-01-07
Help me!
[B]
Acer Aspire 5050 with ALC883[/B]

Tried with the option "acer" laptop has sound but wont detect headphone use.
Tried with the option "acer" and ```
probe_mask=1 position_fix=1
``` and NO SOUND at all..the volume setting is all mixed up. Here's my thread:

[http://ubuntuforums.org/showthread.php?p=6466060#post6466060](http://ubuntuforums.org/showthread.php?p=6466060#post6466060)

ps-its getting real annoying switching between using the headphone and laptop speakers..tired of muting and unmuting manually.

---

### Post by Shpongle on 2009-01-07
im using the realtek alc861-vd an a toshiba equium and iv tried all lots of different options bt still the sound is coming out of the speakers while the headphones are plugged in, i cant seem to solve this at all??:(

iv tried all the alsa configurations and checked the checkbox for the headphones . . . ect bt still to no avail

any suggestions ???

btw im running ubuntu 8.10

---

### Post by uBeer on 2009-01-09
Worked for me on a Dell Studio 1737.

Output head -n 1 /proc/asound/card0/codec*:
Codec: **IDT 92HD73C1X5**

zless ALSA-Configuration gave:
**STAC92HD73***

So I added '**option snd-hda-intel model=dell-m6**'
Rebooted and magic!

It switches automagically on inserting jack, so no need for manual switching!
Thank you very much!!

---

### Post by Shpongle on 2009-01-09
> **Lord C said:**
> Tried 
options snd-hda-intel model=targa-dig
options snd-hda-intel model=auto probe_mask=1 position_fix=1
options snd-hda-intel model=lenovo

and lots more.

Whatever I do, I can't stop the speakers playing with I switch to headphones :/

Running a Realtek ACL888

im having the exact same problem and tried all them too , im running a realtek avc861-vd

---

### Post by Daigakusei on 2009-01-10
hahaha thanks a lot, I have ubuntu 8.10, intrepid ibex and worked excellent

---

### Post by fathead_gti on 2009-01-12
Wow cheers buddy, after countless hours spent over two days I have eventually found a solution that works!

Thanks again mate :)

---

### Post by seish on 2009-01-21
Works on  ASUS F3N laptops.

Codec: Realtek ALC660-VD

I used: options snd-hda-intel model=**lenovo**

Just leave headphone switch on, speakers turn off when you plug the jack in.


THANK YOU! :KS:KS:KS:KS:KS:KS:KS

---

### Post by phantom3113 on 2009-01-22
> **psychoelf said:**
> Worked on Gateway 6850FX!   :popcorn:

Update:  No longer working. WTF? Today I booted up and plugged in speakers and no sound from external speakers.  Reboot with plugged in and it works.  Unplug and plug back in...not working.  Help please?

This is a half bump half help request. I have an identical problem as this (only with headphones, but they both use the same jack) and I hadn't tried any of this before hand. I attempted the workaround in the OP trying multiple different options, but nothing worked. aplay -l gives me this:

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

head -n 1 /proc/asound/card0/codec* yields this:

```
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9205

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040
```

I tried the options for STAC9205 in the list of different sda-hda-intel options, but like I said nothing improved, not to mention that the only ones listed were dell. My laptop model is Gateway T-1621. I would absolutely LOVE anyone that can assist with this as this is driving me crazy! All I want to do is use my headphones when I want to without having to have them plugged in prior to boot. :'(

---

### Post by hhabroad on 2009-02-02
Just wanted to say THANKS!  I've been wandering about the different posts for the last couple of hours when I finally discovered this one, which gave me all the info I needed to fix my sound problems with my laptop.

For other's info, its a LG T1 Series Laptop with an ALC880 sound card.  The module to use was simply the lg option.  Works perfectly now.

---

### Post by liqwiz on 2009-02-07
This was the ONLY solution that worked to this. No one else seems to even understand the problem.
Thank you So Much. Without this I'd given up on Ubuntu, a thing like this simply does it you know.

=]

---

### Post by gaixixon on 2009-02-08
How about Lenovo G410? Has anyone fixed this bug on this machine?? Please help me.. I am running Intrepid Ibex.

---

### Post by Mac181 on 2009-02-10
/ect/modprobe.d/alsa-base doesnt exist for me, and I cant save that file. 

Also, my laptop (lenovo ideapad y530) doesnt exist. 

I already have a 'headphone' switch. When its checked, I hear sound in both speakers and headphones. Unchecked, speakers but no headphones.

---

### Post by g0er on 2009-02-15
Made it to the end of this solution before encountering a problem, I'm on an ASUS F3 laptop with Realtek ALC660- VD running on Ubuntu 8.10. When I open alsa-base a new window opens, but there is no text in he window. I pasted options [snd-hda-intel model=asus laptop] as should have been my option and attempted to save, but when I did an error message read:

"Could not find the file /ect/modprobe.d/alsa-base."

Same problem as Mac181, already have the headphones switch and the same thing happens.

Any ideas? Thanks:confused:

---

### Post by uranous on 2009-02-15
Hi,
I used this guide to solve my "sound from both speakers and headphones" problem. I typed this: options snd-hda-intel model=3stack-6ch and after the reboot sound did just come out from the headphones, but when i plugged them out i couldnt get any sound from the speakers :P Tried plugging in and out and checking/unchecking the headphone switch but with no luck...
Any ideas?
Thanks in advance :)

---

### Post by WGamradt on 2009-02-16
HP 6730b Laptop Solution.

On my HP 6730b the issue was that sound would work just fine via headphones but not over the internal speakers.  The following two options resolved my issue:

1. options snd-hda-intel enable_msi=1
2. options snd-hda-intel model=laptop

I hope that saves someone else some pain.

Wayne

---

### Post by iseeclouds on 2009-02-16
> **davidkyn said:**
> SO you then issue the command: 
Code:
zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
i get stuck here, or maybe i'm doing something wrong. i get this error in a terminal:
gzip: /usr/share/doc/alsa-base/driver/ALSA-configuration.txt.gz: No such file or directory
/usr/share/doc/alsa-base/driver/ALSA-configuration.txt.gz: No such file or directory

---

### Post by gumbeto on 2009-02-17
I have a Dell Studio XPS 16 and everything uBeer said also applies to me:

> Output head -n 1 /proc/asound/card0/codec*:
Codec: IDT 92HD73C1X5

zless ALSA-Configuration gave:
STAC92HD73*

So I added 'option snd-hda-intel model=dell-m6'
Rebooted and magic!

It switches automagically on inserting jack, so no need for manual switching!
Thank you very much!!

I have the same coded, did the exact same thing and got the same perfect result.

Thanks a lot

---

### Post by kazuya on 2009-02-17
Hi all. For three days I struggled with the ALC663 Realtek sound  for my ASUS X83Vb on Ubuntu 8.04 64bit. Eventually, I gave up after trying most of this suggestion. 
My workaround was to install Ubuntu Intrepid 32bit. Then everything worked flawlessly including sound. I have not tested wireless yet; But sound works fine and I see the switch options.
 
Sound device is hda intel alsa i believe. So sound is solved for me.

---

### Post by zacattack on 2009-02-17
i have followed the direction to the T. i have an hp mini 1000 and have had no luck. the codec says IDT 92HD75B2X5. i have tried everything.

---

### Post by mumi on 2009-02-20
I also had similar problems with sound on both or nothing at all. I tryed different methods and nothing worked. Then i found a update script for the alsa driver. It solved all my problems :0)

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

i'am using Asus m50vn.

Good luck.

---

### Post by exjinn on 2009-02-20
Many, Many thanks! You just made my brand new Acer Aspire 6530 that much cooler.

---

### Post by EliteBlack on 2009-02-21
i get this message when i enter the code: zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz


Advanced Linux Sound Architecture - Driver
                ==========================================
                            Configuration guide


Kernel Configuration
====================

To enable ALSA support you need at least to build the kernel with
primary sound card support (CONFIG_SOUND).  Since ALSA can emulate OSS,
you don't have to choose any of the OSS modules.

Enable "OSS API emulation" (CONFIG_SND_OSSEMUL) and both OSS mixer and
PCM supports if you want to run OSS applications with ALSA.

If you want to support the WaveTable functionality on cards such as
SB Live! then you need to enable "Sequencer support"
(CONFIG_SND_SEQUENCER).

To make ALSA debug messages more verbose, enable the "Verbose printk"
and "Debug" options.  To check for memory leaks, turn on "Debug memory"
too.  "Debug detection" will add checks for the detection of cards.

---

### Post by Mac181 on 2009-02-21
Upgrading didnt solve it for me. It just doesnt want to play nice. That list of hardware simply doesnt include the Lenovo Ideapad.

---

### Post by iseeclouds on 2009-02-23
> $ head -n 1 /proc/asound/card0/codec*

==> /proc/asound/card0/codec#0 <==

Codec: Realtek ID 663



==> /proc/asound/card0/codec#1 <==

Codec: Generic 10de ID 6

when I search under "Module snd-hda-intel" I can't find any of those. Which one should I choose instead?


> $ sudo gedit /ect/modprobe.d/alsa-base

Unmatched element: citerefentry

Unmatched element: refentrytitle

Unmatched element: citerefentry

Unmatched element: refentrytitle



** (gedit:6566): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.


I get an empty text file and this error. When I try to save I get an error the file doesn't exist.

Anyone knows what I should do or what i'm doing wrong?

---

### Post by EliteBlack on 2009-02-23
well i have tried all the solutions i have seen for the vaio series and tried some other general ones...and it still doesn't work...i have a sony vaio VGN-NR140E and i have an alsa 262...please help...and i am a newb to linux...help me out...thank you

---

### Post by FellowPhx on 2009-02-25
> **EliteBlack said:**
> well i have tried all the solutions i have seen for the vaio series and tried some other general ones...and it still doesn't work...i have a sony vaio VGN-NR140E and i have an alsa 262...please help...and i am a newb to linux...help me out...thank you

I have an ALC262 and when I find it in the terminal it doesn't give me any useful info to add onto the options snd-hda-intel model=

this is what it says under my ALC262:

 ALC262
          fujitsu       Fujitsu Laptop
          hp-bpc        HP xw4400/6400/8400/9400 laptops
          hp-bpc-d7000  HP BPC D7000
          hp-tc-t5735   HP Thin Client T5735
          hp-rp5700     HP RP5700
          benq          Benq ED8
          benq-t31      Benq T31
          hippo         Hippo (ATI) with jack detection, Sony UX-90s
          hippo_1       Hippo (Benq) with jack detection
          sony-assamd   Sony ASSAMD
          ultra         Samsung Q1 Ultra Vista model
          lenovo-3000   Lenovo 3000 y410
          basic         fixed pin assignment w/o SPDIF
          auto          auto-config reading BIOS (default)


now what part of that do I tack onto options snd-hda-intel model=


Could use some help...

---

### Post by Incomming on 2009-02-25
Hello
I have the following problem:
when i type head -n 1 /proc/asound/card0/codec* I get Codec: Realtek ALC888
and  cat /proc/asound/modules -> snd_hda_intel
But when I try sudo gedit /ect/modprobe.d/alsa-base and try to edit the fileI get this massage: "Could not find the file /ect/modprobe.d/alsa-base."
Can someone help me to fix the headphones problem ?
Thanks

EDIT: this "gksu gedit /etc/modprobe.d/alsa-base" instead of "sudo gedit /ect/modprobe.d/alsa-base" worked.

---

### Post by iseeclouds on 2009-02-26
> **iseeclouds said:**
> when I search under "Module snd-hda-intel" I can't find any of those. Which one should I choose instead?



I get an empty text file and this error. When I try to save I get an error the file doesn't exist.

Anyone knows what I should do or what i'm doing wrong?
anyone, please??

---

### Post by FellowPhx on 2009-02-26
> **Incomming said:**
> Hello
I have the following problem:
when i type head -n 1 /proc/asound/card0/codec* I get Codec: Realtek ALC888
and  cat /proc/asound/modules -> snd_hda_intel
But when I try sudo gedit /ect/modprobe.d/alsa-base and try to edit the fileI get this massage: "Could not find the file /ect/modprobe.d/alsa-base."
Can someone help me to fix the headphones problem ?
Thanks

EDIT: this "gksu gedit /etc/modprobe.d/alsa-base" instead of "sudo gedit /ect/modprobe.d/alsa-base" worked.

change the ect to etc   I had the same problem

---

### Post by iseeclouds on 2009-02-27
ok, thanks. i can now edit the text file. but i still have this problem...
> $ head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 663

==> /proc/asound/card0/codec#1 <==
Codec: Generic 10de ID 6
when I search under "Module snd-hda-intel" I can't find any of those. Which one should I choose instead? i can't find the right one to make it work.

---

### Post by Mac181 on 2009-03-02
Bumpity bump smack. Seems alot of us in 8.10 with new laptops are having this trouble. Is it simply ALSA lacking our new hardware? Or would a 8.4 rollback be the answer to all our linux-related prayers?

---

### Post by iseeclouds on 2009-03-02
i have 8.04. so that's not really the problem for me.

---

### Post by gaixixon on 2009-03-02
I have two big problem unresolved with ubuntu 8.10 that is: loud speaker unmuted when mic jack plugin AND unable to connect to WPA wireless network! It keeps bumping asking for the paraphase :mad: and sometimes OO spreadsheet crash when openning Microsh!t Excel.. that's why I have to co-exist with Bill.

---

### Post by tommaso.tullo on 2009-03-03
Solved on my asus F3E -> lenovo

---

### Post by aniketvb on 2009-03-06
I have dell studio xps 13:
"head -n 1 /proc/asound/card0/codec*" gives me 
 ==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD73C1X5

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP7A HDMI


So I set the model=dell-m6 as someone did for his Studio XPS 16 laptop, but it doesnt work for me yet. I still get sound from both speakers and headphones. 

Has anyone had luck with Studio XPS 13 and this problem!?

---

### Post by aniketvb on 2009-03-19
Ok I solved this problem in my F10 install by compiling the latest alsa-driver from git and using model=dell-m6 . Will try it on Ubuntu later, it should work afaik.

---

### Post by aldimond on 2009-03-24
I have the headphone sense problem on my new computer, which has a VIA VT1708B codec.  When I read that people were using module-loading options to fix this problem I checked the kernel source and docs to see what was going on.  I found some things.

*TL;DR version: if you can't get headphone sense working and you have a VIA chip, or some other that nobody's reported as working in Ubuntu, headphone sense for your chip may not be supported in Ubuntu's kernel, or in Ubuntu's alsa-sources, yet.  It may be supported in a more recent version, though!*

First, the "model" option for snd-hda-intel only works for models within the codec you have (which you can find by **grep -i codec /proc/asound/card*N*/codec#***, where *N* is ALSA's index for your card, which is usually 0; you can use * for *N* to see all the codecs for all the cards).  So when you look at [the list of models]("http://lxr.linux.no/linux+v2.6.29/Documentation/sound/alsa/HD-Audio-Models.txt") don't choose one that's not under your codec, it won't do anything.

Second, Ubuntu's kernel, as of 8.10, is 2.6.27, which doesn't yet support headphone jack sense for VIA chips.  This support should be in kernels 2.6.28 and later.  Ubuntu's version of alsa-source (1.0.17) appears to be even older.  I don't really know much about git, though (it looks like development for all but new drivers happens in the kernel tree, but I don't know which kernel version corresponds to which ALSA version), so I downloaded the package, and support isn't in there.

---

### Post by aldimond on 2009-03-24
oops, double-posted (caused by browser forward-button navigation)... i am new to this, is there a way to delete?

---

### Post by nikislash on 2009-03-26
> **Pedhead said:**
> 

EDIT:: OK THE WINDOW HAS TEXT IN IT, ITS JUST HIDDEN!:lolflag: THANKS!!

how do you make it show the hidden text?

---

### Post by Marcham89 on 2009-04-07
-Deleted by User-

---

### Post by twitchor on 2009-04-13
Thx worked a treat:p):P

---

### Post by peterkim04 on 2009-04-13
Hey guys who have had their problems solved, I am still struggling.
Vaio NR10E I am running, 8.10 the sound problem still occurs even though the tick is put next to the headphone switch box.
when i try to follow the instruction above, when i type head -n 1/proc/asound/cardO/codec*, i get 'invalid number of lines'..
also sudo gedit/etc/modprobe.d/alsa-base i get 'command not found'. i can't even start to fix it. recently converted to linux after having enough of windows, maybe i did too soon.. 
it really annoys me that i can't use a simple headphone to work, please help. any help will be welcomed..
regards
pk

---

### Post by Clancy_s on 2009-04-15
> **peterkim04 said:**
> Hey guys who have had their problems solved, I am still struggling.
Vaio NR10E I am running, 8.10 the sound problem still occurs even though the tick is put next to the headphone switch box.
when i try to follow the instruction above, when i type head -n 1/proc/asound/cardO/codec*, i get 'invalid number of lines'..
also sudo gedit/etc/modprobe.d/alsa-base i get 'command not found'. i can't even start to fix it. recently converted to linux after having enough of windows, maybe i did too soon.. 
it really annoys me that i can't use a simple headphone to work, please help. any help will be welcomed..
regards
pk

I'm just going through the thread before trying this myself, so I'm no expert.  However if you posted the commands exactly as you tried them I can see 2 problems:

there should be a gap between the '1' and the '/' in the first command

and between the 'gedit' and the '/' in the second.  

I usually copy commands from the OP instead of retyping them, although in this case the second one has an error, with 'ect' instead of 'etc'

Since I was just looking

```
head -n 1 /proc/asound/card0/codec*
```

and 

```
sudo gedit /etc/modprobe.d/alsa-base
```

hth

---

### Post by oneiric on 2009-04-16
RE: Sal from Dec 2008, Realtek ALC889A audio on Macintosh, running Ubuntu 8.10

I have an iMac 20" (aluminum), on which I installed Ubuntu 8.10

Sound is working through the computer speakers, but there is no switching to headphones and there is no sound at all from the headphones when they are plugged into the computer.   My file /etc/modprobe.d/alsa-base
was modified, I added ```
options snd-hda-intel model=imac24
```

There is a red light coming out of the headphone jack too.  I read several forums that suggested different options to the end of my  /etc/modprobe.d/alsa-base, which I tried below, but none of these has fixed the lack of sound from headphones problem. 

options snd-hda-intel intel-mac-v1  [[broken my vol control]]
options snd-hda-intel model=intel-mac-v1  [[no sound]]
options snd-hda-intel model=intel-mac-v2 [[no sound]]]
options snd-hda-intel model=imac-intel [[no sound]]
options snd-hda-intel imac-intel	[[[[[broken my vol control]]]]
options snd-hda-intel intel-20    [[broken]]
options snd-hda-intel model=intel-20 [[no sound]]
options snd-hda-intel model=laptop (((broken, and shifted my screen to left)))
options snd-hda-intel model=3stack [[broken my vol control]]]
options snd-hda-intel model=auto [[no sound]]
options snd-hda-intel model=ref [[[[no sound]]]]]
options snd-hda-intel model=3stack-dig ((((no sound)))))


Has anyone resolved the problem for this Codec: Realtek ALC889A sound.  I am using the snd-hda-intel module.  By the way the sound works when running my Mac OS X partition, so I don't think its a hardware problem.  Also I have installed the latest Alsa 1.0.19.
Any solution for getting this to work in linux would be greatly appreciated !!!  




> **windsword said:**
> My system too works partially, no switching when I plug in the headphone.

when type:  head -n 1 /proc/asound/card0/codec*
I get: Codec: Realtek ALC889A

Under:  zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz 
I don't see an option for this Realtek ALC889A, 
so I tried: model=imac24 

I have a Macbook Pro running Xubuntu 8.10, please let me know if there is a work-around for this.

Thank you

// Sal 


options snd-hda-intel model=imac24

---

### Post by peterkim04 on 2009-04-17
SOLVED! thank you everybody for the help, just follow the steps, except changing /ect to /etc in one of the lines. thank you again

---

### Post by jward3010 on 2009-04-18
Thanks, this worked. I have a Sony Vaio VGN-N38Z/W. My Vaio uses a Realtek ALC262 chip. 

By adding
```
options snd-hda-intel model=**sony-assamd**
``` as a last line to "/etc/modeprobe.d/alsa-base.conf", I've solved the problem right after a restart.

---

### Post by jonny2040 on 2009-04-19
I got my headphones kinda working with this fix. I have a msi ms-1223 or pr201 laptop. I use the following option -

options snd-hda-intel model=medion

(some other models also work though)

Its enough to enable a switch to allow me to mute the speakers. Its manual but its enough to let me use linux on this laptop now so I'm happy.

Thanks,
Jonny

---

### Post by nautilusny on 2009-04-20
Acer EMachines E520 works with the following and the latest alsa-driver tarball. I tested this with Fedora 10 running 2.6.27.21-170.2.56.fc10.x86_64. 

options snd-hda-intel model=laptop

Thanks everyone!

---

### Post by Monkeyven on 2009-04-20
Thanks worked great
Running Ubuntu 8.10 on a Compaq tc4200 (2006 Hp tablet) with AD1981B codec
Code added:  options snd-hda-intel model=3stack

---

### Post by ilcontegis on 2009-04-24
I have alc889 on a vaio tt
Mic does not work and headphone does not make mute the speakers.

I added in /etc/modprobe.d/alsa-base.conf~ 
options snd-hda-intel model=vaio

But no changes

```
teo@teo:~$ head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC889

==> /proc/asound/card0/codec#2 <==
Codec: Intel G45 DEVCTG

```
If you can please help me.
Thank you very much

---

### Post by Saint_ on 2009-04-24
Yeah i'm having the exact same problem as oneiric, my computer speakers work fine (laptop), but when i plug my external speakers into my headphone jack, they don't output any sound. It works in windows 7 so im sure it's not a hardware problem. So far this is what i got from reading through this thread, only problem is neither one of those codecs are listed. Any ideas/suggestions/help are greatly appreaciated, thanks in advance.

saint@saint:~$ head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD71B7X

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

---

### Post by Tteddo on 2009-04-28
Just reporting that this worked for me on an Acer Aspire 5050. Adding the line 
> options snd-hda-intel model=acer-aspire
Worked for me.
The speakers do not turn off when you put the headphones in, but it was that way even in Windows.

---

### Post by hubriz on 2009-05-05
> **davidkyn said:**
> **SOLVED..**.Headphone & Speaker Issues:
Ussualy effect intel HDA sound cards...Sound comes out both fronts and headphones at same time!

My Solution for Ubuntu8.04.............**Basicaly you just want to add a switch to the volume controll!**
[IMG]http://i181.photobucket.com/albums/x30/davekyn/VolumeControl.png[/IMG][IMG]http://i181.photobucket.com/albums/x30/davekyn/Switch.png[/IMG]

Tell alsa which driver to use for your hda intel sound card. You do this by first looking at the output of 
Code:
head -n 1 /proc/asound/card0/codec*

Mine was:
Codec Realtek ALC888

SO you then issue the command: 
Code:
zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

Look for the subtitle "Module snd-hda-intel".
In this subsection look for the name of codec “you” aquired from the output above...Mine was Realtek ALC888...so after locating  the list for  “Module snd-hda-intel” I scrolled down further to find:

ALC883/888 then I looked at the options directly under and chose “_3stack-6ch_   3-jack 6
 channel” you may have to choose another option or experiment.

Important!!!!Now that you have an option what do you do with it.........1st you only take the part of it...that is the part directly under the listed codec...for me that is “_3stack-6ch_” and add it to the following line to get:
[U]
options snd-hda-intel model=3stack-6ch[/U]

Without the underline of course, so that it looks like:

options snd-hda-intel model=3stack-6ch

This is the line that you need to add to /etc/modprobe.d/alsa-base by doing the following:

For Ubuntu:
sudo gedit /ect/modprobe.d/alsa-base

When the new window opens, cut and paste the new line you have just made at the bottom of all the text, save and exit.

Restart and hopefully if you have not buggered up with the spacing as I did you should now have a SWITCH option in your “Volume Contol” found in the desktop panel.  Just deselect or select to switch between speakers of headphones as it should have been from the start.

HOW RIDICULOUS FOR something SO ESSENTIAL...TOOK ME ALL DAY TALKING TO MYSELF AND SEARCHING THE NET TO FIX. Oh yea..a special thanks to the guys at the Suse Forum as well :)

HOPEFULLY THIS WILL HELP SOMONE ELSE...I would say it was more a case with the module than it was ever with updating...but then again I dont know that much ecept what I have learnt today...........Persistance Pays I guess!:guitar:
[SIZE=4][COLOR=Navy]how about for **[COLOR=Red]_COMPAQ CQ40-340T_[/COLOR]**.. Anyone who has an idea or bright solutions, please..[/COLOR][/SIZE]

---

### Post by ouq77 on 2009-05-16
For my Fujitsu Amilo xi3650:

```
options snd-hda-intel model=haier-w66
```

Headphone switch has to be OFF (unticked)

---

### Post by NeonNomad on 2009-05-18
I had Upgraded to Jaunty and as a result internal speakers would not mute after my headphones were plugged.

Added: options snd-hda-intel model=3stack-6ch as described (my codec was also Realtek ALC888) and this worked a treat, thanks for the useful guide :D

---

### Post by bhagwad on 2009-05-21
This fix worked in Jaunty with a Sony VAIO VGN-NR498E. Had to choose the sony-assmd option. Also, the file was "alsa-base.conf" not just alsa-base.

Thanks a lot - don't know what I would have done without you!

---

### Post by Reggino on 2009-05-21
Thanks... I have been looking for hours for this.

Got NEC P570 working with 'jack-sensing' and all! using:

options snd-hda-intel model=targa-dig

Thanks again! :D

---

### Post by hubriz on 2009-05-24
I've got this problem solved for Compaq Presario CQ40 laptops. Stay or revert Ubuntu to Hardy Heron(8.04) if you're using Jaunty. That solves the problem for the meantime. Let's wait 9.04 will work on Compaq Laptops' sound chipsets.

---

### Post by ZeroCool69 on 2009-05-27
Frickin' awesome. Worked great after a few typos were corrected...

For newbies, be aware of:
/**etc**/modprobe.d/alsa-base**.conf**

The "etc" appears as "ect" in the original fix post
 
and

The ".conf" does not appear in the original fix post.

Other than that, should work great for you. Good luck!

---

### Post by cantinflasa on 2009-05-28
thank you very much... that was very useful for me... i've been looking for this solution for about 1 year... thanks!!

---

### Post by ricflomag on 2009-05-31
Acer Aspire 5050 owners, using Ubuntu 9.04 (Jaunty): the following will make your speakers, headphone and INTERNAL MICROPHONE work.
[LIST]
[*]press ALT + F2
[*]enter this command: > gksudo gedit /etc/modprobe.d/alsa-base.conf
[*]enter your password
[*]in the text editor that opens, paste this line (replacing the previous content, if the file is not blank):
   > options snd-hda-intel model=fujitsu-pi2515
(This is "fujitsu-pi2515", not "acer-aspire", because the later would not allow the internal microphone to work.)
[*]save and close
[*]restart your computer
[*]you'll have to edit your Volume Control settings to select the internal mic as a source. Some of the sliders settings won't be saved, but this is not a major problem.[/LIST]

Hope it helps.

---

### Post by AZChief1893 on 2009-05-31
Hey there all, I am an extreme beginner... not that that is established, I am trying to get my sound card to work on an HP mini 1010 I am using the netbook remix 9.04 and when i go to select the HDA ALSA option on the sound preferences below is the error that i receive....

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

any help would be greatly appreciated...

T

---

### Post by v04sva on 2009-06-12
I have a problem,  internal speakers would not mute after my headphones were plugged.

laptop hp Pavilion tx2525nr
Ubuntu 9.04 (amd 64)
codec: Realtec ALC268

I had try a lot of variable (hp, toshiba, 3stac, e.t.c. ) in string "options snd-hda-intel model = ... " but nothing didn't halp me

---

### Post by ricflomag on 2009-06-12
Hi v04sva,

You can try to install "linux-backports-modules-jaunty" (and revert your changes to "snd-hda-intel").

Ric.

---

### Post by gbrotos on 2009-06-12
What about Dell Inspiron 1410 - S66 ? I almost frustrated to find the model should I put at [U] options snd-hda-intel model=???????

[/U]Anyone can give me advice, before I'm surrender from Ubuntu?

regards,
gbrotos

> **davidkyn said:**
> **SOLVED..**.Headphone & Speaker Issues:
Ussualy effect intel HDA sound cards...Sound comes out both fronts and headphones at same time!

My Solution for Ubuntu8.04.............**Basicaly you just want to add a switch to the volume controll!**
[IMG]http://i181.photobucket.com/albums/x30/davekyn/VolumeControl.png[/IMG][IMG]http://i181.photobucket.com/albums/x30/davekyn/Switch.png[/IMG]

Tell alsa which driver to use for your hda intel sound card. You do this by first looking at the output of 
Code:
head -n 1 /proc/asound/card0/codec*

Mine was:
Codec Realtek ALC888

SO you then issue the command: 
Code:
zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

Look for the subtitle "Module snd-hda-intel".
In this subsection look for the name of codec “you” aquired from the output above...Mine was Realtek ALC888...so after locating  the list for  “Module snd-hda-intel” I scrolled down further to find:

ALC883/888 then I looked at the options directly under and chose “_3stack-6ch_   3-jack 6
 channel” you may have to choose another option or experiment.

Important!!!!Now that you have an option what do you do with it.........1st you only take the part of it...that is the part directly under the listed codec...for me that is “_3stack-6ch_” and add it to the following line to get:
[U]
options snd-hda-intel model=3stack-6ch[/U]

Without the underline of course, so that it looks like:

options snd-hda-intel model=3stack-6ch

This is the line that you need to add to /etc/modprobe.d/alsa-base by doing the following:

For Ubuntu:
sudo gedit /ect/modprobe.d/alsa-base

When the new window opens, cut and paste the new line you have just made at the bottom of all the text, save and exit.

Restart and hopefully if you have not buggered up with the spacing as I did you should now have a SWITCH option in your “Volume Contol” found in the desktop panel.  Just deselect or select to switch between speakers of headphones as it should have been from the start.

HOW RIDICULOUS FOR something SO ESSENTIAL...TOOK ME ALL DAY TALKING TO MYSELF AND SEARCHING THE NET TO FIX. Oh yea..a special thanks to the guys at the Suse Forum as well :)

HOPEFULLY THIS WILL HELP SOMONE ELSE...I would say it was more a case with the module than it was ever with updating...but then again I dont know that much ecept what I have learnt today...........Persistance Pays I guess!:guitar:

---

### Post by endersgame09 on 2009-06-13
> **Pedhead said:**
> It looks like this is heading me in the right direction. However, when I enter the command-

sudo gedit /ect/modprobe.d/alsa.base

I open a window named- 

*alsa.base (ect/modprobe.d) - gedit

this window is completely blank. But I tried entering the text anyways-

options snd-hda-intel model=vaio

And I get an error message reading-

Could not save the file [i]/ect/modprobe.d/alsa.base[i] unexpected error, file not found

So I close out that window and I have an error message on my terminal, basically saying the same thing... 

I would think that file would be named the same in Mint as in Ubuntu, but maybe I am wrong..? Maybe I am missing something?

EDIT:: OK THE WINDOW HAS TEXT IN IT, ITS JUST HIDDEN!:lolflag: THANKS!!ok it seems im at exactly this point with the same problem - anyone want to help the newb out :) please ;)

---

### Post by ricflomag on 2009-06-13
Note that the correct filename is ```
/etc/modprobe.d/alsa-base.conf
``` instead of "/etc/modprobe.d/alsa.base" (there's a minus sign between "alsa" and "base", not a dot. It's also recommendend to use the ".conf" extension.

Ric.

---

### Post by endersgame09 on 2009-06-13
> **ricflomag said:**
> Note that the correct filename is ```
/etc/modprobe.d/alsa-base.conf
``` instead of "/etc/modprobe.d/alsa.base" (there's a minus sign between "alsa" and "base", not a dot. It's also recommendend to use the ".conf" extension.

Ric.
thanks ricflomag, when i try and save this file i get a perrmisions error - how do you get permission for root files?

---

### Post by ricflomag on 2009-06-14
Press ALT+F2 and type the following command:```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
This will open the text editor with root permissions.
Hope it helps.
Ric.

---

### Post by endersgame09 on 2009-06-15
thanks for that mate

---

### Post by marin.r on 2009-06-15
Hi there :)

I'm trying to fix a friend of mine's Asus F3E, with Ubuntu 9.04 installed, and despite there are already two users reporting that "lenovo" option works, it doesn't change nothing for me (with "microphone" checkbox either way - selected/not selected).
The F3E has 660-VD codec, and I tried all the options listed there, too, still - didn't help.
Alsa version on the machine - 1.0.18.

Should I try to downgrade to 8.10 ? Because I think both success reports are on 8.10 (based on post dates)? Or install newer/older Alsa ?

I'd be very grateful if someone with such machine shares his (working) configuration, too :)

EDIT:
So now I can confirm that the line:
> options snd-hda-intel enable=1 index=0 model=lenovo
works fine with the ASUS F3E, ALC660-VD :)

---

### Post by chrisgaffrey on 2009-06-17
For my Toshiba Satellite A135-S4527 with ALC861VD I had to use:

options snd-hda-intel model=auto

This enabled the headphone switch in the mixer and gave me headphone functionality out of the front jack. Only problem however is that the sound still plays out of the speakers. I tried simply adjusting my mixer, but it turns out that the speaker output and headphone output seem to be intertwined. Anyone know if there is a way to fix that?

---

### Post by curson on 2009-06-23
As anyone had any luck with a Sony Vaio VGC-JS2E series? It's an all-in-one PC. Sounds work fine, but headphones plugged in don't switch the main speakers off.

Tried with: vaio, sony-assmd, hippo, imac24 options...

Looking for answers :)

---

### Post by bhagwad on 2009-06-23
> **curson said:**
> As anyone had any luck with a Sony Vaio VGC-JS2E series? It's an all-in-one PC. Sounds work fine, but headphones plugged in don't switch the main speakers off.

Tried with: vaio, sony-assmd, hippo, imac24 options...

Looking for answers :)

This may be off, but the file name is "alsa-base.conf" - not just "alsa-base". Maybe it'll work if you try that.

---

### Post by curson on 2009-06-23
> **bhagwad said:**
> This may be off, but the file name is "alsa-base.conf" - not just "alsa-base". Maybe it'll work if you try that.

Thanks for the precision, but I'm in fact editing the right file: alsa-base.conf. 

Wish it was just that in fact :P

---

### Post by dootzky on 2009-06-29
great stuff man, thanks!!! WORKED FOR ME!! :)

---

### Post by grimanda on 2009-07-02
Hi... Just wanna share

I have Compaq CQ40-114AX AMD Turion X2 64bit, ATI Radeon, and ubuntu 9.04 for AMD 64bit

1. head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD71B7X

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

2. zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
and chose 

STAC92HD71B*
          ref           Reference board
          dell-m4-1     Dell desktops
          [COLOR="Red"][COLOR="Black"]**_dell-m4-2     Dell desktops_**[/COLOR][/COLOR]
since mine is IDT 92HD71B7X. I've chosen m4-1 previously, but it was failed for some test.

3. I executed
sudo vi /etc/modprobe.d/alsa-base.conf

2. Added 
options snd-hda-intel model=dell-m4-2 

3. Then restarted alsa
- killall pulseaudio
- sudo alsa force-reload
- pulseaudio -D

And it works now.., but still don't know any defect available
HTH

Regards.

---

### Post by Zebra_ on 2009-07-04
options snd-hda-intel model=sony-assamd on the end of /etc/modprobe.d/alsa-base.conf worked for my Sony VAIO VGN-NS255J in Jaunty (9.04)

---

### Post by Dmck23 on 2009-07-04
Hi I'm having the same problem with my Sony Vaio PCG-7144m running Ubuntu 9.04. I have the switch option in the sound menu and it does switch the sound on and off the headphones, but the problem is the sound will continue playing out of the main speakers regardless.

Any help will be greatly appreciated.

---

### Post by andredurao on 2009-07-07
Thanks also helped me 2 things to add
it doesnt need to restart to test if it's working

in my G50vt-x5

I needed to do this:

sudo gedit /etc/modprobe.d/alsa-base.conf
*add line:*
options snd-hda-intel model=asus-mode3

sudo /etc/init.d/alsa-utils restart
sudo alsa force-reload

---

### Post by curson on 2009-07-08
> **Zebra_ said:**
> options snd-hda-intel model=sony-assamd on the end of /etc/modprobe.d/alsa-base.conf worked for my Sony VAIO VGN-NS255J in Jaunty (9.04)

This doesn't solve the problem for me, on VGC-JS2E and Jaunty.
I've run out of options, tried pretty much all of them with no success... I will hope for a "change" in the future release of Alsa, don't know what to do next.

---

### Post by snu on 2009-07-08
> **ricflomag said:**
> Acer Aspire 5050 owners, using Ubuntu 9.04 (Jaunty): the following will make your speakers, headphone and INTERNAL MICROPHONE work.
[LIST]
[*]press ALT + F2
[*]enter this command: 
[*]enter your password
[*]in the text editor that opens, paste this line (replacing the previous content, if the file is not blank):
   
(This is "fujitsu-pi2515", not "acer-aspire", because the later would not allow the internal microphone to work.)
[*]save and close
[*]restart your computer
[*]you'll have to edit your Volume Control settings to select the internal mic as a source. Some of the sliders settings won't be saved, but this is not a major problem.[/LIST]

Hope it helps.


i tried this with my acer aspire 4935G - didn't help at all (i thoought maybe it works for other aspire too).

what worked for me, however:

ticking all volume controls for HDA Intel (Alsa Mixer) and checking if one fader turns up the headphone volume.
and it worked - "surround" controls the headphone plug volume, "front" the volume for the integrated speakers.
couldn't find a way to automatically turn off speakers when headphones are pluged in, tho.

---

### Post by biyouboogie on 2009-07-08
I still can not get mine to work.  
I have an Acer Aspire 6920, and it has Realtek ALC889 which is NOT listed.
I tried using model=acer, model=acer-aspire, and several 3stack-6ch.  None of them worked.  Is the ALC889 that much different from the ALC888 that these would not work?  It is a bit frustrating, because if I connect a docking station to the system, it finds those devices, and by default the sound will work.  I don't want to have to carry this docking station around with me.  :confused:

Any suggestions?

---

### Post by biyouboogie on 2009-07-11
For anyone else who has an Acer Aspire 69XX, I got my sound working using the following procedure.




Step 1: Open Terminal from "Applications->Accessories->
Terminal"  (I acually prefer Guake.)

Step 2: Run the following commands (copy/paste each command into the Terminal and then hit <enter>)

sudo gedit /etc/modprobe.d/alsa-base.conf

Add these 2 lines to the end of the alsa-base.conf file:

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

If those alsa-base.conf options don't work, please try these 2 lines instead:

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer-aspire

If it still does not work, you can try upgrading alsa to v1.0.19 using this link:

[http://monespaceperso.org/blog-en/2009/02/10/acer-aspire-6920-no-sound-on-ubuntu-810-upgrade-of-alsa/](http://monespaceperso.org/blog-en/2009/02/10/acer-aspire-6920-no-sound-on-ubuntu-810-upgrade-of-alsa/)

Don't forget to reboot your pc after every change you make on the /etc/modprobe.d/alsa-base.conf file.

For me, the very first step worked.  Step 2 wasn't necessary.  

P.S.  I got this procedure from a Google questions/answers forum... NOT from an Ubuntu forum.  Go figure!

I LOVE MY UBUNTU.... even when the sound wasn't working.  :))

---

### Post by CyberConan on 2009-07-15
My mainboard is ASUS P5QC.

Codec: Realtek ALC1200

Better option I found is model=targa-dig.

Now I can mute all channels except Front and switch between Front/Headphone clicking in kmix on Headphone "mute" option. :p

---

### Post by MasteRPenguiN on 2009-08-04
Hi all!

I had the same problem on my Ubuntu 9.04, and my card is ALC1200. Adding 

> options snd-hda-intel model=haier-w66

Was not enough. So i opened volume control and choosed Realtek ALC1200 from the combobox at the top. Now just disable PCM-2 output and it just works!

P.S. Before fixing this i have problems with launching Amarok since the last update... But Amarok somehow began to work too! :popcorn:

---

### Post by The Thug on 2009-09-02
Thanks very much.

I can eventually listen to music on my laptop without disturbing my co-workers !

---

### Post by richwillal on 2009-09-06
I really appreciate the detail in your post.  Configuring Alsa now makes sense.

I thought I'd post the stats on the card I was working on in case it helps someone else.

Laptop: HP HDX9300
Codec: STAC9271D
Module: snd-hda-intel
Jacks:
Rear: Front, Center/Sub, Side, Rear
Front: Mic, Headphone 1, Headphone 2

Working options in /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=5stack position_fix=0 probe_mask=-1 bdl_pos_adj=-1 enable=yes

Results:
----------------------
Currently, I have 5.1 speakers attached to the Front, Center/Sub and Rear connectors. All work correctly.

=> Laptop speakers work when the checkbox "Line in as Output" is checked.

Unchecking that checkbox leaves me with external speakers which works great when docked.

Headphone jack 1 does not work, but plugging headphones into headphone jack 2 works and mutes other outputs correctly.

The jacks on the rear of the laptop do appear to be mixed up, so I had to fumble with them a little to get all the individual volume controls working as intended.

HTH: I've found very few references for this laptop configuration running Linux.

Rich

---

### Post by joerik on 2009-09-15
Reaction #76 by Incomming worked for me on Sony Vaio VGN-NS11S with Realtek ALC262 using:

"gksu gedit /etc/modprobe.d/alsa-base" instead of "sudo gedit /ect/modprobe.d/alsa-base".

model=sony-assamd

Thanks everyone.

---

### Post by magic-neophyte on 2009-10-16
For me (Jaunty 9.04) on Sony Vaio VGN - NS11 Z, recording and playback were fine when I added the following line:

# Enable microphone and other features
options snd-hda-intel model=toshiba-s06

to the bottom of

/etc/modprobe.d/alsa-base.conf

And then reboot the computer and recheck all the settings in Volume Preferences. Set Options > Input Source to: Int Dmic

Apparently the internal chipsets are most similar to Toshiba's s06 model.


magic neophyte

---

### Post by wabbalee on 2009-10-16
Thanks to OP.

---

### Post by curson on 2009-10-29
Just FYI, the update to 9.10 Karmic Koala solved the problem for me on a Sony Vaio VGC series, with a "vanilla" configuration, nothing special done ;)

Loving this version already :D

---

### Post by LuK_green on 2009-10-30
I've got an ASUS F3Ke laptop with a Realtek ALC660-VD chip. In times of 9.04 Jaunty Jackalope the line "options snd-hda-intel model=lenovo" worked good, but not now. In 9.10 Karmic Koala everything goes as usual by default. I mean speakers sound along with headphones. So I've added the options-lenovo line that helped me much in times of 9.04 Jaunty Jackalope. In the new "Sound Preferences" dialog, in the "Output" tab I switched to "Analog Headphones" from "Analog Output". Speakers muted, but the sound from headphones was so faint, so I could hardly hear it =((( Please help.

---

### Post by LuK_green on 2009-10-31
Solved. The trouble was that now, in 9.10 Karmic Koala, it is possible to regulate channel volumes only through console alsamixer app.

---

### Post by fenrir12 on 2009-11-02
It took me a while to find, but with a STAC9205 card in a Gateway M-series running Karmic, these steps got me sound in my headphones!

[http://blog.wessendorf.org/software/headphones-with-ubuntu-904-and-gateway-t-6345u/comment-page-2/#comment-3219](http://blog.wessendorf.org/software/headphones-with-ubuntu-904-and-gateway-t-6345u/comment-page-2/#comment-3219)

---

### Post by XProflmfao on 2009-11-07
> **Pedhead said:**
> It looks like this is heading me in the right direction. However, when I enter the command-

sudo gedit /ect/modprobe.d/alsa.base

I open a window named- 

*alsa.base (ect/modprobe.d) - gedit

this window is completely blank. But I tried entering the text anyways-

options snd-hda-intel model=vaio

And I get an error message reading-

Could not save the file [i]/ect/modprobe.d/alsa.base[i] unexpected error, file not found

So I close out that window and I have an error message on my terminal, basically saying the same thing... 

I would think that file would be named the same in Mint as in Ubuntu, but maybe I am wrong..? Maybe I am missing something?

EDIT:: OK THE WINDOW HAS TEXT IN IT, ITS JUST HIDDEN!:lolflag: THANKS!!
How do you  make it show the hidden text? Because I've been searching for a while on Gedit and I still haven't found the solution to show it. Gosh, I'm so close to finally solving the biggest problem on my computer but this step just ruins everything! :(

---

### Post by Marc Di Pinto on 2010-03-09
I have a Toshiba Satellite A135-S2276... Could anyone explain to me what to do?
I'm new to Linux. I'm using Ubuntu 9.10

---

### Post by fabian.g on 2010-03-11
Hello everyone. I have the same problem. Speakers don't go quiet, when i plug in my headphones.

I have an **ASUS X5DAD Notebook**. The Soundcard is:
[B]cat /proc/asound/cards
0 [SB ]: HDA-Intel - HDA ATI SB HDA ATI SB at 0xfbcf4000 irq 16
and the codec is:
[/B] [B]cat /proc/asound/card0/codec#0
Codec: VIA VT1708S[/B] ...

The codec is NOT listed in **HD-Audio-Models.txt**  which I guess is not good ;-) The card is working though (I hear sound). So it is after all supported in one way or another. The speaker-headphone problem remains, though.

I tried adding **options snd-hda-intel model=*****  to the [B]/etc/modprobe.d/alsa-base.conf file

[/B]For *** (model name) I tried a hundred different combinations: auto, laptop-automute, 3stack, asus, targa-dig, ...

If anyone has a solution, that would be really, really great!

Best regards

---

### Post by pichagi on 2010-04-25
> **chriskin said:**
> well the easier way
download alsamixergui and configure everything
easy living :D

Just wanted to say you're awesome dude!  Been looking for a fix to this problem everywhere.  Tried pretty much almost everything. I added a line at the end of /etc/modprobe.d/alsa-base, changed the options and I even compiled the latest version of alsa...  Installed alssamixergui through the synaptic package manager in Mint 8, turned on head jack sense and voila!  worked like a charm! :P Did this on my Hp nc8000 laptop

these are my settings 

lspci
```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:0d.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5007G Wireless Network Adapter (rev 01)

```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by hamid.afshar on 2011-07-13
Thanks buddy,

awsome help

---

### Post by andender on 2012-01-03
I had a similar issue with my Gateway 3040GZ Notebook.  Sound played fine when Windows was on, no sound after installing Ubuntu 11.10.  After searching and searching the internet, i installed the Gnome ALSA Mixer and the Pulse Audio Volume Control.  Now I'm not sure if installing these made any difference, however I thought sure I had tried the same settings with the alsamixer.

Solution:
While playing music, I unchecked both "Headphone Jack Sense" and "External Amplifier" and sound started working.

---

### Post by IcemanBG on 2012-12-27
Dude first tnx for awesome help,

Second one usefull thing for everyone who have HP Pavillion dv6 series ..use trick with "model=hp-dv5" ..It works.For other people should gonna be hopeful (just dont complicate things :) and u will success)  :

1. skip  this command "head -n 1 /proc/asound/card0/codec*" it can confuse u
2.type this in terminal aplay -l
3.from the right side ull see ur codec model (in my case it was STAC92xx Digital [STAC92xx Digital])
4. now type this command in terminal zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz

5.now just find ur codec model in the list 
6.open new terminal tab and type this command sudo gedit /etc/modprobe.d/alsa-base.conf
7. try to find line "options snd_hda_intel model=hp-dv5" ,change model value according ur codec model...try all models from the list in model`s subsection  from HD-Audio-Models.txt.gz document  if u dont know what u should use,after every change u have to restart ur lap top

I hope this will help for someone ;) ):P

---

