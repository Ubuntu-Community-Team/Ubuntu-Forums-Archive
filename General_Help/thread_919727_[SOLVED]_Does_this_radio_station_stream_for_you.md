---
title: "[SOLVED] Does this radio station stream for you?"
date: 2008-09-14
forum: General Help
---

### Post by paydaydaddy on 2008-09-14
[http://www.kgncam.com/](http://www.kgncam.com/)
Wondering if I can get this radio station stream to work with ubuntu hardy. Does it work for you? What app do you use to play it? I don't get any kind of prompt or error message. It acts like it is going to work and then nothing. Any clues?

---

### Post by exploder on 2008-09-14
The station streamed fine for me. I use MPlayer and had no problems at all.

---

### Post by paydaydaddy on 2008-09-14
I have mplayer installed but can't figure out how to make it the default for streaming audio. Also cannot figure out how to manually make it stream from the radio station. Any suggestions?

---

### Post by mb_webguy on 2008-09-14
The Totem plugin also plays it with no problems.

---

### Post by drs305 on 2008-09-14
> **paydaydaddy said:**
> I have mplayer installed but can't figure out how to make it the default for streaming audio. Also cannot figure out how to manually make it stream from the radio station. Any suggestions?

If you use Firefox I highly recommend mediaplayerconnectivity plugin. I use it for all sorts of things and it will let you easily configure the player you want to play a given type. 

In this case, I have it set up to use VLC but for some reason it wouldn't play your station. I right clicked the MPC icon, changed VLC to mplayer and got the audio working in a couple of seconds.

---

### Post by steveneddy on 2008-09-14
> **drs305 said:**
> If you use Firefox I highly recommend mediaplayerconnectivity plugin. I use it for all sorts of things and it will let you easily configure the player you want to play a given type. 

In this case, I have it set up to use VLC but for some reason it wouldn't play your station. I right clicked the MPC icon, changed VLC to mplayer and got the audio working in a couple of seconds.

Install the plugins for Firefox and all of the codecs for Hardy from Medibuntu.

Look at the links in my sig or click here:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron)

---

### Post by drs305 on 2008-09-14
> **steveneddy said:**
> Install the plugins for Firefox and all of the codecs for Hardy from Medibuntu.

Look at the links in my sig or click here:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron)

This is the first station I haven't gotten VLC to play. It could have been just a quirk as I only tried once and then switched to mplayer. I'd not used mplayer in MPC before.

---

### Post by paydaydaddy on 2008-09-14
I installed the mediaplayerconnectivity plugin and got things working. Thanks for the help. I will mark this thread solved.

---

### Post by lswb on 2008-09-14
I clicked on the streaming link in firefox, a new window opened and it played OK. One thing I see is that the link for the stream on that site is actually a javascript call to open a stream player on another site, rather than just a link to the stream itself. By copying the url from the firefox window that was playing the stream to the "open location" dialog in totem, I was able to get totem to play the stream.

This is what the url for the actual stream looked like: (all on one line!)

[http://www.streamaudio.com/stations/player/pages/newplayer/auth/GenerateASX2.asp?ts=1221397317843&t1=cc244e467521aa385031bd99f51f5198&t2=1e0bc4bb56f137f0b9c1ed8ff6a0fb6d&s=1365&y=2008&m=9&d=14&hh=13&mm=1&ss=56&useCall=&ntk=&referer=www_streamaudio_com](http://www.streamaudio.com/stations/player/pages/newplayer/auth/GenerateASX2.asp?ts=1221397317843&t1=cc244e467521aa385031bd99f51f5198&t2=1e0bc4bb56f137f0b9c1ed8ff6a0fb6d&s=1365&y=2008&m=9&d=14&hh=13&mm=1&ss=56&useCall=&ntk=&referer=www_streamaudio_com)

The javascript-generated urls appear to be dynamically changed and only valid for a short length of time, probably a way for the streamplayer site to track usage and get revenue somehow. Probably the easiest way to play is to install a plugin for firefox and just let firefox handle the linking. The totem plugins are available in the regular ubuntu repositories for hardy via synaptic.

---

### Post by lswb on 2008-09-14
oops, double post.

---

