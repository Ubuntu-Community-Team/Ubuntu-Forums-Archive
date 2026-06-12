---
title: "Onboard 'Realtek ALC662' or SB Audigy??"
date: 2008-08-07
forum: Hardware
---

### Post by witeboy724 on 2008-08-07
I'm finally putting together a new system and the motherboard (BIOSTAR TForce TP43D2A7) has built-in audio which is the Realtek ALC662.  I have a Soundblaster Audigy card that I used in my old system because the sound card went out in that mobo, and when I put in the card I got a lot better sound from my speakers.  

So my question is, should I use the onboard audio or should I put the Audigy card that I have?  I figure that onboard audio has come a long way from my old system and it might even be better than the older Audigy card.  What do you guys think?  Once I get the parts in the mail I can get it running and try it out, but it would be nice to know beforehand which is better.  Any feedback would be greatly appreciated!

---

### Post by Nepherte on 2008-08-07
I can't recommend Creative if you're looking for linux compatibility. Although your card *should* work, I'd go for the on board.

---

### Post by smi402 on 2008-08-08
You might want to check out this report regarding the ALC662 and the 2.6.24 kernel if you need to use the digital output.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=475441](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=475441)

I also avoid Creative cards if possible - their Linux support leaves a lot to be desired. Certainly avoid the X-Fi range as it appears necessary to go to OSS4 rather than ALSA to get them to work at all. For digital output "surround sound" options, cards based on the CMI8770 chipset appear to work well in Linux (for example HT Omega Striker 7.1, Auzentech X-Plosion). The Omega Striker works well for me. If you want a cheap card the ChainTech AV710 based on the ENVY24 chipset has been reported to work well for basic music and dvd output, but I have never tried one of these myself.

Trust this is useful!

---

### Post by Brebs on 2008-08-08
> **witeboy724 said:**
> when I put in the card I got a lot better sound from my speakers.
Audio that's built into motherboards still sucks. Use the Audigy. Although you haven't stated WHICH Audigy, but I assume it's an Audigy 2.

There's tons of garbage written on forums by people who've never even used an Audigy. Creative are scumbags, but the facts remains that an Audigy 4 off Ebay is the best card for a gamer and non-musician. Because it is one of the very few cards that has **hardware mixing**, and software mixing in Linux still sucks. See [links](http://forums.gentoo.org/viewtopic-p-4192284.html#4192284) for more info.

---

### Post by witeboy724 on 2008-08-08
Well I think I'm going to clone my older hard drive to my newer, faster, bigger one for this system.  It took me a while to get my dual boot for XP and Ubuntu going and it'd me nice not to have to start over.  I remember getting the Audigy to work with Linux was not fun, but eventually I got it running.  

The card is actually just the Audigy 1 (if they call it that).  I pretty much got it to replace the onboard on my other mobo when it burned out while switching cases.  Maybe it's time I just go buy a new card altogether.  I'll be using my system mostly for games (using XP, though I use Ubuntu for everything else).  I'll look into the Audigy 4.  Thanks for the replies and the link!

---

### Post by Nepherte on 2008-08-08
> **Brebs said:**
> Audio that's built into motherboards still sucks. Use the Audigy. Although you haven't stated WHICH Audigy.
[LIST=1]
[*] It all depends on the speakers you use. If you have speakers of $80, you won't hear much difference.
[*] Second, your audio source is important as well. What's the point of having a decent sound card if you play mp3s of 192kbps?
[*] If you're going to use the digital output, you use pass through anyways. Then there's no difference at all between on board and a external sound card.
[*] The advantage Creative has over other sound cards is EAX. That is only used in games...games as in, no linux games. They use openal most of the time.
[/LIST]
Most of the time an on board will do. If you already have the the sound card, you can always use that one of course. It's just if you're going to buy a new one, and even then I'd recommend other brands.

---

### Post by stchman on 2008-08-08
> **Nepherte said:**
> I can't recommend Creative if you're looking for linux compatibility. Although your card *should* work, I'd go for the on board.

Creative used to have good Linux support before the X-Fi.  My Audigy 2 works great.

---

### Post by resqguy on 2008-08-17
> You might want to check out this report regarding the ALC662 and the 2.6.24 kernel if you need to use the digital output.


I have 2.6.24.16 and can't get S/PDIF to work.  I haven't patched Linux in quite a while, but is there any way to upgrade to the 2.6.25 kernel to test this?  What would be the risk?

This is a new motherboard/install and this is the only OS that I have to test everything out.  If my MB is bad I want to get it RMAed ASAP.

I've done kernel builds in the past but I'm rusty.

---

