---
title: "Which init string to initialisize a Samsung phone in KMobileTools"
date: 2008-07-27
forum: General Help
---

### Post by Chimichurri on 2008-07-27
I use Kubuntu 8.04 Hardy Heron.
I own a Samsung SGH-D900i
I like to sync my telephone with KmobileTools.
But unfortunaly my phone isn't recognized:-(

Besides KmobileTools I tried all kind of Phone Managers for Linux, like:

- Wammu
- Gammu
- Gnokii
- Kandy

I setup my phone as an "Modem device" to be able to communicate via AT commands.

none of the above programs initialisize my phone correctly.

I now use the "GSM Generic setting" coz Samsung is not listed.
But it's not working.
I saw I can use an init string to try if KmobileTools will initialize it.

The init string is at the moment with the "GSM Generic" setting:
 
AT S7=45 S0=0 V1 X4 &c1 E0 
 
But as I said, unfortunaly the above init string is not working.

My concrete question is:

Which init string do I need to be able to initialisize my Samsung SGH-D900i Correctly?

Related to above described problem: When will KmobileTools 5.0.x final be released? from what I have seen of the Beta, it looks all very promising. I'm very anxious for the final release.

---

