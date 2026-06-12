---
title: "How do I get SBx00 Azalia (Intel HDA) (rev 40) to work?"
date: 2018-08-12
forum: Hardware
---

### Post by dalekky on 2018-08-12
My built-in audio device doesn't work in Ubuntu since about release Ubuntu 12.04
Now tried out Ubuntu 18.04.1 - it still isn't supported out of the box.

Does anyone know any way to make this card work in Ubuntu 18.04.1?

Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)

Nothing shows up in the sound settings menu in Ubuntu

It DOES show up in alsamixer

How do I fix this? I'd like to be able to get sound working again.

---

### Post by Yellow Pasque on 2018-08-12
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Yellow Pasque on 2018-08-13
I see that you found a solution (you had the jacks plugged incorrectly) in another thread. Please mark this thread solved.
Oh, and I hope it didn't take you 6 years to figure out that you plugged it in wrong.

---

### Post by dalekky on 2018-08-14
Oh yes.. Sorry. I'd forgotten I had this thread open.

The problem was solved on launchpad after I replied to Actionparsnip, the reply of which is re-posted below.

@actionparsnip  yes... plus - I just had an epiphany moment... wiping the dust away from  the ports on the back, I discovered that the front speaker's lead was  in fact plugged into the side surround port instead of the Line-out  port. I don't know when or how long ago it got swapped to the wrong port  - I've just been plugging and unplugging it into that wrong port  thinking it was the correct one (not being able to easily read the  label).
 The moment I plugged the front speaker lead into the correct port,  the option to select analogue surround suddenly re-appeared in sound  settings and everything was working again.
 I guess this non-problem is now solved.

---

### Post by dalekky on 2018-08-14
> **Temüjin said:**
> Oh, and I hope it didn't take you 6 years to figure out that you plugged it in wrong.

Embarrassingly... I think the plugs were in the wrong ports for at least 4 years :P

---

