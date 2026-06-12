---
title: "Acer 4530-6039 headphone jack not working"
date: 2009-08-24
forum: Hardware
---

### Post by Statik on 2009-08-24
Hi all,

I've been trying to work out a couple of issues with my new (refurb) Acer 4530-6039 laptop. Everything seems to work good except for two exceptions, and one cavet, so far.

1. Wireless NIC : works great in windows, default driver works for open network, not for WPA. Working at it in a separate thread [here]("http://ubuntuforums.org/showthread.php?t=882003").
2. Random freezing of entire desktop, save for the mouse pointer. Temporary solution was to go back to no desktop effects.

3. Plugging in the headphones into the headphone jack does nothing. No sound from the headphones and speakers still sound.

I have searched through many posts about this issue on this laptop and others, and no posted solutions have worked. Can anyone walk me through fixing this?

Statik

---

### Post by christiebunny on 2009-08-24
I've got sound issues too -- it won't see my mic, or my headphones - and only my right speaker.

---

### Post by Statik on 2009-08-26
OK, I think I misunderstood the original instructions. I have my headphones working now.

I had to uninstall the backports as that was causing problems with the wifi setup. However, they didn't seem to be necessary. The trick was, and yes this was said before, was to open up the full volume control, find the control called 'Front' and mute it. This causes the headphones to start working.

It also helps if you plug the headphones into the correct port. I thought the laptop had the standard green, pink, black setup for headphones, microphone, digital, but no, it doesn't. That actually isn't green, but blue! It actually has blue, pink, black for line-in, microphone, headphones. 

Sound is working!

Wifi is fixed in the other thread.

Now, all I have to is play with the desktop effects (at my leisure) and everything will be working . .. I think.

Statik

---

### Post by coibyxqx on 2010-07-08
> **Statik said:**
> OK, I think I misunderstood the original instructions. I have my headphones working now.

I had to uninstall the backports as that was causing problems with the wifi setup. However, they didn't seem to be necessary. The trick was, and yes this was said before, was to open up the full volume control, find the control called 'Front' and mute it. This causes the headphones to start working.

It also helps if you plug the headphones into the correct port. I thought the laptop had the standard green, pink, black setup for headphones, microphone, digital, but no, it doesn't. That actually isn't green, but blue! It actually has blue, pink, black for line-in, microphone, headphones. 

Sound is working!

Wifi is fixed in the other thread.

Now, all I have to is play with the desktop effects (at my leisure) and everything will be working . .. I think.

Statik
"It actually has blue, pink, black for line-in, microphone, headphones. "
Yes, it is.
Thanks! :D
But under windows plugging the headphones into the blue and pink ports works. 
Actually the black one is not fit for my my headphone in size.

---

