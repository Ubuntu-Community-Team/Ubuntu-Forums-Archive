---
title: "Windows video stream"
date: 2008-09-18
forum: General Help
---

### Post by Olav on 2008-09-18
Hello,

The debates in the lower house of Dutch parliament are streamed live through either of these URLs: [dialup]("http://streams.planet.nl/cgi-bin/reflector_tkstream.cgi?stream=TKStream4&title=Tweede%20Kamer%20der%20Staten-Generaal"), [broadband]("http://streams.planet.nl/cgi-bin/reflector_tkstream.cgi?stream=TKStream3&title=Tweede%20Kamer%20der%20Staten-Generaal"). The web page where I got these URLs is [here]("http://www.tweedekamer.nl/vergaderingen/plenaire_vergaderingen/live_devat_plenaire_zaal/index.jsp").

Typical of our sometimes clueless national government, the streams are of course done exclusively in Windows Media formats. I can't play them through either Mplayer (with w32codecs), Totem (gstreamer with all of the good, bad & ugly codecs) or VLC. I remember that about a year ago it **did** work, so something has changed either on their end or perhaps in the media players and codecs themselves. After all, since then I have also installed a new Ubuntu twice: 7.10 and 8.04.

So, are other users also unable to watch the streams? At the very moment I am posting this there is no debate, they will continue later this evening, but you should at least be able to see the empty parliament benches.

Should I be trying another media player?

I don't really like Wine or VMware solutions, though I am using the latter now as a workaround. But the sound is choppy, it's annoying and it makes it difficult sometimes to follow what is being said. As if some politicians aren't hard enough to understand already... ;)

---

### Post by Linteg on 2008-09-18
Well, you've tried the popular applications and I wouldn't be too hopeful if neither Mplayer nor VLC can play it, but it might be worth a try to install an application which uses Xine (such as totem-xine).

---

### Post by Olav on 2008-09-18
Of course, Xine, I had almost forgot about its existence.

So I did just try gxine. But unfortunately it gives the same (no) result as the other players... :sad:

---

### Post by mb_webguy on 2008-09-18
Are you sure there's not something wrong with the stream itself?  The stream identifies itself as type video/x-ms-asf, which the Totem plugin, Mplayer, and VLC should all be able to play with no problem.  But the Totem plugin says that it doesn't have the decoder to play the stream.  Since I have just about every codec available for Linux on this machine, I seriously doubt that I'm lacking a simple asf codec.

---

### Post by Olav on 2008-09-18
> **mb_webguy said:**
> Are you sure there's not something wrong with the stream itself?No, I'm not sure. But it would not surprise me at all.

> The stream identifies itself as type video/x-ms-asf, which the Totem plugin, Mplayer, and VLC should all be able to play with no problem.  But the Totem plugin says that it doesn't have the decoder to play the stream.Hmmm, Totem on my system doesn't give any message, just doesn't play the stream. How did you start it to receive that error message?

> Since I have just about every codec available for Linux on this machine, I seriously doubt that I'm lacking a simple asf codec.That's what I thought too in my case. Now that you confirmed, I am inclined to believe I was right. So I guess I will have to investigate this a bit further and file a complaint to the website. Problem is, I already know how well they respond to all complaints, suggestions or questions... Not very!

I have a card up my sleeve though: parliament itself has passed a resolution that the government should use and encourage the use of open standards and open source software in IT. Not much is being done with the resolution at all, but perhaps I could convince them to apply it here.

---

### Post by mb_webguy on 2008-09-18
> **Olav said:**
> Hmmm, Totem on my system doesn't give any message, just doesn't play the stream. How did you start it to receive that error message?

I'm just clicking on the link you provided to open the stream using the Totem plugin in Firefox.  Most of the time, it won't do anything, but every once in a while it will give me that message.

---

