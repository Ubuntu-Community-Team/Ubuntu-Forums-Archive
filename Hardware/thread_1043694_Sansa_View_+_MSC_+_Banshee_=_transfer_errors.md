---
title: "Sansa View + MSC + Banshee = transfer errors"
date: 2009-01-18
forum: Hardware
---

### Post by azredwing on 2009-01-18
Hi all,

I have a Sansa View 16GB. I am currently running Intrepid x64, and my music player of choice is Banshee.

Banshee (latest version, 1.4.1) locks up whenever I try to connect in MTP mode. After spending a lot of time on that problem, I decided to go with MSC mode.

Banshee detects the View in MSC mode (after placing .is_audio_player in the root folder for the player) but transferring music to the player always results in the following error:

```

Object reference not set to an instance of an object

```

Is this a Banshee issue, View issue, MSC issue, or some combination of the three?

(Transferring music works fine with Rhythmbox. I really would prefer to keep with Banshee but if necessary I will switch players...)

---

### Post by giancaldo on 2009-06-18
for me, banshee always fails to copy if I don't have the output_formats set in .is_audio_player

add the following to the the contents of .is_audio_player

```
audio_folders=MUSIC/,RECORD/,AUDIBLE/,AUDIOBOOKS/,PODCASTS/,
output_formats=application/ogg,audio/ogg,audio/mpeg,audio/flac,audio/wave,audio/x-wav,audio/x-ms-wma,audio/x-ms-wmv,audio/audible,audio/x-pn-audibleaudio
```look at post [http://ubuntuforums.org/showthread.php?t=917677](http://ubuntuforums.org/showthread.php?t=917677) for more info

---

### Post by giancaldo on 2009-06-18
you may want to add   audio/mp3  or    audio/mpeg   as the first entry in the output_formats list if you want banshee to convert the incompatible audio files to mp3 when you transfer.

---

