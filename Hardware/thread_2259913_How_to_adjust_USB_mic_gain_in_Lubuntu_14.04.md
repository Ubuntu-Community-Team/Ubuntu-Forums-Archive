---
title: "How to adjust USB mic gain in Lubuntu 14.04?"
date: 2015-01-07
forum: Hardware
---

### Post by cdoublejj on 2015-01-07
How do I adjust USB microphone gain in Lubuntu 14.04? the also mixer just says no audio play back support on this device when i select my Microsoft Lifecam Cinema.

---

### Post by Dennis N on 2015-01-08
> How do I adjust USB microphone gain in Lubuntu 14.04?

In the default installation, Lubuntu does not have pulse audio installed. It may help adjusting your USB microphone. Packages to install are:

[B]pulseaudio
pavucontrol[/B]

which are Pulse Audio and Pulse Audio Volume Control.

---

### Post by cdoublejj on 2015-01-08
> **Dennis N said:**
> In the default installation, Lubuntu does not have pulse audio installed. It may help adjusting your USB microphone. Packages to install are:

[B]pulseaudio
pavucontrol[/B]

which are Pulse Audio and Pulse Audio Volume Control.


Just now installed that as per your suggestion. It does not see it, it see the HDMI audio on my video card. I'd almost blaem it o nthe fact it's also web came except Alsa did see it it as sound device where pulse audio does not. :?

---

### Post by cdoublejj on 2015-01-09
> **Dennis N said:**
> In the default installation, Lubuntu does not have pulse audio installed. It may help adjusting your USB microphone. Packages to install are:

[B]pulseaudio
pavucontrol[/B]

which are Pulse Audio and Pulse Audio Volume Control.

it only worked after reboot but, i only tried rebooting fter also install xfce audio mixer now i have no sound at all.

EDIT: clicked a few thing in pulse audio mixer and now i'm good to go, at least so far.

---

### Post by mörgæs on 2015-01-09
Please mark the thread 'solved'.

---

