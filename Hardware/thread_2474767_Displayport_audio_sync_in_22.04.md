---
title: "Displayport audio sync in 22.04"
date: 2022-05-07
forum: Hardware
---

### Post by scarygary on 2022-05-07
I recently upgraded my HTPC from 20.04 to 22.04. Everything else works great, but I can't get my audio working properly. It's a Lenovo Thinkcentre M93p(Tiny) connected to my Denon receiver using a displayport to hdmi cable. In Ubuntu 20.04 everything worked great. 5.1 audio out playing video in Chrome as well as vlc. In 22.04 the audio is delayed by at least a second. I tried switching to pipewire according to some guide I found, that fixed the sync but completely scrambled the channels. I.e. front right turned to rear left, one of the front channels turned into the center channel and the other one into the subwoofer. I reverted back to pulse audio, but I still have no idea how to fix the sync issue.
I figured maybe I did something wrong, so after a full backup I reinstalled the entire machine. Didn't do any good though. Still the same issue. Easiest way to test it is using the gnome sound settings test feature. Whenever I click on a speaker it takes two seconds before the test sound is heard.
Since everything worked great in 20.04 I figured it must be a software issue.

---

