---
title: "Fiesty Sound Problem for Audigy 2ZS Sound Card"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by anon23 on 2007-06-03
Hi, 

I am having problem with my Creative Sound Card Audigy 2Zs.  It works perfectly in Dapper Drake Version. But in Fiesty, it has not worked.  Somehow After doing some tweak, it is working now,  but sometimes on booting it works perfectly but sometime it doesn't work and If it is not working then again i have to restart my PC and it will start automatically.  I don't know what the hell is going on.

---

### Post by crimsun on 2007-06-03
> **anon23 said:**
> sometimes on booting it works perfectly but sometime it doesn't work and If it is not working then again i have to restart my PC and it will start automatically.  I don't know what the hell is going on.

That's symptomatic of the nondeterminism of PCI device enumeration.  You can set a default card by using asoundconf(1) set-default-card, or you can blacklist the drivers for the audio devices that you DON'T want to be default, or you can use negative index masks for the drivers that you DON'T want to drive the default card(s).

---

### Post by FNDII on 2007-07-14
I have that same card. My problem is that my sound jumps from my on board to the pci sound card, at different times. Like rebooting and crashing and just periodically. 

How can I make it so that it will always use my audigy 2 Zs sound card?

---

### Post by ryanlhjess on 2007-11-11
that worked for me !

---

### Post by speirint on 2007-11-12
I've been having this problem in Fiesty, and even after upgrading to Gutsy it persists even still.

> **crimsun said:**
> That's symptomatic of the nondeterminism of PCI device enumeration.  You can set a default card by using asoundconf(1) set-default-card, or you can blacklist the drivers for the audio devices that you DON'T want to be default, or you can use negative index masks for the drivers that you DON'T want to drive the default card(s).

Can you please expound upon how this works?  I pasted asoundconf(1) set-default-card into the terminal and I'm assuming it expects me to put in the exact card I wnt to use.

I've had a similar problem and believe it's something to do with how the computer recognizes the sound card. When unsuccessfully testing, I get a couple of error messages either:

I will get a sound tone if I'm very lucky

or

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

or 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.


I'm using an integrated intel ICH5 card as well as something else that was supposed to enable 5.1 sound.

the default mixer tracks are as follows:
Intel ICH5 (alsa mixer)
C-Media PCI CMI87378-MC6 (Alsa mixer)
Realtek ALC655 rev 1 (OSS Mixer)

I have very little idea about what is what other than when using the oss, sound will sometimes work on the internet and in the gdm (the drum beat sound) when booting up.  Rythmbox and all other on-computer media programs are unable to make sound at all times, online audio (typically from streaming video) and the test sounds work only extremely rarely.

---

### Post by TheWired on 2007-11-14
I have an older version of the Audigy sound card in my system, but I was experiencing the same issues. Every time I restarted my machine it was 50% chance that my sound would work. The above fix for using asoundconf is what ended up working for me. The proper way of using the command is: 

```
asoundconf is-active <device>
asoundconf set-default-card <device>
```

If you execute ```
asoundconf list
``` you will be able to see what values you have for <device>. All I did was just set ```
asoundconf is-active ICH5
``` in rc.local so even if the system detects one card, once I log in the card I want will be selected. 

Hope this helps!

---

### Post by speirint on 2007-11-14
I pasted the code into terminal and the testing tones in system->preferences->sound are still giving the same errors regardless of the sound card that I select and oss, alsa, or something else. I'll try restarting the computer to see if any other changes will take effect afterward.

---

