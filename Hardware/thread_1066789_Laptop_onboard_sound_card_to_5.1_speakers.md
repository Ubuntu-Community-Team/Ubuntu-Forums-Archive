---
title: "Laptop onboard sound card to 5.1 speakers"
date: 2009-02-11
forum: Hardware
---

### Post by micdhack on 2009-02-11
As you might have guessed from the title i dont get subwoofer, rear, and center speaker sound. So only basic stereo sound from the front speakers.

Im using alsa through pulse server.

lspci:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```
Also in the menu of sound it says **ALC888** near it

~/.asoundconf
```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/micdhack/.asoundrc.asoundconf>
pcm.!default {
type plug
slave.pcm &#8220;surround51&#8243;
slave.channels 6
route_policy duplicate
}
```

~/.asoundrc.asoundconf
```
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
pcm.!default {
type pulse
 }
ctl.!default { type pulse }
!defaults.pcm.card default
defaults.ctl.card default
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.pcm.file_format "raw"
defaults.pcm.file_truncate true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off

```

My laptops brand is Acer Aspire 7730G

Volume control Center, surround, lfe, side as options and it is unmuted.

I dont think its a pulse audio alsa problem cause alsa feed to pulse. Normally i think that if alsa worked correctly pulse wouldnt have a problem about it. In windows in order to make a card 5.1 you just choose the output and the 3 plugs become 5.1 sound (transformed from speaker, linein and mic).
Any other information you might need about solving the problem. i have seen that many people have the same problem and i have no idea if there is even a 5.1 support for watching movies or music for linux. (hopefull it has)

---

### Post by micdhack on 2009-02-11
after some trial and error i still havent got it to work but i managed to pinpoint some of the problems.

1st. I need in some way to tell ubuntu to use mic and line in for 5.1 sound. windows have an option but here i dont see anything in system->preferences->sound

2nd. Using this guide:
[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)
i changed the options and now default sample type in pulse is: s16le 6ch 44100Hz which is what i want but still on volume meter i get front left and right. Searching a little bit further on volume control of pulse audio my device: ALSA PCM on front:0 (ALC888 Analog) via DMA, has only two channels, front right and left.

3rd. As far as the test goes:
speaker-test -Dplug:surround51 -c6 -l1 -twav
i got this message
```
ALSA lib confmisc.c:768:(parse_card) cannot find card 'default'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM surround51
Chyba p&#345;i otevírání p&#345;ehrávání: -19,No such device

```

i have no idea if the configuration in alsa should specify a surround51 device

---

### Post by micdhack on 2009-02-15
ok at least can someone answer.. if there is no such feature for ubuntu i should propose it for development on ubuntu brainstorming site

---

### Post by zgemba on 2009-04-26
I don't either see the option to choose between laptop speakers and outer speakers connected on sound-out jack. (In windows these get auto detected.)

Codec: Realtek ALC888

---

### Post by micdhack on 2009-04-26
yeap after the upgrade to the new version i dont see any changes regarding that matter. I still have to hear everything in stereo in Ubuntu even though i have 5.1 system. Its a pitty...

---

