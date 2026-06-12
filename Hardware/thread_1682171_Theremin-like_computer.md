---
title: "Theremin-like computer"
date: 2011-02-05
forum: Hardware
---

### Post by felinoel on 2011-02-05
I want to produce an electric theremin, yes I know the theremin is already electric but I am using the term electric as it is used in the electric piano, if someone can find me a better term to use please do not hesitate to say so.

This instrument will work exactly like an ordinary theremin, but the type of sound should be able to be adjusted like an electric piano. If I want the theremin to produce guitar sounds I would flip it to one switch, theremin another, etc and so forth. For some instruments like drums, the volume control could instead be speed control. 

Someone in a different community told me that to somehow take the analog data received from the theremin's electric field and convert it to a digital format so the note played can be read and the appropriate sound come out, would call for running it through Linux and planet ccrma software, though taking this route I would prefer to just have the computer be the theremin itself...

Is this possible? How would you go about it? How much would you think this may end up costing me?

---

### Post by cchhrriiss121212 on 2011-02-05
> This instrument will work exactly like an ordinary theremin
To clarify this statement, do want something that can just make the same sounds a theremin makes (easy), or do you want the control system as well (difficult)?
Do you currently own a theremin?

---

### Post by felinoel on 2011-02-05
> **cchhrriiss121212 said:**
> To clarify this statement, do want something that can just make the same sounds a theremin makes (easy), or do you want the control system as well (difficult)?
Do you currently own a theremin?Same control system, and yea I know it will be difficult x.x

In college I used to play my professor's theremin and I currently am looking up cheap theremins I can gut or pieces of theremins I can put together. Would it be better to mod or to build from scratch?

---

### Post by cchhrriiss121212 on 2011-02-05
Essentially what you are aiming for is a software synthesiser with MIDI input from a theremin control set. Getting a synth is the easy part, there are plenty of free ones in the repos: zynaddsubfx, phasex, bristol.

The difficulty will be getting a MIDI signal from a theremin.
A theremin with built in MIDI has been produced by Moog:
[http://www.moogmusic.com/theremin/?section=product&product_id=11]("http://www.moogmusic.com/theremin/?section=product&product_id=11")
But you can also do this via software with pure data:
[http://createdigitalmusic.com/2008/08/how-to-turn-theremin-into-midi-free-with-pd/]("http://createdigitalmusic.com/2008/08/how-to-turn-theremin-into-midi-free-with-pd/")
I would recommend the second option as it is roughly $5000 cheaper. All you need now is a theremin, you won't need to do any hardware modding, just a cable to hook it up to your computer sound input.

---

### Post by felinoel on 2011-02-05
> **cchhrriiss121212 said:**
> Essentially what you are aiming for is a software synthesiser with MIDI input from a theremin control set. Getting a synth is the easy part, there are plenty of free ones in the repos: zynaddsubfx, phasex, bristol.

The difficulty will be getting a MIDI signal from a theremin.
A theremin with built in MIDI has been produced by Moog:
[http://www.moogmusic.com/theremin/?section=product&product_id=11]("http://www.moogmusic.com/theremin/?section=product&product_id=11")
But you can also do this via software with pure data:
[http://createdigitalmusic.com/2008/08/how-to-turn-theremin-into-midi-free-with-pd/]("http://createdigitalmusic.com/2008/08/how-to-turn-theremin-into-midi-free-with-pd/")
I would recommend the second option as it is roughly $5000 cheaper. All you need now is a theremin, you won't need to do any hardware modding, just a cable to hook it up to your computer sound input.Can I just gut the theremin I get, stick a hard drive in it, and make it a new case?

Also, THANK YOU for such AMAZING help

---

### Post by cchhrriiss121212 on 2011-02-05
> Can I just gut the theremin I get, stick a hard drive in it, and make it a new case?
A theremin produces analogue audio and a hard drive reads and writes digital data, so you can't just stick them together unfortunately. 
> Also, THANK YOU for such AMAZING help
No problem, post back if you need any help setting up pure data (which you can also find in the repos). I just ran the program, and it seems to work OK, but I don't have a theremin to test it on. Good luck theremin hunting, I know they are not cheap.

---

### Post by felinoel on 2011-02-05
> **cchhrriiss121212 said:**
> A theremin produces analogue audio and a hard drive reads and writes digital data, so you can't just stick them together unfortunately. 

No problem, post back if you need any help setting up pure data (which you can also find in the repos). I just ran the program, and it seems to work OK, but I don't have a theremin to test it on. Good luck theremin hunting, I know they are not cheap.Well it will be getting steampunked and so changing the casing would help, can't I just put them next to each other? Not combine them physically just in a single box?

---

### Post by cchhrriiss121212 on 2011-02-05
Sure, as long as you take cooling into account. So by hard drive, did you mean a whole computer system?

---

### Post by felinoel on 2011-02-05
> **cchhrriiss121212 said:**
> Sure, as long as you take cooling into account. So by hard drive, did you mean a whole computer system?Hm... guess I would *have *to mean that, wouldn't I?

> **cchhrriiss121212 said:**
> But you can also do this via software with pure data:
[http://createdigitalmusic.com/2008/08/how-to-turn-theremin-into-midi-free-with-pd/]("http://createdigitalmusic.com/2008/08/how-to-turn-theremin-into-midi-free-with-pd/")
I would recommend the second option as it is roughly $5000 cheaper. All you need now is a theremin, you won't need to do any hardware modding, just a cable to hook it up to your computer sound input.Now I am not doing this myself as I am not one who is adept at circuitry and whatnot, but the one who is moderately enough that I have doing this for me says that he needs a schematic of the patching device, but you say I just need a cable?

---

### Post by cascade9 on 2011-02-06
> **cchhrriiss121212 said:**
> Sure, as long as you take cooling into account. So by hard drive, did you mean a whole computer system?

Cooling could be a problem, but I'd want to put some form of faraday shielding between he theramin and the computer parts. 

[http://en.wikipedia.org/wiki/Faraday_cage](http://en.wikipedia.org/wiki/Faraday_cage)

Not that theramins create a huge electrical field, but better safe than sorry.

---

### Post by wilee-nilee on 2011-02-06
[http://www.moogmusic.com/theremin/?](http://www.moogmusic.com/theremin/?)

Bob Moog is gone, but his genius lives on.

---

### Post by felinoel on 2011-02-06
> **felinoel said:**
> Hm... guess I would *have *to mean that, wouldn't I?

Now I am not doing this myself as I am not one who is adept at circuitry and whatnot, but the one who is moderately enough that I have doing this for me says that he needs a schematic of the patching device, but you say I just need a cable?[http://www.amazon.com/Alesis-GuitarLink-AudioLink-4-inch-Cable/dp/B001OXEDA0](http://www.amazon.com/Alesis-GuitarLink-AudioLink-4-inch-Cable/dp/B001OXEDA0)

Is this the cable you speak of?

> **cascade9 said:**
> Cooling could be a problem, but I'd want to put some form of faraday shielding between he theramin and the computer parts. 

[http://en.wikipedia.org/wiki/Faraday_cage](http://en.wikipedia.org/wiki/Faraday_cage)

Not that theramins create a huge electrical field, but better safe than sorry.Yea was also trying to think of some build that would work that wouldn't be too bulky...

> **wilee-nilee said:**
> [http://www.moogmusic.com/theremin/?](http://www.moogmusic.com/theremin/?)

Bob Moog is gone, but his genius lives on.k

---

### Post by cascade9 on 2011-02-06
> **felinoel said:**
> Yea was also trying to think of some build that would work that wouldn't be too bulky...

Bulky is good with steampunk :lolflag:

If you really wanted it small, I'd probably just mount the hardware under the HDD cage. Copper mesh is the best material to use for a faraday shield, but even aluminum foil will give you some protection. A foil lined bag is how people make 'booster bags' to shoplift RFIDed goods. ;)

---

### Post by felinoel on 2011-02-06
> **cascade9 said:**
> Bulky is good with steampunk :lolflag:Oh no it definitely will be bulky, especially with the mini fog machine for a steam effect and the moving gears on the front of it (though am not sure about these gear), I said I didn't want it to be *too* bulky

> If you really wanted it small, I'd probably just mount the hardware under the HDD cage. Copper mesh is the best material to use for a faraday shield, but even aluminum foil will give you some protection. A foil lined bag is how people make 'booster bags' to shoplift RFIDed goods. ;)I was planning on attaching it to a strap and wearing it though, which will definitely lead to some awesome sounds if I play it while wearing it

---

### Post by cascade9 on 2011-02-06
> **felinoel said:**
> Oh no it definitely will be bulky, especially with the mini fog machine for a steam effect and the moving gears on the front of it (though am not sure about these gear), I said I didn't want it to be *too* bulky

I wouldnt put a fog machine in the same case as a computer. Or even run one in the same room as a computer if I had any other option. Beside the heat output, the fog itself is bad for computer parts.....

---

### Post by felinoel on 2011-02-06
> **cascade9 said:**
> I wouldnt put a fog machine in the same case as a computer. Or even run one in the same room as a computer if I had any other option. Beside the heat output, the fog itself is bad for computer parts.....

Oh sadface, I figured I would chance the fog but didn't think of the heat output... sigh, scratch that then, two possible issue causers is not worth chancing it...

Well at least that is one expense that doesn't need bought so huzzah for that

---

### Post by cchhrriiss121212 on 2011-02-06
> **felinoel said:**
> 
Now I am not doing this myself as I am not one who is adept at circuitry and whatnot, but the one who is moderately enough that I have doing this for me says that he needs a schematic of the patching device, but you say I just need a cable?
Assuming the theremin you buy has a standard 1/4" jack output, and your computer has a standard 1/8" line-in, a cable like this is all you would need:
[http://cgi.ebay.co.uk/Cable-Stereo-3-5mm-Mini-Jack-6-3mm-MONO-Lead-3M-/200565727551?pt=UK_Computing_CablesConnectors_RL&hash=item2eb2a6213f](http://cgi.ebay.co.uk/Cable-Stereo-3-5mm-Mini-Jack-6-3mm-MONO-Lead-3M-/200565727551?pt=UK_Computing_CablesConnectors_RL&hash=item2eb2a6213f)
Then the rest is handled by software, no need for any circuitry knowledge.

If you are to be wearing this contraption, I think a netbook should have enough resources to handle the audio manipulation, but I would test one out first.

---

### Post by cascade9 on 2011-02-06
You could probably build something for dry ice. While it wouldnt be as smokey as a mini fog machine, at least the CO2 wont get into your parts and blow anything up. The only thing you would need to be careful of woud be condensation.

---

### Post by felinoel on 2011-02-06
> **cchhrriiss121212 said:**
> Assuming the theremin you buy has a standard 1/4" jack output, and your computer has a standard 1/8" line-in, a cable like this is all you would need:
[http://cgi.ebay.co.uk/Cable-Stereo-3-5mm-Mini-Jack-6-3mm-MONO-Lead-3M-/200565727551?pt=UK_Computing_CablesConnectors_RL&hash=item2eb2a6213f](http://cgi.ebay.co.uk/Cable-Stereo-3-5mm-Mini-Jack-6-3mm-MONO-Lead-3M-/200565727551?pt=UK_Computing_CablesConnectors_RL&hash=item2eb2a6213f)
Then the rest is handled by software, no need for any circuitry knowledge.

If you are to be wearing this contraption, I think a netbook should have enough resources to handle the audio manipulation, but I would test one out first.lol you didn't see my post after that, was googling about it and found this cable

[http://www.facebook.com/l.php?u=http%3A%2F%2Fwww.thereminworld.com%2Fforum.asp%3Fcmd%3Dp%26T%3D1839%26F%3D715&h=2239a](http://www.facebook.com/l.php?u=http%3A%2F%2Fwww.thereminworld.com%2Fforum.asp%3Fcmd%3Dp%26T%3D1839%26F%3D715&h=2239a)

Would this work instead?

> **cascade9 said:**
> You could probably build something for dry ice. While it wouldnt be as smokey as a mini fog machine, at least the CO2 wont get into your parts and blow anything up. The only thing you would need to be careful of woud be condensation.Awesome idea, don't know how often I would use it though...

---

### Post by cchhrriiss121212 on 2011-02-06
> lol you didn't see my post after that, was googling about it and found this cable

[http://www.facebook.com/l.php?u=http...%3D715&h=2239a]("http://www.facebook.com/l.php?u=http%3A%2F%2Fwww.thereminworld.com%2Fforum.asp%3Fcmd%3Dp%26T%3D1839%26F%3D715&h=2239a")

Would this work instead?I would avoid it, it could work OK, but it would be a risk. Even if it does work it has no real advantage over using an analogue cable and it costs more money.

Edit:
If you want an easy preamp, try using a guitar overdrive pedal. This will boost the signal before it reaches the computer and allows you to adjust the sound.

---

### Post by felinoel on 2011-02-06
> **cchhrriiss121212 said:**
> I would avoid it, it could work OK, but it would be a risk. Even if it does work it has no real advantage over using an analogue cable and it costs more money.Well I was wanting to keep the theremin's internal computer minimal and I figured attaching a USB port would be easier and/or cheaper than a 1/8 port

> Edit:
If you want an easy preamp, try using a guitar overdrive pedal. This will boost the signal before it reaches the computer and allows you to adjust the sound.Oh hey thanks!

---

### Post by cchhrriiss121212 on 2011-02-06
> Well I was wanting to keep the theremin's internal computer minimal and I  figured attaching a USB port would be easier and/or cheaper than a 1/8  port
Pretty much all motherboards will have both ports available. What are you planning to use for the computer, a [mini-ITX]("http://www.mini-itx.com/store/?c=2") board?

---

### Post by felinoel on 2011-02-06
> **cchhrriiss121212 said:**
> Pretty much all motherboards will have both ports available. What are you planning to use for the computer, a [mini-ITX]("http://www.mini-itx.com/store/?c=2") board?Planning is a strong word... xD

But hey sweet I will likely be using that =b

---

