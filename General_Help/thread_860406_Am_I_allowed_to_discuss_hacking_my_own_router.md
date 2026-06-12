---
title: "Am I allowed to discuss hacking my own router?"
date: 2008-07-15
forum: General Help
---

### Post by the lemming on 2008-07-15
Am I allowed to discuss this issue?

If so I'd like to see how easy it is to hack my WEP key?

And if it is indeed a doddle then I'm going to change to WAP keys.

Cheers

---

### Post by bodhi.zazen on 2008-07-15
Yes, but please search these forums first, there are several threads already discussing this.

---

### Post by the lemming on 2008-07-15
I did this by putting Hack Wireless Router and got nothing interesting except for 9 pages of irrelevant suggestions.

However if you have any useful links then I would be most grateful.

Cheers

---

### Post by bodhi.zazen on 2008-07-15
> **the lemming said:**
> I did this by putting Hack Wireless Router and got nothing interesting except for 9 pages of irrelevant suggestions.

However if you have any useful links then I would be most grateful.

Cheers

:lolflag:

[http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276)

---

### Post by the lemming on 2008-07-15
I take it that Cutting-and-Pasting into a terminal is the wrong way to go?

That or I'm a thicko.

---

### Post by fsmithred on 2008-07-15
Maybe I can save you the trouble. I've already seen how easy it is. Someone did a demo at a LUG meeting. We were on a college campus, and he collected packets while he gave the lecture for 30-40 minutes. When it came time to cracking the WEP code, it took him just under 15 seconds.

---

### Post by tamoneya on 2008-07-15
> **the lemming said:**
> I did this by putting Hack Wireless Router and got nothing interesting except for 9 pages of irrelevant suggestions.

However if you have any useful links then I would be most grateful.

Cheers

I find that it is best to use google to search ubuntu forums.  In your case I would type: "WEP crack ubuntu".  Typically the first couple results are ubuntu forums results.

---

### Post by the lemming on 2008-07-16
Sorry for appearing a bit thick here but does anybody have a fool proof walkthrough or guide that will help me in my quest?

Otherwise I will come to the conclusion that WEP is fine and dandy for everyday use seeing as Joe Bloggs won't have a clue on how to crack it.

---

### Post by Taxman415a on 2008-07-16
Well see, that's not really the issue. It does depend on the population density around your wireless router, but if there are people around, it only takes one of them to know how. Multiply that by the long time period over which your wireless network is operating and you make yourself an easy target.

As others have said it is trivial, but you do have to do a bit of reading. For example, search synaptic for WEP and read the manpages for some of those tools.

---

### Post by moore.bryan on 2008-07-16
Ars Technica's brilliant [wireless security]("http://arstechnica.com/guides/tweaks/wireless-security.ars") article discusses wep vs. wpa if that's what you're in a round-about way asking... if you just want to see how easy it is to hack a wep, what about [this]("http://www.hacknmod.com/displayMOD.php?hack=245")?

---

### Post by bodhi.zazen on 2008-07-16
As others have said, it depends on your level of paranoia and how sensitive your data is.

Regardless of your understanding, WEP is easily cracked, you should go to a more secure protocol if possible. You should change the default password on your router. You should configure your router to allow access by MAC.

If you do these things you will be better off. You should know, however, wireless is always less secure then wired (you are transmitting your packets in the airwaves and anyone with an antenna can pick them up. Your access point is also in the open so it makes sense to be as secure as possible).

---

### Post by the lemming on 2008-07-17
Ok, I am using the following guide
[http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276)

But I'm still confused.  I know that I have to ct and paste into my terminal but it is the coloured bits that are confusing me because I do not know how to find this information.

Can anybody help me?

The first but that I type is

sudo airmon-ng start <interface> <channel>


How do I find out what my interface and channel are?

---

### Post by the lemming on 2008-07-17
I'm banging my head against a brick wall here.  I've looked at every tutorial that I can get my hands on and I even have a copy of Back Track which is monitoring my packets.  So far I've monitored  12,000
of them

I am using the following tutorial
[http://ryanunderdown.com/2007/02/12/cracking-wep-using-backtrack/](http://ryanunderdown.com/2007/02/12/cracking-wep-using-backtrack/)

All goes well until I get to step to and at this point my inexperience shows itself.

I know I have to type something like this

airodump-ng ath0 -w /mnt/hda2/home/ryan/belkin_slax_rcu 9 1

But it is the bit between       -w /mnt/  bla bla bla_rcu 9 1     that is really confusing me.

Do I need to create a folder of my own.  And if I do how the hell do I type it in a way that the terminal will understand?

No matter what I type, which is obviously wrong, I get 

"airodump-ng --help" for help

---

### Post by bodhi.zazen on 2008-07-17
> **the lemming said:**
> Ok, I am using the following guide
[http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276)

But I'm still confused.  I know that I have to ct and paste into my terminal but it is the coloured bits that are confusing me because I do not know how to find this information.

Can anybody help me?

The first but that I type is

sudo airmon-ng start <interface> <channel>


How do I find out what my interface and channel are?

If you have questions about the tutorial, have you considered posting your questions on the tutorial ?

I doubt you will have much visibility on this thread, the tutorial is designed to show you how to use these tools, and your questions on the tutorial will help (and be found by) others.

---

