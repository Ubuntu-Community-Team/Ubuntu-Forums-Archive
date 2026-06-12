---
title: "X-Fi Fatality and Feisty"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by montgoja on 2007-05-28
General question:
Last September, I put together a computer of my own and purchased the Soundblaster X-Fi Fatality sound-card.  I dual boot Feisty and Windows XP, and it's a massive annoyance to switch my speaker input when I switch to windows for gaming/etc.  I've looked around and there doesn't seem to be any Linux support yet for the X-Fi series of cards... anyone have any further information about this that they can add?  I like having the frontside faceplate with all the inputs and everything, but it doesn't do me any good in Linux, which is my main OS.

---

### Post by christhemonkey on 2007-05-28
As far as i can tell its not likely to happen anytime soon as Creative Labs are actively preventing support of this device.

From the alsa sound card matrix:
> [X-] Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time.



Maybe you should email creative and let them know what you think about their lack of support for linux or even just helping the developers a little (by providing data sheets).

---

### Post by christhemonkey on 2007-05-29
Although you may be in luck...
According to here:
[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

> X-Fi series
The X-Fi series of products are not supported under Linux. (Yet)
Closed-source drivers will be available for the X-Fi series of sound cards.
It looks like the first public Beta will be available end calendar Q3 or early calendar Q4. It has taken more resources than expect to redesign our software and drivers for Vista.
It is planned that the drivers will have full support for ALSA (playback, recording, mixer, MIDI, synthesis) and OpenAL 1.1 (with EAX effects).

So they are going to release a driver for the Xfi series sometime this year hopefully!

---

### Post by montgoja on 2007-05-29
I'm only a year into Linux, personally, so I still have a LOT to learn.  haha.  How do I go about sending Creative Datasheets to help them make closed source drivers for the X-fi series?

---

### Post by christhemonkey on 2007-05-29
Oh sorry i didnt make that very clear;

The ALSA developers need (to create drivers) sheets of information regarding things like maximum voltages chips will accept and other relevant technical information.

Creative has this information but is refusing to share it with the ALSA developers.


I was suggesting that you emailed Creative and ask them to share their data sheets with ALSA people to help make open source drivers.

But it seems that Creative are making their own closed source drivers so its unlikely they will want to help the ALSA people make rival open source drivers.

---

### Post by paulg on 2007-05-30
I have no faith in Creative completing decent soundcard drivers for Linux - especially binary drivers. The ALSA team is *offering* to create the drivers for them on behalf of the card owners and they are stonewalling them? The Creative cards have some of the best, if not **the** best, audio driver support in Linux - certainly some of the most used drivers. I cannot understand Creative's reasoning on this. 

I suggest you check out an alternative card if it's an option and it's really becomming a problem for you. You might look at M-Audio (Revolution series) or perhaps Terratec depending on your locale. Unless you are doing a lot of gaming in Windows, I expect either company would make a card that would be as good as far as playback quality goes (excuse my ignorance if I am dead wrong as I know nothing of X-Fi). Both also have decent Linux support for some, if not all models. If you need EAX support then Creative is pretty much the only option but you could always downgrade to an Audigy...

~pAul.

---

