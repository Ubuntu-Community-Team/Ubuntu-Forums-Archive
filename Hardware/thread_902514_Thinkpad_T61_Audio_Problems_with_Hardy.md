---
title: "Thinkpad T61 Audio Problems with Hardy"
date: 2008-08-27
forum: Hardware
---

### Post by sparks13 on 2008-08-27
So I have seen a lot of other threads out there about similar problems and so far I have yet to find a solution that works for me. My problem is I have absolutely no audio when running on kernel 2.6.24-19-generic. However, it works perfectly fine with the 2.6.24-16-generic kernel. The problems arose for me with a kernel update shortly after I upgraded to Hardy. I've been getting by for months by simply booting into the older kernel when I've cared about audio. The 2.6.24-19-generic kernel actually caused from display problems to where X wouldn't load. However, I finally got those fixed just last night. So yeah, I've been messing with this off and on for the past several months without a solution. I've only been running linux for a little less than a year so I'm not an expert by any means, but I can handle some stuff. Any help would be greatly appreciated.

---

### Post by proxc on 2008-08-27
I've had no problems with T61 (14.1") audio on Hardy (2.6.24-19).  lspci gives:

```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

The module snd_hda_intel recognizes the card.

Can you provide some more info about your setup?

---

### Post by sparks13 on 2008-08-27
running lspci gives me this line for audio:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

What exactly are you wanting to know about the setup? Sorry, I haven't had to get this technical into troubleshooting any problems before.

---

### Post by proxc on 2008-08-27
> **sparks13 said:**
> 
What exactly are you wanting to know about the setup? Sorry, I haven't had to get this technical into troubleshooting any problems before.
Please give the output of lsmod|grep snd and dmesg|grep hda.  

Also, please run alsamixer and ensure that master and PCM have some volume and master isn't muted (muted is denoted by MM instead of 00).  

What are you using to try to play sound?  Try aplay <filename> on some wave file (look in /usr/share/sounds).

---

### Post by sparks13 on 2008-08-27
lsmod|grep snd
```
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  1 snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  1 snd_pcm

```

lsmod|grep hda returned nothing.

alsamixer
```
alsamixer: function snd_ctl_open failed for default: No such file or directory

```

As for trying to play sound, pick anything that makes a sound on the computer, nothing happens. If I click on the audio icon in the top right (it has a red square w/ a white x next to it), I get this:
```
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
```

---

### Post by proxc on 2008-08-27
What happens when you execute
```

modprobe -v snd_hda_intel

```
This is the kernel module (driver) which supports your audio hardware.  For some reason it's not loaded when you boot from the -19 kernel.

---

### Post by sparks13 on 2008-08-27
modprobe -v snd_hda_intel

```
insmod /lib/modules/2.6.24-19-generic/updates/snd-hda-codec.ko 
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.24-19-generic/updates/snd-hda-codec.ko): Operation not permitted
insmod /lib/modules/2.6.24-19-generic/updates/snd-hda-intel.ko index=0 model=thinkpad
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-19-generic/updates/snd-hda-intel.ko): Operation not permitted

```

---

### Post by proxc on 2008-08-28
My apologies, try
```

sudo modprobe -v snd_hda_intel

```
(loading drivers requires root privileges).

---

### Post by sparks13 on 2008-08-28
my apologies back at you. I ran it, saw the operation not permitted, and sudo'd it, but then copied the wrong thing.

sudo modprobe -v snd_hda_intel

```
insmod /lib/modules/2.6.24-19-generic/updates/snd-hda-codec.ko 
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.24-19-generic/updates/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
insmod /lib/modules/2.6.24-19-generic/updates/snd-hda-intel.ko index=0 model=thinkpad
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-19-generic/updates/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by proxc on 2008-08-28
Strange, but apparently not uncommon with Hardy kernels for some reason (see [here]("http://ubuntuforums.org/showthread.php?p=5507157") and [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/148561")):

I'm not sure why your module is in the updates/ directory (it's not on mine, it's in /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda), but someone more knowledgeable about how Ubuntu compiles and packages ALSA drivers might.

Try this:
```

sudo apt-get update
sudo apt-get install module-assistant
sudo module-assistant auto-install alsa

```

That's supposed to download and install ALSA packages from source.  Check to make sure that when you try to load snd_hda_intel again, that it's trying to load a file that was changed when you compiled it.  If not, you'll have to move the offending file away.

The underlying problem is a bug, but there appear to be open reports about it.  This is just a workaround that will hopefully fix things for you.

---

### Post by sparks13 on 2008-08-28
Well that worked like a charm! It required a restart of alsa which I couldn't remember how to do so I just rebooted. Everything seems to be working fine now. The logic seems to make perfect sense about it fixing the problem. I'm surprised I didn't see such a solution anywhere else. Anyways, a huge thanks. Let me know if you ever need some programming done. I'm a lot better with that.

---

### Post by aatheus on 2008-12-30
> **sparks13 said:**
> So I have seen a lot of other threads out there about similar problems and so far I have yet to find a solution that works for me. My problem is I have absolutely no audio when running on kernel 2.6.24-19-generic. However, it works perfectly fine with the 2.6.24-16-generic kernel. The problems arose for me with a kernel update shortly after I upgraded to Hardy. I've been getting by for months by simply booting into the older kernel when I've cared about audio. The 2.6.24-19-generic kernel actually caused from display problems to where X wouldn't load. However, I finally got those fixed just last night. So yeah, I've been messing with this off and on for the past several months without a solution. I've only been running linux for a little less than a year so I'm not an expert by any means, but I can handle some stuff. Any help would be greatly appreciated.

I had some trouble installing the mandated updates after a fresh Hardy install - some of the kernel packages failed to update. This broke wireless and sound on my T61. Installing the linux-restricted-modules package brought back wireless, but not sound.

I installed the linux-386 metapackage, which fixed the missing linux-ubuntu-modules package. Sound is back for me! Might want to try that!

---

### Post by asif.mkhan on 2009-11-19
My sound stopped working since I upgraded to 9.10. I have tried a few options including the ones suggested in these posts, but with no success. I have not been running linux for long so please let me know if I should provide any details that will be helpful in analyzing the problem.

I have the server generic pae kernel and 2.6.31-14-generic installed but the sound doesn't work on any.

---

### Post by b49P23TIvg on 2010-11-06
alsa build fatal    Maybe this is the one of the bugs?

$ locate pci_ids.h
/usr/src/linux-headers-2.6.35-22/include/linux/pci_ids.h
/usr/src/linux-headers-2.6.35-22-generic/include/linux/pci_ids.h
$ sudo module-assistant auto-install alsa
...
                 from /usr/src/modules/alsa-driver/acore/memalloc.inc:1,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
In file included from include/linux/pci.h:58,
                 from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/linux/pci_ids.h:2: fatal error: @CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No such file or directory
compilation terminated.
make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2
BUILD FAILED!
See /var/cache/modass/alsa-source.buildlog.2.6.35-22-generic.1289084163 for details.
Build failed. Press Return to continue...

---

### Post by b49P23TIvg on 2010-11-06
Thinkpad T500 ubuntu 10.10.

---

