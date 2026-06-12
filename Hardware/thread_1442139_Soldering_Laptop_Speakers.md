---
title: "Soldering Laptop Speakers"
date: 2010-03-29
forum: Hardware
---

### Post by fiveironfrnzy08 on 2010-03-29
Hi everyone,

I got a couple laptop speakers that I salvaged from my brothers laptop and I've trying to mod them a bit.

I took a 3.5mm male cable, split it open, and soldered the grounds, rights, and lefts together, making a portable set of 1.5W speakers. However, the sounds coming out is about earbud volume, not laptop speaker volume. Can anyone help with this? Is there a way to make them as loud as they were in a laptop?
Thanks in advance!

-Ryan

---

### Post by Barriehie on 2010-03-29
> **fiveironfrnzy08 said:**
> Hi everyone,

I got a couple laptop speakers that I salvaged from my brothers laptop and I've trying to mod them a bit.

I took a 3.5mm male cable, split it open, and soldered the grounds, rights, and lefts together, making a portable set of 1.5W speakers. However, the sounds coming out is about earbud volume, not laptop speaker volume. Can anyone help with this? Is there a way to make them as loud as they were in a laptop?
Thanks in advance!

-Ryan

What you've done is alter the impedance of the speakers.  To retain original volume you've got to keep the load and supply impedances matched, or **transformed** to match, each other.  You don't say whether it's a digital or analog source but google on 'audio impedance matching' and you'll see why they make 'transformers'.

---

### Post by fiveironfrnzy08 on 2010-03-29
Thanks for the reply!
I really know nothing about how impedance works...
Do you have any suggestions on what I could do for my situation, or will it pretty much just not be the same outside of the laptop's hardware?
To respond to your comment about digital or analog, I would guess digital but I'm not positive. The speakers came out of a year old HP DV7-1264nr laptop. What sort of difference will that make?
Thanks again!

---

### Post by Barriehie on 2010-03-29
See if you can find, via the speaker make/model/serial #,(ggogle) the impedance and I can probably provide some sort of circuit.

Check this out: [http://www.horrorseek.com/home/halloween/wolfstone/Audio/spkimp_SpeakerImpedanceMatching.html#WhereDoYouFindImpedance](http://www.horrorseek.com/home/halloween/wolfstone/Audio/spkimp_SpeakerImpedanceMatching.html#WhereDoYouFindImpedance)  [http://www.bcae1.com/spkrmlti.htm](http://www.bcae1.com/spkrmlti.htm)  [http://en.wikipedia.org/wiki/Impedance_matching](http://en.wikipedia.org/wiki/Impedance_matching)

---

### Post by fiveironfrnzy08 on 2010-03-29
Hey, I found out the speaker set is 480470-001, 4ohm 2W. I assume that's 2W total?
So there are two speakers, one with red and black and the other with white and black wires. The 3.5mm cable has red, blue, and copper. I took both blacks together and soldered them to the copper wire on the 3.5mm cable, then the red to red, and the white to blue. Any suggestions?
I looked at those sites, but I really don't know where to begin with it. This is great stuff though, I'm glad to be learning more about what's actually going on

---

### Post by Barriehie on 2010-03-29
> **fiveironfrnzy08 said:**
> Hey, I found out the speaker set is 480470-001, 4ohm 2W. I assume that's 2W total?
So there are two speakers, one with red and black and the other with white and black wires. The 3.5mm cable has red, blue, and copper. I took both blacks together and soldered them to the copper wire on the 3.5mm cable, then the red to red, and the white to blue. Any suggestions?
I looked at those sites, but I really don't know where to begin with it. This is great stuff though, I'm glad to be learning more about what's actually going on

The copper is the ground!  Red is RIGHT and white is LEFT,  I would've gone black >> black to blue and red >> white to red. You'll have to add a 2.2 ohm resister in series with the speakers; put it in between the blue wire and where it connects to both of the black wires.

---

### Post by fiveironfrnzy08 on 2010-03-29
> **Barriehie said:**
> I would've gone black >> black to blue and red >> white to red.
I didnt quite understand that, can you try that past me one more time?
I know copper is ground, so I thought I should put both the black wires (one black from each speader) with the copper. So in one piece soldered I've got black, black, and copper. The next piece soldered is red and red. The final piece soldered is white and blue. So in essence I have the three grounds together, the two rights together, and the two lefts together. Is that not how it should be?
If you have any diagrams or pictures to illustrate how it needs to be between the 2 right speaker wires, the 2 left speaker wires, and the 3 3.5mm cable wires, I'd love to see that to better understand what needs to happen.

---

### Post by Barriehie on 2010-03-29
> **fiveironfrnzy08 said:**
> I didnt quite understand that, can you try that past me one more time?
I know copper is ground, so I thought I should put both the black wires (one black from each speader) with the copper. So in one piece soldered I've got black, black, and copper. The next piece soldered is red and red. The final piece soldered is white and blue. So in essence I have the three grounds together, the two rights together, and the two lefts together. Is that not how it should be?
If you have any diagrams or pictures to illustrate how it needs to be between the 2 right speaker wires, the 2 left speaker wires, and the 3 3.5mm cable wires, I'd love to see that to better understand what needs to happen.

Yeah, you just need the resistor in there.

---

### Post by fiveironfrnzy08 on 2010-03-29
> **Barriehie said:**
> You'll have to add a 2.2 ohm resister in series with the speakers; put it in between the blue wire and where it connects to both of the black wires.

How did you come up with needing to use a 2.2 ohm resister?
Also the way I have it, the blue wire doesn't connect to the black wires... I guess I'm still just a little confused about what needs to happen and how the circuit needs to be set up.

---

### Post by Barriehie on 2010-03-29
I drew a pic and you appear to have it wired right.  How many watts is your supply rated for and what is it's impedance?

Edit:  Usually the watts specified in a sound system is total watts; not the addition of all of the components.  At least that's how it works in cars... 8)

---

### Post by fiveironfrnzy08 on 2010-03-30
Hmm, not too sure. I was trying to play music off a netbook 3.5mm jack, so I really don't have a clue what the wattage or impedance would be. Is there some generic set that is used with laptops and computers? Or do speakers usually just have stuff to modify to match the impedance of each output device?
And you never mentioned how you got 2.2 ohms ;)
Thanks for all your back-and-forth help here, it's much appreciated.

---

### Post by Barriehie on 2010-03-30
> **fiveironfrnzy08 said:**
> Hmm, not too sure. I was trying to play music off a netbook 3.5mm jack, so I really don't have a clue what the wattage or impedance would be. Is there some generic set that is used with laptops and computers? Or do speakers usually just have stuff to modify to match the impedance of each output device?
And you never mentioned how you got 2.2 ohms ;)
Thanks for all your back-and-forth help here, it's much appreciated.

There probably is some 'generic' set of numbers but I don't know what they are.  I got the 2.2 ohms because prior you said they were 4 ohm speakers and I was assuming they were now wired in parallel, which would 1/2 the ohmage.  2.2 ohms is the closest standard value that would bring it back up to 4. (Probably really 4.7 because that's a standard value)  I know this type of stuff because my parents are amateur radio operators and I grew up around electronics.  It used to be a hobby when I had more time.

---

### Post by Iowan on 2010-03-30
It's been awhile since I did impedance matching, but a transformer *might* be preferred. A resistor will help balance impedance, but will absorb signal. The proper transformer (if you can find it) will balance impedance at higher efficiency.

---

### Post by Barriehie on 2010-03-30
> **Iowan said:**
> It's been awhile since I did impedance matching, but a transformer *might* be preferred. A resistor will help balance impedance, but will absorb signal. The proper transformer (if you can find it) will balance impedance at higher efficiency.

Yes, the last time I bought one it was 1000:8 at radio shack.  Most of my stuff is RF, smaller, cheaper, you can make it.

---

