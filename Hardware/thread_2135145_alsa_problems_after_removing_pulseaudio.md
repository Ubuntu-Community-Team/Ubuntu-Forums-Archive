---
title: "alsa problems after removing pulseaudio"
date: 2013-04-13
forum: Hardware
---

### Post by logan_2k6 on 2013-04-13
HI,

so for info im have a creative xfi fatality pro, kubuntu 12.10
ive try kubuntu cause it has alsa by deafult so that stupid pulseaudio is not present (or at least is not present). why alsa? cause i can use the alsaequal awesome plugin.
why not pulseaudio? pulseaudio has a equalizer too u know?
yeah i know but the sound on pulse audio is crap and with equalizer is even worst than before.

problem: some applications keep instaling pulseaudio. after that alsa is gone....well not completly but plugin for alsa does not work anymore.
if i remove pulseaudio with apt-get remove pulseaudio then i loose all surround sound. all thats left is fron channels althou alsamixer show all channels.but the good part is that alsaequal works again.
channels are not on mute (for info)
also my kmix looks diffrent from how it use too look.
so questions:
how can i disable pulseaudio to never ever install again?
how can i disable pulseaudio for good (if 1st question is not posible)
how do i get my channels back on after removing pulseaudio?
is there any way to trick programs that i have pulseaudio and actually to use alsa? (without the presence of pulseaudio in my system)
is there a good reason to keep developing this pulseaudio? it seems that has bad sound quality and from what i can tell pulseaudio still use alsa (in a weird way for me)

also some information in case this [http://www.alsa-project.org/db/?f=ecaa9bf19198bab4439de241dfab2383f5862f10](http://www.alsa-project.org/db/?f=ecaa9bf19198bab4439de241dfab2383f5862f10) is helful for you. cause for me its not much of info (since i'm kind of a noob to linux)

---

### Post by Aide9aic on 2013-04-21
A standard Kubuntu install will include PulseAudio. It isn't a hard dependency, so you can remove it. However, some packages in the repositories have a hard dependency on Pulse:

```
steve@t520:~$ apt-cache rdepends --no-recommends --no-suggests pulseaudio | grep -v pulseaudio
Reverse Depends:
 |kde-telepathy-call-ui
  veromix-common
  ubuntustudio-desktop
  ubuntu-gnome-desktop
 |kde-telepathy-call-ui
  indicator-sound-gtk2
  gnome-core
  arkose
  ubuntu-desktop
  ltsp-client
  libcanberra-pulse
  indicator-sound
```

Kubuntu is packaged with the expectation that PulseAudio will be used, so it's difficult to predict how your audio might work without it.

Which version of KDE are you running? In 4.10, KMix has [undergone some changes]("http://kmix5.wordpress.com/"). Further [changes will come later]("http://wm161.net/2013/03/21/a-fresh-new-kmix/").

If you don't like KMix, and you're looking for something with an equalizer, have you investigated the Veromix Plasmoid? I would recommend that.

---

### Post by CatKiller on 2013-04-21
Pulse Audio's sound quality is no better or worse than ALSA's.

---

