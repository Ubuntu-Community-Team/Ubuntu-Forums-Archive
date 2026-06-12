---
title: "No Sound with Intel ICH5 Card"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by mrg201 on 2008-01-09
Dear All,

I have searched around and am fairly sure this hasn't been answered already. I can get no sound from my Intel ICH5 card with Gutsy Gibbon - it has never been a problem with previous distributions.

I get the little drum beat when the log on screen loads, but after I log in I can get no sound at all. I have compiled and installed the most recent ALSA driver but have the same problem. To my knowledge all the appropriate channels are unmuted. I have also checked and made sure that I am a member of the audio group. If I try to play anything using Rhythmbox it just sits there and does nothin (the time bar doesn't even progress) and eventually hangs. If I use splay in a terminal I get the following message (even if I do an su to make sure I'm root first just in case it is a group issue):

Cannot open /dev/dsp or /dev/sound/dsp!
splay: Failed to open sound device.

I can't understand this as it always plays the sound on the log in screen without fail.

I don't know if this is related but thought I would mention in case it holds any clues. In Rhythmbox (or Banshee) it wont let me pick AAC as an importing option (even though it is  set as an active profile in Rhythmbox), it just doesn't appear in the drop down box for Preferred Format. Oh and I've got all the good bad and ugly gstreamer versions installed.

---

