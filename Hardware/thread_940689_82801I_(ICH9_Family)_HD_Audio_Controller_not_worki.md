---
title: "82801I (ICH9 Family) HD Audio Controller not working"
date: 2008-10-07
forum: Hardware
---

### Post by smaring on 2008-10-07
I am on an HP Pavilion dv7 running Ubuntu 8.10 (intrepid) kernel 2.6.27-5-generic x86_64

I hear my soundcard play the quick drum beats on the Ubuntu login screen, but it starts playing them REALLY loud and longer then usual, then progressively steps down in volume about every 5 seconds until all I hear from then on is a continuous very low beat in the background that never stops.

I grabbed a wav file off the internet and tried to run it and got:
# aplay -v familyguy1.wav
aplay: test_wavefile:782: can't play WAVE-file format 0x0055 which is not PCM or FLOAT encoded

my alsa-info.sh output is here: [http://www.alsa-project.org/db/?f=a1fbc9d12fc8ac3ec787a285fde0d56a7035f974](http://www.alsa-project.org/db/?f=a1fbc9d12fc8ac3ec787a285fde0d56a7035f974)

I see a similar problem here, but I'm already on 1.0.17 and it still does not work:
[http://sourceforge.net/mailarchive/message.php?msg_id=200808130030.16058.LuHe%40gmx.at](http://sourceforge.net/mailarchive/message.php?msg_id=200808130030.16058.LuHe%40gmx.at)

I also tried compiling/installing 1.0.18rc2 and that didn't help matters either.

I tried a few snd_hda_intel "model" options, but none seemed to help.  Any thoughts?


Thanks,
Steve Maring

Even with no sound at the moment.  I think removing Vista off this thing was the right thing to do.  I lived with it for a week ... and it was a VERY long and painful week.

---

### Post by mbarak on 2008-10-07
i have the same problem
fixed it by adding irqpoll as a boot option
here's the launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424)

to add irqpoll as an option (permanently)
edit /boot/grub/menu.lst
find the line saying kopt = ...... 
and irqpoll to the end of it
run sudo update-grub
and voila

---

### Post by smaring on 2008-10-07
OH!  Bless you!  You're awesome!  I love you man!  **wipes a tear**

---

### Post by mbarak on 2008-10-07
lol thank you

---

### Post by gawan on 2008-10-17
I tried irqpoll, but I still don't hear anything, only while booting 20 times system speaker :(. 

I have ASUS M50VC 

```

$ lspci 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

$ lsmod | grep snd
snd_hda_intel         489264  3 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm


$ lshw -c multimedia 
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel


```

Does someone any idea?

---

### Post by nevcos on 2008-10-20
Same issue here.

Same audio chip in a Asus M50V with Ubuntu 8.04.

Can anyone know what happens?

In my case I have this interface's listed in Audio (System > Tools > Audio):

* PulseAudio server
* OSS
* ALSA
* HDA Generic

Neither interface works.


Thanks!

---

### Post by stego_s_aurus on 2008-11-28
Tons and tons and tons of searching later, I ran across the solution!

We have an ASUS M50VM that has an Intel Corporation 82801I (ICH9 Family) HD Audio Controller (Rev 03). Couldnt get it to work, went through the entire OpenSound reconfiguration, Did the irqpoll thing, And the snd-hda-intel enable_msi = 1. No Dice.

Just before I went to sleep last night, I found some Other settings by searching for "options snd-hda-intel"... and Someone else had some additional settings that I added to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

Did the edit, rebooted, and sure enough the lovely sound of drums!!!

Heres hoping this can help others from having to spend 8 hours looking for the info!!

-Stego

:KS:KS:KS

---

### Post by odim31 on 2008-11-29
hi every one,
 i have the same problem, on my laptop Asus X56v, with lspci | grep Audio i've obtaned:
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]



can any one help me.

---

### Post by ralph.p on 2008-11-29
> **stego_s_aurus said:**
> Tons and tons and tons of searching later, I ran across the solution!

We have an ASUS M50VM that has an Intel Corporation 82801I (ICH9 Family) HD Audio Controller (Rev 03). Couldnt get it to work, went through the entire OpenSound reconfiguration, Did the irqpoll thing, And the snd-hda-intel enable_msi = 1. No Dice.

Just before I went to sleep last night, I found some Other settings by searching for "options snd-hda-intel"... and Someone else had some additional settings that I added to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

Did the edit, rebooted, and sure enough the lovely sound of drums!!!

Heres hoping this can help others from having to spend 8 hours looking for the info!!

-Stego

:KS:KS:KS



I have a similiar sound problem (no sound, 8.10, HD audio). I'm not very familiar with Linux, can someone explain the irqpoll thing and this solution from the beginning? Thanks

my topic: [http://ubuntuforums.org/showthread.php?t=996694](http://ubuntuforums.org/showthread.php?t=996694)

---

### Post by odim31 on 2008-11-29
open a terminal;
write:
sudo gedit /etc/modprobe.d/alsa-base
give your password when asked;
it's normal that nothing is shown when you are writing your password;
a text document will open;
all you have to do is to past the three lines at the end of the text document;
and finaly reboot your system.

please after rebooting tell me if it works for you, because for me it doesn't.

---

### Post by odim31 on 2008-11-29
oh you must save the document before rebooting

---

### Post by ralph.p on 2008-11-29
unfortunately i still haven't any sound

when I try to add the irqpoll thing i get:
```
Warning: unknown mime-type for "/boot/grub/menu.lst" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"
```

---

### Post by casahoo on 2008-12-11
> **mbarak said:**
> i have the same problem
fixed it by adding irqpoll as a boot option
here's the launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424)

to add irqpoll as an option (permanently)
edit /boot/grub/menu.lst
find the line saying kopt = ...... 
and irqpoll to the end of it
run sudo update-grub
and voila

Bonjour,

j'ai le meme probleme, mais je n'ai pas trouve' la ligne kopt pour que je puisse "irqpoll".

Merci de me donner une explication.

---

### Post by kezeb on 2009-01-15
just cd to /etc/modprobe.d/alsa-base as root and add 
options snd-hda-intel model=3stack-dig   
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1      at the end and that should fix it, save and then restart, that's all!!!!!!!!!!!   enjoy

---

### Post by piva on 2009-04-04
It worked perfectly on my new HP dv4-1190br, thanks a lot kezeb.

---

### Post by xCoLeYs on 2009-04-19
> **stego_s_aurus said:**
> Tons and tons and tons of searching later, I ran across the solution!

We have an ASUS M50VM that has an Intel Corporation 82801I (ICH9 Family) HD Audio Controller (Rev 03). Couldnt get it to work, went through the entire OpenSound reconfiguration, Did the irqpoll thing, And the snd-hda-intel enable_msi = 1. No Dice.

Just before I went to sleep last night, I found some Other settings by searching for "options snd-hda-intel"... and Someone else had some additional settings that I added to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

Did the edit, rebooted, and sure enough the lovely sound of drums!!!

Heres hoping this can help others from having to spend 8 hours looking for the info!!

-Stego

:KS:KS:KS

OMG... Works for me too!! You are the bombbb!!!:popcorn: (I really thought, I'd never get it working... you complete me lol!)

---

### Post by xCoLeYs on 2009-04-21
EDIT: It seems to work, with all but headphones... in other words when I plug in the headphones it doesn't start playing through them :p

Currently trying to search for a fix, if anyone has any tips would be greatly appreciated... I know this driver isn't easy to configure probably will be a random fix like above :p

kudoss, and thanks in advanceee!!!

---

### Post by drasgard on 2009-04-24
OMG, finally I've got sound working on my Compaq Presario CQ20 116TU, thank you!

Simply added the following three lines to /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

---

### Post by SeanBlader on 2009-04-25
Those same alsa-base.conf settings don't seem to help on my Dell even though I have the same info showing up in the lspci

```

~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

And here's my aplay -l

```

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And lastly lshw

```

~$ sudo lshw -C multimedia
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
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

I've been through all the threads in the top searches for "82801I" in the forums and haven't found anything that works for my Dell Adamo.

---

### Post by smaring on 2009-04-30
I decided to kick things up a notch and try the real-time kernel.  Well, it turns out that the irqpoll kernel option is ignored in the rt kernel.  So, I tried the ...

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

mods and they worked like a charm!

Thanks for figuring that out Stego!

-Steve Maring

---

### Post by gangak on 2009-05-02
I had the same problem with ubuntu 8.10 with Compaq Presario CQ40. I was glad that I could solve it by adding these three magiz lines to /etc/modprobe.d/alsa-base. I was working alright till I upgraded to 9.04, jaunty. 


Now, with jaunty, even the garbled drum beat is not heard. I here some continueous garble on the arhone but total silence in the Built in speakers. i tried adding these three magic lines to /etc/modprobe.d/alsa-base, but nothing happened.

Can some one help?

---

### Post by petyr zekhtinsky on 2009-05-20
Hi, i had no sound on my Fujitsu Siemens Amilo Li 3710 with ubuntu 9.04 here`s my lspci output:

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


so adding these : 
> options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

at the bottom of the /etc/modprobe.d/alsa-base.conf file made sound work  for me.I also have a spdif  a headphone and a mic out so i`ll test them whenever i can and keep you guys posted.
Thanks :)

---

### Post by mkaut on 2009-07-13
> **stego_s_aurus said:**
> 
Just before I went to sleep last night, I found some Other settings by searching for "options snd-hda-intel"... and Someone else had some additional settings that I added to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

Did the edit, rebooted, and sure enough the lovely sound of drums!!!

-Stego


For the first, I trust you meant /etc/modprobe.d/alsa-base.conf (at least on my Xubuntu 9.04)?

Anyway, I have an HP 2530p laptop (with  "Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)" and it kind of worked for me, once I replaced "3stack-dig" by "laptop". I write kind-of, because now the speakers are ON all the time, even when I plug in headphones. (In other words, I get the sound both from speakers and from headphones.)

Any idea how to make Ubuntu behave in the standard way and switch the speakers off with headphones?

Thanks

Michal

---

### Post by klueze on 2009-08-23
> **gangak said:**
> I had the same problem with ubuntu 8.10 with Compaq Presario CQ40. I was glad that I could solve it by adding these three magiz lines to /etc/modprobe.d/alsa-base. I was working alright till I upgraded to 9.04, jaunty. 


Now, with jaunty, even the garbled drum beat is not heard. I here some continueous garble on the arhone but total silence in the Built in speakers. i tried adding these three magic lines to /etc/modprobe.d/alsa-base, but nothing happened.

Can some one help?

I have the same problem

The 3 magic line didnt work in 9.04

I havent try with irqroll because I dont really understand it

can someone write the detailed progress with irqroll

thx

---

### Post by louigi600 on 2009-09-12
I've a Fujitsu Esprimo Mobile with ICH9 chip-set running Ubuntu 9.0.4 Desktop.
Initially I was also unable to get anything out of my built-in microphone.
I fiddled around with System -> Preferences -> Sound settings and enables all the optional controls.

What got my microphone working was the sum of these 2 things:
Enabling the front microphone
Giving some front microphone boost

Everything else was left untouched as just after install (except that all updates were made).

Now I'm pretty sure that this will not work for all but before assuming that there is some driver bug or software incompatibility do checkout all audio settings ... even the ones that are not shown by default.

Good luck everybody 
David Rao

---

### Post by ade234uk on 2009-09-17
> **klueze said:**
> I have the same problem

The 3 magic line didnt work in 9.04

I havent try with irqroll because I dont really understand it

can someone write the detailed progress with irqroll

thx


If you still dont have this working, then last night I downloaded the ALPHA 5 of Ubuntu 9.10 and sound worked out of the box.

---

### Post by neel_ on 2009-09-20
Here is my experience:

- I am using Ubuntu 8.04.03 LTS on Acer 4736 (for software reasons cannot upgrade beyond 8.04)
- There is NO sound
- I tried with:

--- kopt=irqpoll 
--- entries in alsa-base using all possible values for "model"
options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1
--- reinstalled driver using alsa_setup.sh (one version is here [http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)) for 1.0.19 and 1.0.16

Nothing gives!!

Any suggestions?

Thanks in advance,
Neel.

---

### Post by neel_ on 2009-09-20
forgot to add, troubleshooted with:

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Any suggestions is welcome.

Thanks again,
Neel.

---

### Post by mhgsys on 2009-09-22
> **stego_s_aurus said:**
> Tons and tons and tons of searching later, I ran across the solution!

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

Heres hoping this can help others from having to spend 8 hours looking for the info!!

-Stego

:KS:KS:KS

I just wanted to thank you, it worked out great for me adding these options to the  /etc/modprobe.d/alsa-base.conf 
Saved me lot's of time!

:guitar:

---

### Post by chandan_raka on 2009-10-13
hi,

 I am also facing same issue. I have got one ASUS K50IJ. but not able to hear anything out of that sound driver

#lspci
Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller

lsmod | grep snd
snd_hda_codec_via      30500  1 
snd_hda_intel          29000  4 
snd_hda_codec          65376  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               8600  1 snd_hda_codec
snd_pcm                79960  3 snd_hda_intel,snd_hda_codec
snd_timer              22496  1 snd_pcm
snd                    65096  12 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore               7024  1 snd
snd_page_alloc          9216  2 snd_hda_intel,snd_pcm
[root@localhost ~]#

---

### Post by vitaediscimus on 2009-10-13
I just fixed the same problem as follows:

- in the file  /boot/grub/menu.lst, find the line saying "kopt = ..." and add "irqpoll" to the end of it

- run sudo update-grub

- in the file /etc/modprobe.d/alsa-base, add the following lines to the end:

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

- reboot

---

### Post by aliyousafzai on 2009-10-25
My menu.Ist is like this 

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=911b61bc-2e4a-491e-b077-433cd3caac6b ro

Dont know where to add irpoll

---

### Post by Jack Malmostoso on 2009-12-02
> **aliyousafzai said:**
> My menu.Ist is like this 

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=911b61bc-2e4a-491e-b077-433cd3caac6b ro

Dont know where to add irpoll

At the end of the last line, after "ro". Make sure the text is all on one line.

---

### Post by robsablah on 2009-12-05
thanks soooooooooooo much, i'd been missing my sound there


let the ubuntu times roll!:p

---

### Post by subh.arya on 2009-12-23
Hi,

I am unable to get sound off my brand new Dell Adamo even after following the modifications suggested in this forum. These are the lines I have added to /etc/modprobe.d/alsa-base.conf

```

#options snd-hda-intel model=dell-eq enable=1 index=0
#options snd-hda-intel enable_msi=1
#options snd-hda-intel single_cmd=1

```

I also tried auto and laptop in the model field but still I am unable to get it to work. Here is my sound-card related information:

```

$ sudo aplay -l
[sudo] password for subh: 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

 $lspci|grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

Please suggest.

Regards,
Subh

---

### Post by drasgard on 2009-12-24
Back in April I got my built in laptop speakers working by adding these lines:


```
options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1
```

Recently I upgraded to Karmic Koala and my sound issues came back again. Headphone jack works but built in speakers don't. Trying the same magic-3-line fix didn't help this time and even stopped the headphone jack sound from working too.

I have tried adding irqpoll to /boot/grub/menu.lst but it didn't help.

So, hoping someone can point me towards a solution that works on Ubuntu 9.10.

Specs:

Compaq Presario CQ20-116TU


```
# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```



```
# lspci|grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```



```
# cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1984A
Codec: LSI ID 1040
Codec: Intel G45 DEVCTG
```

Thanks in advance.

---

### Post by lubo777 on 2010-06-18
> **stego_s_aurus said:**
> Tons and tons and tons of searching later, I ran across the solution!

We have an ASUS M50VM that has an Intel Corporation 82801I (ICH9 Family) HD Audio Controller (Rev 03). Couldnt get it to work, went through the entire OpenSound reconfiguration, Did the irqpoll thing, And the snd-hda-intel enable_msi = 1. No Dice.

Just before I went to sleep last night, I found some Other settings by searching for "options snd-hda-intel"... and Someone else had some additional settings that I added to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

Did the edit, rebooted, and sure enough the lovely sound of drums!!!

Heres hoping this can help others from having to spend 8 hours looking for the info!!

-Stego

:KS:KS:KS

thanks dude! this fixed my problem with HP ProBook 5310m also! \\:D/
I'm posting the content of my alsa config just in case it can help somebody.

[QUOTE=/etc/modprobe.d/alsa.conf (Getoo user here)]

alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss
alias /dev/mixer snd-mixer-oss

#options snd-hda-intel model=hp-dv5 enable_msi=1 

# Set this to the correct number of cards.
# --- BEGIN: Generated by ALSACONF, do not edit. ---
# --- ALSACONF version 1.0.23 ---
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
# --- END: Generated by ALSACONF, do not edit. ---
options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1
[/QUOTE]

I haven't added the grub kernel option.

---

### Post by andreicristianpetcu on 2010-12-26
Ubuntu 10.10, headphones don't work
I tried the 3 magic lines from /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model both "3stack-dig" and "laptop" and no results. I rebooted after each change

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

sudo lshw -C multimedia
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
       resources: irq:47 memory:fdef4000-fdef7fff


any ideeas? Thanks

---

