---
title: "Nvidia GT1030 (low profile) - audio issue?"
date: 2023-02-12
forum: Hardware
---

### Post by michael351 on 2023-02-12
I have a GT1030 low profile card with its HDMO output connected a Marantz 11.2 channel processor. Multi-channel movie files (such as DTS-HD, DTS-Neo:X, etc.) would play and be decoded into my 7 speakers (L-c-R; Side & Rear) + two subs. Recently, I notice audio is not working properly - sometimes the center channel will come out the rear side speaker and otherwise I lose audio channels. Rebooting the computer sometimes works, but no more rear channels. In addition the Marantz no longer shows "DTS-HD or related" as the connection. Using my old Oppo blu-ray works perfectly, so it's not the processor. My older Roku box still works great with the same movies, but is not as handy as my HTPC.

Is it possible my video card's audio section is going "bad"? Could it even be the HDMI cable? (which I can swap to test). I just assumed it either works or it doesn't. Any experience on this very much appreciated. I've tried all kinds of configurations (including booting into windows to see if it is a driver issue - same problem). The "test" sounds in Ubuntu's settings sometimes plays through each channel, but often doesn't.

Could pulseaudio be the problem?

---

### Post by Autodave on 2023-02-13
That sounds like a failing card to me.  However, before you condemn it, I would at least try another HDMI cable first.  Cables do fail and can fail in many interesting ways.

---

### Post by Yellow Pasque on 2023-02-14
> **michael351 said:**
> Could pulseaudio be the problem?

If you have the same issue in Windows, it seems very unlikely. You may be able to find some creative ways to hack around the issue with pulseaudio channel remapping, but if the problem occurs in an entirely different OS, then it's likely a hardware issue. As you and Autodave noted, trying a different cable would be a good idea before digging further.

---

