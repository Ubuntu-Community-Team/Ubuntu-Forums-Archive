---
title: "Bluetooth audio sink a2d and Enable=Socket with PulseAudio &gt; 2.9"
date: 2013-06-27
forum: Hardware
---

### Post by shaggyDan on 2013-06-27
Hi all, 

I have a little bit of a problem with getting a bluetooth audio device working under Ubuntu. 

The problem is this:
The device only connects if I enable the socket API of Bluze. This is done be setting Enable=Socket in the audio.conf.

But then I can't connect to PulseAudio because the d-bus API with the socket API is not supported.

So what I am trying to find out is why will my device only connect with the Enable=Socket.

And does any one know where to get info about the Bluze project?

Daniel

---

