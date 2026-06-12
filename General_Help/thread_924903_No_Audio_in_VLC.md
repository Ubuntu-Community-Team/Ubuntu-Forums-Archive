---
title: "No Audio in VLC"
date: 2008-09-20
forum: General Help
---

### Post by bluet0oth on 2008-09-20
I'm Currently running Hardy with all current updates on a Sony Vio VGN N-350-N

I've been having some strange audio problems, I can play movie files from MPlayer and they work just fine, but with ne other program theres no audio

I've gone in the sound options and changed everything to AlSA, gone through the sound options and none of the channels r muted, tried muted different channels to c if there were conflicts there... but I can't get audio from other programs and I need to get VLC working...

Ne Suggestions???

---

### Post by Breakar on 2008-09-20
I had this problem with VLC, if i play a movie then shut it off while its playing and then open anther movie it would have no sound.

using this command brings back sound for me, but i'm not sure what the overall problem is with it.

```
sudo /etc/init.d/alsa-utils restart
```

---

### Post by mb_webguy on 2008-09-20
What audio output module do you have set in VLC?  Try using the Alsa module, or installing the PulseAudio plugin for VLC and using it.

Also, you might want to take a look at the PulseAudio link in my signature.  Except for one game that won't let me change it's audio output -- I don't even know which it uses -- I haven't had any problems with sound since I applied those fixes.

Also, do you have Firefox open when you're trying to play VLC?  If so, you might want to try installing the Flash 10 plugin from the backports repository, which fixes some incompatibilities between Flash and PulseAudio which, among other things, may prevent other applications from having sound.

---

### Post by bluet0oth on 2008-09-20
VLC is set to alsa... far as i know everything is set to alsa, when i was using alsa and pulse i was having all sorts of audio problems, changing all settings to alsa seemed to fix that, but theres still a few things without audio, like VLC

---

