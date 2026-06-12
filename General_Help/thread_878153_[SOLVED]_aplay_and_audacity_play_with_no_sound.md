---
title: "[SOLVED] aplay and audacity play with no sound"
date: 2008-08-02
forum: General Help
---

### Post by unebaguettesvp on 2008-08-02
hi-

just recently, i noticed that gdm start up sound, the drum roll, stopped working. i knew that aplay is used to make that sound play when gdm starts up. so, i tried playing some audio files with it. and there is no sound coming out of it. then i tried to play some audio files with audacity. and again, no sound. however, amarok plays all those sounds just fine. the ubuntu start up sound works. anyone have any ideas? this just happened recently. my aplay -L says:

```

default:CARD=Audigy2
    Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Audigy2,DEV=0
    Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy2,DEV=0
    Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy2,DEV=0
    Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
side:CARD=Audigy2,DEV=0
    Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback
    Side speakers
surround40:CARD=Audigy2,DEV=0
    Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy2,DEV=0
    Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy2,DEV=0
    Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy2,DEV=0
    Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audigy2,DEV=0
    Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audigy2,DEV=0
    Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=UART
    MPU-401 UART
    Default Audio Device

```

so, i tried, aplay -D default:CARD=Audigy2 /usr/share/sounds/question.wav, and that didn't work either. can anyone help? i'm stuck. this just started happening recently.

---

### Post by unebaguettesvp on 2008-08-02
sorry for the bump! anyone have any ideas? thanks!

---

### Post by unebaguettesvp on 2008-08-02
fixed it by removing pulseaudio!!! i found out that audacity and aplay both are not compatible with pulseaudio. for more info, this is what i did:
[http://ubuntuforums.org/showthread.php?p=5512482#post5512482](http://ubuntuforums.org/showthread.php?p=5512482#post5512482)

---

