---
title: "Sony Vaio VPCF11S1E - no sound from internal speaker"
date: 2010-02-19
forum: Hardware
---

### Post by Giliad on 2010-02-19
Hello,

I've just installed Ubuntu 9.10 on my new Sony Vaio VPCF11S1E/B laptop. The problem at the moment is, that I can't get any audio from the internal built-in speaker. When I plug in headphones in the headphone jack, sound plays ok. I have a dual boot system with Windows 7, so I know that the speaker itself is working.

I've done some extensive searching on the subject and already tried out several things. I found a thread suggesting that I should check my hardware by issuing

```
cat /proc/asound/card0/codec#0 |grep Codec
```And based on that, change the value of  "options snd-hda-intel model=" in /etc/modprobe.d/alsa-base.conf. The problem is however, that what I get from the command is:
```
Codec: Realtek ID 275
```But I can't find a matching snd-hda-intel model -value anywhere (I've browsed through several listings like this one: [http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)). So far I've tried values "3stack" and "sony" based on some other threads I managed to dig up, but without much success.

I also tried to download and install Realtek audio drivers as suggested in this thread:
[http://ubuntuforums.org/showthread.php?t=557031](http://ubuntuforums.org/showthread.php?t=557031)

The installation went ok, I suppose, at least there were no errors. But still, no sound from the internal built-in speaker. The only thing I was not able to complete in the installation instructions found in the driver package, was running a program called "alsaconf". That one was not found on my system. On the other hand, I found some threads saying that it's already obsolete, so I honestly don't know if that has anything to do with this.

Any help or ideas you might have are much appreciated. Also, I'm quite new to this whole linux-on-desktop thing, so I would also like to be treated as a newbie with any suggestions.

Thanks, and at the end, output from my "lsmod | grep snd", if that's any help.
```
snd_hda_codec_realtek   276644  0 
snd_hda_intel          31264  2 
snd_hda_codec          89888  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9448  1 snd_hda_codec
snd_pcm_oss            44096  0 
snd_mixer_oss          18944  1 snd_pcm_oss
snd_pcm                91912  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3556  0 
snd_seq_oss            33632  0 
snd_seq_midi            8320  0 
snd_rawmidi            27104  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                61312  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25840  2 snd_pcm,snd_seq
snd_seq_device          8500  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77576  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10960  2 snd_hda_intel,snd_pcm

```

---

### Post by fedecrux on 2010-02-19
Hi,
I'm experiencing the same problem with my new sony vaio s series.
I managed to install the nVidia driver for my GeForce 310M following
[http://ubuntuforums.org/showthread.php?t=1369420](http://ubuntuforums.org/showthread.php?t=1369420)
but still I can't figure out how to fix the audio.
Windows 7 detects two audio cards, the first is an intel and the other is an nVidia.
I've read something about the nForce audio driver related to the HDMI audio output, maybe the things are related.

Anyway here's my output for 'aplay -l':
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and through 'alsamixer' I can only see 'Master', 'PCM' and 'Capture'.

Any ideas?

---

### Post by Giliad on 2010-02-19
Fedecrux, almost everything you say I can see on my machine as well. The only difference is I can't see "Capture" in alsamixer.

I also had some struggle getting nVidia 330M working. Basically I did pretty much what you did. In addition, I had problems with wireless network. That one I managed to solve by installing a package called "linux-backport-modules-karmic-generic". 

Slightly related to that, I forgot to say that I also installed a package called "linux-backports-modules-alsa-karmic-generic" that was mentioned in some thread. Didn't help either.

---

### Post by kenjiru on 2010-02-20
I'm having the same problems with sound. I have an VPCF11M1E.

root@kenjiru:/home/radu# cat /proc/asound/card0/codec#0 |grep Codec
Codec: Realtek ID 275

root@kenjiru:/home/radu# lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)

---

### Post by jfrorie on 2010-02-20
Similar problem on a VPCS111FM.  I think we all have the same hardware.  I filed a bug at:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/525149](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/525149)

---

### Post by fedecrux on 2010-02-21
> **Giliad said:**
> Fedecrux, almost everything you say I can see on my machine as well. The only difference is I can't see "Capture" in alsamixer.

I also had some struggle getting nVidia 330M working. Basically I did pretty much what you did. In addition, I had problems with wireless network. That one I managed to solve by installing a package called "linux-backport-modules-karmic-generic". 

Slightly related to that, I forgot to say that I also installed a package called "linux-backports-modules-alsa-karmic-generic" that was mentioned in some thread. Didn't help either.
Same problem with the wireless network. I can see from 'dmesg' some frimwares are missing.

$ dmesg|grep iwlwifi
[   12.620436] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-3.ucode
[   12.741991] iwlagn 0000:02:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[   12.741996] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-2.ucode
[   12.743596] iwlagn 0000:02:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[   12.743598] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-1.ucode
[   12.745190] iwlagn 0000:02:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[   12.805874] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-3.ucode
[   12.807536] iwlagn 0000:02:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[   12.807541] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-2.ucode
[   12.809827] iwlagn 0000:02:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[   12.809833] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-1.ucode
[   12.813272] iwlagn 0000:02:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2

In fact there's only 'iwlwifi-6000-4.ucode' in /lib/firmware
I googled but couldn't find the missing firmware.

---

### Post by Giliad on 2010-02-21
I had the same symptoms. Take a look at this thread, the sixth post by Chili555 in particular. It's what worked for me:
[http://ubuntuforums.org/showthread.php?p=8840255](http://ubuntuforums.org/showthread.php?p=8840255)

---

### Post by fedecrux on 2010-03-30
Problem solved :D
Upgrading the alsa diver to version 1.0.22 sound works!

[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

---

### Post by jfrorie on 2010-03-30
> **fedecrux said:**
> Problem solved :D
Upgrading the alsa diver to version 1.0.22 sound works!

[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

The current updates appear to have fixed the speaker problem.  The microphone still isn;t working.

Did the alsa install make the microphone functional?

---

### Post by fedecrux on 2010-03-30
> **jfrorie said:**
> The current updates appear to have fixed the speaker problem.  The microphone still isn;t working.

Did the alsa install make the microphone functional?

No, mic is not working. I hadn't tried yet.

---

