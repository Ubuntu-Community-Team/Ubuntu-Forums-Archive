---
title: "Hp pavilion dv6: no sound...from headphones"
date: 2009-06-30
forum: Hardware
---

### Post by Wanderingspirit on 2009-06-30
i've got Linux mint by the way, but as it is for one very similar to ubuntu, moreso on this subject, and the fact that I signed up for access to soundcheck's wonderful alsa upgrade script made me post here: why not use what you have? anyways...

Here's the problem (briefly): an out of the box install gives no sound. Absolutely. Yet pulseaudio shows me that there are sound streams coming out of my STAC92xx (that's the name it gives my card which according to lspci is an Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) (codec: IDT 92HD75B3X5 ), and moreover it also registers the laptop's internal mic (i think). It seems it registers nothing from the 3 jack front panel that I want to use: it doesn't register an external microphone, nor do i hear anything out of the two headphones jack.
Of course I played around with Volume control until my eyes bled. no dice. Volume control showed me among other things, master, PCM, speaker and headphones. Checked that everything was up to the max and unmuted. turned on every single option. Still nothing.

That's when i upgraded alsa, and started playing around with the models in alsa-base.conf . It turns out that with the latest versiuons of alsa I was able to get the internal speakers of my laptop to work. Moreover I accidentally found out that my external microphone was directly streaming to the external headphone jacks: i could hear myself speak but no sound from the system, no music etc... furthermore I could record the external mic no problem, and hear the results... on the laptop's internal speakers.

I've made progress but what i would really like is to be able to hear the system from external speakers, which in my opinion are much better than the (mediocre) internal speakers (bassless, for example). I've been able to activate the headphones (that is to say reroute the sound to their output) using a program called hda-verb-0.3 but it's a dirty hack: the commands requiring sudo access have to be reiterated at every boot (hence needing the password) and I lose the ability to play multiple streams at one time even with the latest snapshot of Alsa.

All in all, if anyone could suggest to me a better fix than what I've got i'm ready to delve into code and text files if need be. For those with similar problems I hope this helps you:
the (dirty) hack (which works) [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870)
soundcheck's great alas upgrade script: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

hardware info: running intel centrino 2 processor, ATI HD4500 series card (aplay -l gives me 3 choices, primary sound card (see up) analog, primary sound card digital, and HDMI output from the ATI  card.

Thx in advance for your answers :)

---

### Post by R3ason on 2009-07-03
Hi,
Same problem, same (dirty) solution...
I think Alsa doesn't support jack autodetect for our sound card...
so, as to me the real problem now is  "How we can detect if a jack is plugged in?" if we understand how it works , we can think to build something like a daemon.

---

