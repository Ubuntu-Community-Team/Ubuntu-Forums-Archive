---
title: "No sound on MacBook 2,1 after upgrade to Jaunty"
date: 2009-04-28
forum: Hardware
---

### Post by Sopelsiasty on 2009-04-28
EDIT: SOLVED

Hi all.

I had an Intrepid installed on my MacBook 2,1 and configured according to some web-available instructions. It worked well, although sound was thin due to the fact, that alsa doesn't detect MacBook's third speaker. Nevermind.

Then I upgraded my system to Jaunty and the problems with sound began.

Generally - the sound drivers seem to be installed, ALSA Mixer works well and all audio programs start their playback without reporting any problems. The problem is that I can hear nothing. All alsamixer volume controls are set to full, but there's still no sound.

The thing is a little bit more complicated, because I don't know, whether those problems began directly after upgrade to Jaunty or a little bit later - I just don't use this computer for audio purposes too often.

According to lspci I've got an "Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)" if it can help you.

Thank you for your answers in advance.
Hope there will come a day when I'll be able to help someone.

---

### Post by Sopelsiasty on 2009-05-05
I solved the problem by myself.

Just install kmix (type sudo apt-get install kmix or search for kmix in Synaptic) and unmute all output devices. I don't know why default gnome-mixer doesn't cope with it.

---

### Post by tom4everitt on 2009-05-06
I had a similar problem on my macbook 1,1, after upgrading to jaunty.

The normal speakers worked fine, but the ear-phone output was ignored. When I inserted a cable, sound went to the built-in speakers.

I opened kmix (which was installed since I tried kde a while ago), and found that speaker2 was muted. Unmuting it fixed the problem.

---

