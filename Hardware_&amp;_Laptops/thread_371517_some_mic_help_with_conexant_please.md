---
title: "some mic help with conexant please?"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by pixeldotz on 2007-02-27
i went through about 20 threads  till i decided to post but here's my problem.
internal mic does not work on my compaq c500.

the card is HDA INTEL with a CONEXANT CXT5045.

i know this because i've already compiled the latest alsa from source to get the headphones and speakers to run correctly. i'm very glad for this :) as it was something i was dreading doing.

i've tried so many different check and tweaks and configurations to get the mic to work but it just wont. one tutorial i was following fell bad when the compilatino said i need a CURSES library to configure the alsa-util.

does anyone know what else i could try? beleive me, i went through everything i could fine before deciding to post this, but i feel like i've tried every suggestion in those threads.

thank you, any help is greatly appreaciated.

---

### Post by pixeldotz on 2007-02-27
nobody has anymore info that could be of use?

---

### Post by lapichiflati on 2007-03-07
I have this same audio card on my HP DV2040 (DV2000) series laptop.  I got the mic to work with alsa driver 1.1.14RC2.  The problem is that there was no jack sense, meaning that the onboard speakers didn't mute when headphones were plugged in, so I added the patch made by Tobin Davis which I found on the ALSA devel mailing list.  This in effect made the onboard speakers mute but I lost mic functionality.  I just tried 1.1.14RC3 in hopes that it would return my mic functionality and give me jack sense, best of both worlds, but still no mic.  I am thinking about returning to RC2 to get mic back, but cant decide which option I prefer.

---

### Post by pixeldotz on 2007-03-07
can you tell me what options you used to get mic working?

i configured and installed rc2 with no problems about a week ago and got jack sense workig fine but no mic. now with rc3 i get jack sense and audacity shows that the mic input is enabled but still doesn't record sound input. moving the mic slider UP makes the mic sound actually lower and lowering makes it go up. strange.

---

### Post by MJMurray on 2007-03-26
I have an HP dv9005us running XP Pro (MCE 2005). The laptop has built-in microphones, and is preloaded with Vongo software, so it is obviously configured for microphone usage. However, no matter what I do, I can not get either the built-in mic or an external mic to work properly; there is too much background hiss/static to make the recording intelligible.

I've tried to activate the Microphone Boost feature, but on my system that option is grayed out. In fact, it is also grayed out on my wife's L2310CU laptop (HP Special Edition), and from other forums I've learned that users with other types of HP laptops have a similar problem.

Other than HP (who seem clueless about this problem), most people seem to think the problem is with the Conexant HD driver. Does anyone know of a work around or other fix for this driver? I've already uninstalled/reinstalled/updated the driver about a dozen times, and that hasn't worked. HP wants me to send the laptop in for repairs, and based on the experience of other users I'm convinced that won't solve the problem either, and I'll just end up back where I started.

---

### Post by a vagas ! on 2008-04-09
I have the same issue in my C500. I've searched and googled but I still not found a solution for the mic.

I'm running Gusty.


Any good news?

---

### Post by robyk on 2008-05-02
I have a Laptop HP DV2700t (Special Edition), it has a Conexant SoudCard with Ubuntu 8.04 64bit on it.
The hda_intel Alsa driver work fine on the output standing point but I can't get an acceptable level of the quality of the recording.
I think it's basically the same problem that MJMurray has, 

background noise while recording through the internal mic.

I've got the exact same result with Ubuntu 8.04i386 and 7.10i386, I don't know about Vista, I refused the EULA.
Does anyone have an idea if this may be either an hardware issue or a software issue? In case how to fix it?

Many Thanks.

---

### Post by ravl on 2008-05-28
I have a similar problem on my HP dv6810. My sound card is HPA Nvidia with a Conexant CX20651(Hermosa) chip. I have full output, all sounds work correctly. But the internal mics don't work, I'm using Skype test call to see, and nothing is recorded.
I'm using Kubuntu 8.04

---

### Post by vnieto on 2008-07-16
same error, same conexant (hermosa)

---

