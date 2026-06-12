---
title: "Unable to get sound working (Envy24 card)"
date: 2004-12-05
forum: Hardware &amp; Laptops
---

### Post by Ribs on 2004-12-05
Hi,

I'm currently migrating from Gentoo. After installing, I'm pretty happy (except that I think the installer formatted my second HD, which had a lot of stuff on I wanted  :-s ). However, I am totally unable to get sound working.

It's one of the few things that 'just worked' in Gentoo... The card should be working with the 'Envy24' driver in the kernel. Ubuntu was unable to detect the sound card, so didn't load the module (snd-ice1724). I load it manually with modprobe, but I'm unable to get any output from it. I even added it to the /etc/modules and rebooted. To which I get this error when I boot;
```
ice1724: No matching model found for ID 0xf2745f6
ice1724: Invalid EEPROM (size = 255)
ICE1724: probe of 0000:02:0f.0 failed with error -5
```The boot continues as normal. But obviously sound doesn't work. I have no idea what the above error message means, but I'm guessing it's the cause of the problem...

I cannot find any way to configure sound cards once the system is actually running.

Any ideas?

-Ribs.

---

### Post by gama on 2004-12-06
Same problem here. Could anybody help, please!

---

### Post by Daphoid on 2004-12-09
My problem is similar. However the card appears to be detected fine, it natively shows up in volume control as "M-Audio Revolution 7.1 ALSA Mixer" which it should I'm assuming. If I run "gnome-control-center" and go into Advanced I believe, then Multimedia System (gstreamer I believe) I've switched everything in there to ALSA, and also switched XMMS to ALSA...

When I hit play the song starts playing, no errors at all, but there's no sound at all... This is connected via COAX SPDIF, any solutions with regards to that?

- D

---

### Post by gama on 2004-12-09
Has any one got ice1724 to work successfully on a Debian/Debian-based distro?

---

### Post by Ribs on 2004-12-11
Hi,

Okay, I found a soultion, but it ain't pretty... Basically you have to upgrade to a 2.6.9 kernel to get sound working on my specific card, as it was only supported from 2.6.9 upwards.

There are currently two ways of doing this in Ubuntu. Making your own kernel, which is just a pain in the ass, or doing a partical upgrade to Hoary. I did the latter.

I basically changed my config to use Hoary, then I only upgraded the stuff I wanted. I upgraded to a 2.6.9 kernel, upgraded XChat, migrated to XOrg, Upgraded Firefox, and that was it. Synaptic has loads of updates ready to go, but I don't want them, for the simple fact that it *will* break at some point. Many users in #ubuntu on Freenode complain that thier desktop is broken with one thing or another.

So, do a partical switch to Hoary is my advice. I now have sound working.

Be warned. The drivers appear buggy at the moment. Sometimes the sound will be far too slow, sometimes far too quick. The pitch is totally wrong. I've not found a fix for this yet (2.6.10 kernel maybe?)

-Ribs.

---

### Post by Vendy on 2004-12-11
I'm having somewhat the same problem - though it's partially functioning. Basically, everything sounds like a burst of static - if I play a music file I know by heart, I can pick out the music in the background, but it's covered in a layer of static. The mixer controls in alsa, both the normal ones and the gnome-alsamixer control, don't do anything, whether I mute it or anything, it just stays staticed.

Looking around a bit I see a few topics elsewhere that say the Envy24 is hardware controlled for channel volume and such, and there's a package called envy24control that will let you control levels - I suspect the problem may be the levels are all at 100% and so the sound's clipping quite very badly. Can I use this "envy24control" package on Ubuntu, and if so, how would I go about it?

Now I'm a Complete Linux Newbie© although I'm certainly trying... so I don't quite yet know what the steps are to troubleshoot this problem, so any suggestions would be appreciated.

---

### Post by thelusiv on 2005-02-05
I also have a card that uses envy24control and need this to use it. How can I get this? Usually it is part of the alsa-utils but it is not included in Ubuntu's alsa-utils package. I have a M-Audio Audiophyle 2496 which uses alsa's snd-ice1712 driver. Ubuntu set up and configured this just find, loaded all the modules etc. but I can not mix the card without envy24control! I have looked through the packages and it seems it's just not available. What can I do?

---

### Post by thelusiv on 2005-02-06
OK, a friend helped me out on this one. Seems that the alsa-tools package hasn't made it into Debian yet. The reason seems to be that there are firmware loaders included and they're not sure about the legalities. See here for more info: [http://lists.debian.org/debian-mentors/2005/01/msg00386.html](http://lists.debian.org/debian-mentors/2005/01/msg00386.html)

Here's how I got it working:

add this line to /etc/apt/sources.list
deb-src [http://mentors.debian.net/debian/](http://mentors.debian.net/debian/) unstable main

then
apt-get update
apt-get build-dep alsa-tools
apt-get source alsa-tools
apt-get install fakeroot

i then realized that it had unpacked alsa-tools in ~/.gnome2/alsa-tools-1.0.8 - not sure why but oh well...
cd ~/.gnome2/alsa-tools-1.0.8/ 
dpkg-buildpackage -rfakeroot

then it makes a .deb in ~/.gnome2 and the binary for envy24control is in the envy24control directory. works just fine. good luck

---

### Post by charlesg3 on 2005-07-31
I am having similar issues, When I play a sound it comes out too fast / at the wrong pitch, but using an alsa mixer I can turn down the sound, what gives? I have an MAudio Audiophile 2496 (envy24) card based on the ice1712 chipset. Has anyone gotten this sound card to work?

---

### Post by thelusiv on 2005-07-31
The reason is that this card must take two channels of separate audio to work properly. If you play a mono (single channel) sound through it, it alternates putting samples on both channels instead of duplicating the sound on both channels (so the sound seems sped up). If you are playing directly out from ALSA this is what will happen. If you enable the sound server you shouldn't have this problem anymore, as esd will split mono sounds up into two channels before sending to the sound card. Unfortunately, some applications have trouble with esd...

---

### Post by charlesg3 on 2005-07-31
[QUOTE=thelusiv]The reason is that this card must take two channels of separate audio to work properly. If you play a mono (single channel) sound through it, it alternates putting samples on both channels instead of duplicating the sound on both channels (so the sound seems sped up)...[/QUOTE]

I have been playing stereo mp3's through beep-media-player and receive the same incorrect-pitch output.

---

### Post by thelusiv on 2005-07-31
[QUOTE=charlesg3]I have been playing stereo mp3's through beep-media-player and receive the same incorrect-pitch output.[/QUOTE]
That's strange...what kind of card do you have?

---

### Post by charlesg3 on 2005-07-31
M-Audio Audiophile 2496

---

### Post by thelusiv on 2005-08-03
Oh yeah, I remembered what causes that. You need envy24control - a clone of the control program that comes with the card from M-Audio's drivers. These cards have an internal master clock rate that you probably need to reset. I have mine set on 44100 Hz. The default is probably set at 22050 Hz. Follow my instructions above on how to get alsa-tools. Once you've compiled it enter the envy24control directory and run the executable in there.

Go to the "Hardware Settings" tab. Uncheck "Locked" under "Rate State". Now change the sample rate under "Master Clock". You can lock it back if you want.

Are you running Warty or Hoary?

---

### Post by reet on 2005-09-22
I am running Hoary but I thought I would post here since this is the only thread it would seem of any relevance to the M-Audio 2496 soundcard.

I have installed the card and am making sound no problem, but it would seem that I cannot run any mixer besides alsamixer. I use XFCE and xfce4-mixer gives a "segment fault". I have downloaded alsa-tools-gui from the debian experimental repository and installed it, however running envy24control gives to following output:
```

~$ envy24control
using    --- input_channels: 2
         --- output_channels: 2
         --- pcm_output_channels: 8
         --- spdif in/out channels: 2
Segmentation fault
```
I cannot manually compile envy24control since I do not have the required development packages. Is there a solution, or am I going to have to wait for the debian package to mature to a state where it can be used?

Thanks.

---

### Post by ElectronicMusic on 2005-10-09
Ah ha!
This just happened to me yesterday. This how I fixed it.

close envy24control
then delete the profile save file.

rm $home/envy24control/profiles.conf

Start it back.

---

### Post by reet on 2005-10-09
I am sorry to say that that wouldn't fixed it for me. Having never been able to start envy24control, the configuration files were never created.

---

### Post by mikeisme77 on 2005-10-14
[QUOTE=reet]I am sorry to say that that wouldn't fixed it for me. Having never been able to start envy24control, the configuration files were never created.[/QUOTE]

Not sure which development tools you need (as I have them myself), but it's more than likely the following:

gcc (either from Synaptic or apt-get install gcc)
libc6-dev (Synaptic or apt-get install libc6-dev)

Make SHOULD already be installed (I think), but you may need that as well... Any way, if you list the error messages you get then it would be easier to help you.

---

### Post by reet on 2005-10-14
Well, since I've now just upgraded to 5.10 and it still doesn't work, you've inspired me to download the nessicary development packages and compile it myself. Turns out all I needed was gtk1.2-dev and libasound2-dev. I'm amazed it actually worked. :D

---

### Post by dolson on 2006-03-07
Just as an FYI (I know this is an old thread), alsa-tools and alsa-tools-gui are now in Dapper.

---

### Post by thelusiv on 2006-07-24
alsa-tools, finally! Oh well, now I've given up on my 2496, and broke down and bought a Turtle Beach card just so I could have a headphone jack.

---

### Post by cheeesemonger on 2008-01-01
lol. I have the 2496 too... Ended up building a headphone amp. o_O

---

### Post by hemebond on 2008-02-05
I am running Ubuntu 7.10 Linux 2.6.22-14-generic #1 SMP Thu Jan 31 23:33:13 UTC 2008 x86_64 GNU/Linux. I have an nForce4 motherboard with onboard Envy24PT (ICE1724).

There were some updates installed today and they have broken my fragile sound setup. Most of the threads I have found offer no assistance, hint that it's already been fixed, or talk about recompiling the kernel after editing the module files. Also, despite having sound before, I have never been able to record any.

Some testing:```
~$ sudo modprobe snd-ice1724
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.22-14-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ice1724 (/lib/modules/2.6.22-14-generic/kernel/sound/pci/ice1712/snd-ice1724.ko): Unknown symbol in module, or unknown parameter (see dmesg)
``````
~$ dmesg
[ 1719.489364] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[ 1719.489368] snd_ac97_codec: Unknown symbol ac97_bus_type
[ 1719.490067] snd_ice1724: Unknown symbol snd_ac97_write_cache
[ 1719.490274] snd_ice1724: Unknown symbol snd_ac97_mixer
[ 1719.490331] snd_ice1724: Unknown symbol snd_ac97_bus
[ 1719.491521] snd_ice1724: Unknown symbol snd_ac97_read
[ 2157.805994] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[ 2157.805999] snd_ac97_codec: Unknown symbol ac97_bus_type
[ 2157.806895] snd_ice1724: Unknown symbol snd_ac97_write_cache
[ 2157.807152] snd_ice1724: Unknown symbol snd_ac97_mixer
[ 2157.807252] snd_ice1724: Unknown symbol snd_ac97_bus
[ 2157.807960] snd_ice1724: Unknown symbol snd_ac97_read
[ 2161.954070] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[ 2161.954074] snd_ac97_codec: Unknown symbol ac97_bus_type
[ 2161.965665] snd_ice1724: Unknown symbol snd_ac97_write_cache
[ 2161.965927] snd_ice1724: Unknown symbol snd_ac97_mixer
[ 2161.966029] snd_ice1724: Unknown symbol snd_ac97_bus
[ 2161.966777] snd_ice1724: Unknown symbol snd_ac97_read
[ 2393.931511] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[ 2393.931515] snd_ac97_codec: Unknown symbol ac97_bus_type
[ 2393.932360] snd_ice1724: Unknown symbol snd_ac97_write_cache
[ 2393.932615] snd_ice1724: Unknown symbol snd_ac97_mixer
[ 2393.932714] snd_ice1724: Unknown symbol snd_ac97_bus
[ 2393.933458] snd_ice1724: Unknown symbol snd_ac97_read
[ 2427.941356] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[ 2427.941360] snd_ac97_codec: Unknown symbol ac97_bus_type
[ 2427.942203] snd_ice1724: Unknown symbol snd_ac97_write_cache
[ 2427.942459] snd_ice1724: Unknown symbol snd_ac97_mixer
[ 2427.942561] snd_ice1724: Unknown symbol snd_ac97_bus
[ 2427.943270] snd_ice1724: Unknown symbol snd_ac97_read
``````
~$ lsmod
Module                  Size  Used by
snd_ice17xx_ak4xxx      6144  0 
snd_pt2258              6528  0 
snd_i2c                 8064  1 snd_pt2258
snd_ak4xxx_adda        10752  1 snd_ice17xx_ak4xxx
snd_mpu401_uart        11392  0 
snd_seq_dummy           5764  0 
snd_seq_oss            39040  0 
snd_seq_midi           11264  0 
snd_rawmidi            30336  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                63648  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27656  1 snd_seq
snd_seq_device         10772  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71464  10 snd_pt2258,snd_i2c,snd_ak4xxx_adda,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
vmnet                  51008  15 
vmblock                19144  4 
vmmon                 999404  7 
binfmt_misc            14860  1 
vboxdrv              1649696  0 
powernow_k8            16608  0 
cpufreq_powersave       3072  0 
cpufreq_userspace       6048  0 
cpufreq_stats           8160  0 
cpufreq_conservative     9608  0 
cpufreq_ondemand       10896  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
video                  21140  0 
ac                      7304  0 
button                 10400  0 
sbs                    21520  0 
dock                   12264  0 
container               6400  0 
battery                12424  0 
sbp2                   27144  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  2 parport_pc,lp
loop                   21764  0 
ac97_bus                4352  0 
snd_page_alloc         12560  0 
nvidia               7013492  34 
k8temp                  7680  0 
pcspkr                  4608  0 
xpad                   11400  0 
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
i2c_nforce2             7808  0 
i2c_core               30208  2 nvidia,i2c_nforce2
ipv6                  317192  24 
evdev                  13056  5 
ext3                  146576  3 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
sd_mod                 32512  9 
ata_generic             9988  0 
usbhid                 32576  0 
hid                    33408  1 usbhid
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
forcedeth              55048  0 
sata_nv                24068  7 
libata                138928  2 ata_generic,sata_nv
scsi_mod              172856  4 sbp2,sg,sd_mod,libata
ehci_hcd               40076  0 
amd74xx                17328  0 [permanent]
ide_core              141200  1 amd74xx
ohci_hcd               25092  0 
usbcore               161584  5 xpad,usbhid,ehci_hcd,ohci_hcd
raid10                 26880  0 
raid456               128544  0 
xor                     7312  1 raid456
raid1                  26880  0 
raid0                   9600  2 
multipath              11264  0 
linear                  7552  0 
md_mod                 88092  9 raid10,raid456,raid1,raid0,multipath,linear
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor
```

See also:
[http://ubuntuforums.org/showthread.php?t=27155](http://ubuntuforums.org/showthread.php?t=27155)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/16041](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/16041)

-------------------------------------------------
SOLVED

Thanks to Jim in irc://irc.freenode.net#alsa. I'm not sure exactly how much of this is required nor if this is everything because I tried a lot of stuff short of recompiling the kernel (which would have broken a lot more than sound).```
sudo aptitude install build-essential linux-headers alsa-source
sudo module-assistant
```Then I updated, selected Alsa from the module list, and built it. After a reboot I had sound again. Still not fully functional, but then I've never had that :-(

---

### Post by gladstone on 2008-02-06
I had the same problem of broken sound after 2.6.22-14-generic

Installing and running:

```

sudo apt-get install alsa-source module-assistant
sudo module-assistant

```

and rebuilding the Alsa modules was all it needed.

Thanks for your post hemebond

---

