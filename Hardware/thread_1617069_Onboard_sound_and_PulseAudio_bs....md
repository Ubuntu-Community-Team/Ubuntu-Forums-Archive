---
title: "Onboard sound and PulseAudio bs..."
date: 2010-11-08
forum: Hardware
---

### Post by Bi11yy on 2010-11-08
I use two soundcards in my system: onboard (Realtek 889a) for system sounds and mp3s and movies, which is routed by spdif to my firewire Focsurite Saffire LE, which I use for A/V work. That's piped to a pair of Wharfdale Diamond Pro Active speakers. in windows, this setup works like a charm, but in UbuStudio 64, I have this issue thats killing me. For some reason, PulseAudio is sending both channels to my right speaker. I verified this by killing the left speaker, and moving the l/r sliders in PulseAudio config gui up and down, I can still hear sound loud and clear when either one is down all the way! 
 Not only that, but I find this odd as well: I have my audio sent digitally, but selecting any of the analog outputs(5.1, stereo, 4 channel, et c....), which effectively should kill the digital outs, but they still play!
 I don't know if the two situations are related, but either way, my sounds is screwing. I'm getting no stereo image and staging, it just sounds like dual mono from my speakers. 
 I've killed pulse audio using the 'killall' command in terminal, and futzed with all my connections, replacing the spdif cable, almost everything I can think of. I'm sure its a driver problem, but not too sure how to go about resolving it. 
 Can anybody help?

---

