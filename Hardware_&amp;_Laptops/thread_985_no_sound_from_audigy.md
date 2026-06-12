---
title: "no sound from audigy"
date: 2004-10-17
forum: Hardware &amp; Laptops
---

### Post by dwight on 2004-10-17
Nothing special. Just can't get any sound from my audigy card. It works just fine is SuSE, but not in Ubuntu yet. So I hope this is where you come in and help me change that :wink: .
I think that the card is located just fine as it is listed in the devices tool &amp; I can change the mixer settings for the card also. However if I try to play a mp3 or (or any other sound file) then regardless of the program (xmms, totem, mpg123) I just get an error message and no sound :cry: 
So... Any ideas. It's probably something really easy but I just don't know what it could be. In SuSE I would use alsaconf, but, alas, no such thing in Ubuntu (me thinks).
Thanks

---

### Post by jimi on 2004-10-18
same problem here
someone told me to sudo apt-get install alsa-oss

so oss emulation in gnome works with alsa 

but i cant try for now, CD install process crash :/

let me know if it works =)

---

### Post by dwight on 2004-10-18
Well. Installed alsa-oss but no change. Maybe it has something to do with the fact that I have Ubuntu WW RC1 installed. As you know.. RC=find the bugs and report back. So maybe this will be fixed when the offical release comes out. Should be quite soon.

---

### Post by im_ka on 2004-10-18
[quote=dwight] I just get an error message and no sound :cry: [/quote]

what's the error message?

---

### Post by Bas on 2004-10-18
Hi all, I got the same problem.

I've already tried the pci=noacpi ( I got this from the other thread with the Dell laptop, dunno if this also works for desktops  ) option during boot sequence, but no results.

But when I open the volume control I got 4 sound devices.
For all I know, I only got 2.

Realtek ALC655 rev 0 [OSS Mixer]
TriTech TR28602 [OSS Mixer]
Intel 82801DB-ICH4 [Alsa Mixer]
Sound Blaster Audigy [Alsa Mixer]

I know I got the bottem 2, but I don't know what/where the other 2 are.

modprobe sndemu10k1       didn't give any errors

sudo /etc/init.d/alsa restart     gave 2 OK's  ( Storing and Restoring )


I'll also post my lsmod : 

Module                  Size  Used by
proc_intf               3968  0
cpufreq_powersave       2048  0
cpufreq_userspace       5336  0
freq_table              4356  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  364
af_packet              20872  2
e100                   30208  0
eepro100               28300  0
mii                     4864  2 e100,eepro100
ohci1394               32004  0
ieee1394              100536  1 ohci1394
emu10k1_gp              3840  0
snd_emu10k1            80776  4
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9120  1 snd_emu10k1
tulip                  42528  0
crc32                   4608  1 tulip
snd_intel8x0           33068  5
snd_ac97_codec         59268  2 snd_emu10k1,snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  6 snd_pcm_oss
snd_pcm                85540  3 snd_emu10k1,snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  3 snd_emu10k1,snd_intel8x0,snd_pcm
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  2 snd_emu10k1,snd_mpu401_uart
snd_seq_device          7944  2 snd_emu10k1,snd_rawmidi
snd                    50660  20 snd_emu10k1,snd_util_mem,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  6 snd
hw_random               5652  0
ehci_hcd               27780  0
uhci_hcd               29328  0
usbcore               104292  4 ehci_hcd,uhci_hcd
pciehp                 83948  0
shpchp                 87276  0
pci_hotplug            30640  2 pciehp,shpchp
intel_mch_agp          10000  0
intel_agp              20512  1
agpgart                31784  2 intel_mch_agp,intel_agp
analog                 10784  0
gameport                4736  3 emu10k1_gp,snd_intel8x0,analog
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
evdev                   9088  0
tsdev                   7168  0
mousedev               10124  1
psmouse                17800  0
reiserfs              207600  2
ide_generic             1664  0
ide_disk               16768  6
piix                   12576  1
pdc202xx_new           10012  1
ide_core              125272  5 ide_cd,ide_generic,ide_disk,piix,pdc202xx_new
unix                   25904  790
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb


If someone needs more info, please say so.

Thanks in Advance.

---

### Post by dwight on 2004-10-19
Well, what do you know...
I was in the process of writing to this thread the error messages from programs that should give sound( but don't), and surprise surprise - I managed to get xmms to play mp3-s  :) 
How? First I switched the output plugin to ALSA, then, in ALSA plugin configuration (in xmms) switched the audio device to Sound Blaster Audigy (hw:1,0) and the mixer to mixer card 1. And I have sound. 
However I still don't have any system sounds (and no error messages). Other programs don't produce sound as well
With mpg123 the error message is:
```

Playing MPEG stream from Beatles - Lucy In The Sky With Diamonds.mp3 ...
MPEG 1.0 layer III, 128 kbit/s, 44100 Hz joint-stereo
/dev/dsp&#58; No such device
Can't find a suitable libao driver. &#40;Is device in use?&#41;

```

I'm not an expert, but if I had to guess I would say that there's something amiss with the way the default sound device is set up. The audigy card doesn't seem to be the default device for whatever reason. So where can I change that? And if my guess is wrong, what's the way to rectify this problem? Well, at least now i can listen to mp3's while looking for an answer :wink:

---

### Post by Bas on 2004-10-20
Hi Dwight,

I'm using my onboard soundcard ATM, cause I can't seem to get my audigy working properly.
I used the ALSA setting with HW 1,0 and 1.3 but both with no results.

A few mins ago I visited Distrowatch and found out that the official release of Ubuntu was a fact.

Let's just hope they got the support for audigy ready ( By this I mean easier installable ) with the final version.

---

### Post by dwight on 2004-10-20
Ok. I seem to have found some kind of a solution. Don't know if it will work for anyone else but I now have sound from **mpg123** and system sounds are also audible. 
I was just messing around with **mpg123** and I found out that it started playing with this command ```
mpg123 -a /dev/audio1 *.mp3
```
If I didn't pass the **-a** option it would moan about device /dev/dsp not being ready. So here is what i did:
```
root@ubuntu&#58;~ # cd /dev
root@ubuntu&#58;/dev # mv dsp /home/backup/   
root@ubuntu&#58;/dev # ln -s audio1 dsp

```
i.e. I created a symbolic link **dsp** instead of a device **dsp**.  :) 
I hope that having done this doesn't  mess anything else up. 

Before I accidentaly found this "solution" I searched around quite a bit (with no useful results regarding solving the problem) and found that this no sound issue seems to be quite common with the 2.6.8 kernel. So this doesn't seem to be an exclusive Ubuntu issue.

---

### Post by CowPie on 2004-12-04
[QUOTE=dwight]Ok. I seem to have found some kind of a solution. Don't know if it will work for anyone else but I now have sound from **mpg123** and system sounds are also audible. 
I was just messing around with **mpg123** and I found out that it started playing with this command ```
mpg123 -a /dev/audio1 *.mp3
```
If I didn't pass the **-a** option it would moan about device /dev/dsp not being ready. So here is what i did:
```
root@ubuntu:~ # cd /dev
root@ubuntu:/dev # mv dsp /home/backup/   
root@ubuntu:/dev # ln -s audio1 dsp

```
i.e. I created a symbolic link **dsp** instead of a device **dsp**.  :) 
I hope that having done this doesn't  mess anything else up. 

Before I accidentaly found this "solution" I searched around quite a bit (with no useful results regarding solving the problem) and found that this no sound issue seems to be quite common with the 2.6.8 kernel. So this doesn't seem to be an exclusive Ubuntu issue.[/QUOTE]

Well this worked.

I KDE, I would go to the sound options and choose Device: hw1,0 .

So I guess htis is similar to Gnome's way :)

Sound is pretty bad quality though oh well

(BTW I have a soundblaster live! emu10k1, not audigy.  looks like a zillion modules loaded for it though, no idea if oss are alsa)

---

### Post by Prymalfury on 2007-09-14
I was just wondering if Feisty Fawn had a fix for the audigy problem. I have Fedora on a dual boot, and the sound is fine. Feisty's sound is really horrible, and I was wondering if they had a fix for it yet since it's been three years?

---

### Post by Rekoil on 2007-09-20
I also get this problem. Sound is fine in Debian but sounds horrible in Ubuntu. Any ideas?

My card is an SB Audigy emu10k1 driver is being used.

---

### Post by feathersk on 2007-11-05
I also have the terrible sound issue on the SB Audigy1 on ubuntu Feisty Fawn. A description of the terrible sound is as follows:

1. Sounds like static interference
2. Music sounds somewhat muted
3. Vioces sound fairly quiet

These three points all occur at the same time when you would play a music file direct from CD, or from the Harddrive as mpeg layer format.

During the course of the near future I will update to ubuntu 7.10 and report back on the findings. Upgrade may very well be the case of resolution.

---

### Post by laph on 2007-11-27
For 7.10, AUdigy sounds GREAT.  Only thing is u want to make sure in Volume control-alsa mixer (dbl click speaker icon in top right system bar) under switches you unclick Digital audio jack if you don't use digital. =D

---

### Post by lordfrikk on 2008-04-09
Hi, I just installed Gutsy Gibbon yesterday and been having problems with Audigy as well. Hopefully this will work!

---

### Post by tshannon on 2008-04-09
Yeah having trouble with Hardy as well.

---

