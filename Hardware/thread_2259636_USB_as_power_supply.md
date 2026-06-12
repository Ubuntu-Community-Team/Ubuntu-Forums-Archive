---
title: "USB as power supply"
date: 2015-01-05
forum: Hardware
---

### Post by JimmyJames89 on 2015-01-05
Hey all, 

In the interest of being efficient I soldered a USB cable to a DC plug for my little 5V 5-port switch. 


[ATTACH=CONFIG]259023[/ATTACH]

Covered it in hot glue and wrapped it in electro tape. Now, this little box gets a bit hot. I wonder how this would fare on a headless debian server, USB powered from the server? Could it handle being on 24/7? It looks a little bit too cheap and chinesey to keep on all the time. 

I have a fair few devices @ 5v that I'd like to do this to. Has anyone attached 12v peripherals into a computers PSU? 

James 

;)

---

### Post by Bucky Ball on 2015-01-05
*Thread moved to **Hardware**.*

This is really a support question and I have moved it here to improve your chances of getting advice quickly (as what you're doing needs some). 

Yes, dodgy. The fact that things are getting hot is an indication. Is that glue and other stuff you've put on there flammable? 

Your computer has a 5V rail, not 12V, so attaching 12V devices to USB ports is not a good idea. Connecting 12V devices directly to the PSU somehow is dodgy and you will need to do some (accurate) calculations to make sure you are not going to destroy the PSU, the device, or worse. How do you intend to attach them to the PSU? Via USB, or improvising another plug from a cable hanging out of the PSU directly???

Hopefully someone with elec. experience and know-how will chime in soon, but unless you're an electrical engineer or are very across what you're intending to do (and as you're asking this question that doesn't seem likely), for your own safety and the preservation of your hardware, I'd hold your fire (so to speak, but that may be the operative word) until you get some expert advice on this.

---

### Post by coldraven on 2015-01-06
You need to check the box's current consumption. Look at it's original power supply, it will say something like Output 5V 1A.
According to this link a standard USB port can only deliver about 150mA. If the box is using more than that you will fry your motherboard!
[http://superuser.com/questions/690074/what-is-the-power-output-of-a-usb-port](http://superuser.com/questions/690074/what-is-the-power-output-of-a-usb-port)

---

### Post by JimmyJames89 on 2015-01-08
*dupe*

---

### Post by JimmyJames89 on 2015-01-08
Thanks for the link coldraven! Thanks for renaming and moving the thread. Long time reader, first time poster! 

According to the STLabs manual [here]("http://www.sunrichtech.com.hk/UploadFiles/Products/2014011416072085/Manual%28N-143%29.pdf") the box is drawing 600ma. 

From your link: "To clarify: Some people  misunderstood the usb spec. A usb port has no power limit. Only the usb  device is not allowed to draw more than 500 mA (USB 2.0) or 900 mA (USB  3.0). But some of them don't respect this limit e.g. several hard  drives. So it depends on the manufacturer." 

Ouch, should have just stuck to the universal DC output adapter I started with. Of course, in the interests of efficiency in a room with a VHS DVR stack, two computers, a scanner, a radio and 4 outlets I was hoping to keep some space free. 

With regards to the heat of the switch, the heat was actually worse when plugged in to the mains. This universal adaptor supports 5v @ 1A. Photo attached. This is an average quality device, it works, but I do expect it to get hot. I don't keep computers/switches on 24hr unless I have to. 

 Besides the Android apps and the USB power metre that Super User discussed, does Linux have any software that could monitor the power/current from a USB port? 

With regards to the 12v device, it's a car phone with no power supply, just cables - a Nokia 616. Really a nerdy novelty - I can screw the components into my desk and the device switches on with the computer when I start work in the morning. This device looks like a different power source could be easily sourced and used. 
 
I am a bit fascinated by the PSU - I like the idea of using the PSU as  like, one transformer for several devices as opposed to a multi-board  full of transformers. But hey, I ain't no engineer and agree totally that it shouldn't be attempted without more know how. 

Of course, more research. Same goes for my little Time Base  Corrector - also drawing 5V. It could easily be powered from the DVR  that does most of the recording. Will investigate before soldering  anything else!

On a slight tangent But hey, I ain't no engineer. 

[EDIT] The cable in the switch has no pin and keeps popping out. Lost the final revision. *Reaches for hot glue gun*

---

### Post by pqwoerituytrueiwoq on 2015-01-08
yes, i have attached keyboard LEDs to the 12v internal PSU (yellow + black wires) (my moms computer)
i have also used a powerblock with a molex output to power a rPi, some 12v leds, and a 12v network switch
[http://imgur.com/a/qQKFx](http://imgur.com/a/qQKFx)

USB3 makes a decent source for 5v hardware as it has 900ma (0.9A)

if you dont have the proper amperage for the voltage the voltage will drop and the amperage will go higher, more amps means more heat

when adding stuff to your PSU check the amperage it needs and the label on the PSU
* there are a lot of low quality PSUs out there you can buy that have labels that are a complete lie

---

### Post by pqwoerituytrueiwoq on 2015-01-08
> **coldraven said:**
> You need to check the box's current consumption. Look at it's original power supply, it will say something like Output 5V 1A.
According to this link a standard USB port can only deliver about 150mA. If the box is using more than that you will fry your motherboard!
[http://superuser.com/questions/690074/what-is-the-power-output-of-a-usb-port](http://superuser.com/questions/690074/what-is-the-power-output-of-a-usb-port)
USB 2 should do 500mA, i would expect the connected device to either not run to take damage depending on the circuitry on the inside of the PC (motherboard/psu)

---

### Post by JimmyJames89 on 2015-01-08
Cable Porn! :P Amazing. 

"Basic Electricity" in the background. A carefully placed, quiet hint? Check the two dollar PSU I got from an op shop. Match in heaven? 

Encouraging to know that splicing in cables to the 12v of the PSU shouldn't be blow your house up terrifying. I guess I'll have to buy that book. 

I'm running a Lenovo Think Centre M57. Fished it from an op shop for $10 - like most of my hardware. The schematics/motherboard manual shouldn't be too hard to come across. I'll get digging. There's a 100ma difference but no sign of damage or frying just yet. 

Give your cat a scratch for me, [**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458") ;)

---

### Post by Bucky Ball on 2015-01-09
> **pqwoerituytrueiwoq said:**
> 
* there are a lot of low quality PSUs out there you can buy that have labels that are a complete lie

Be very aware of this. If you don't know the precise specs of your PSU, don't go there, and if you are using a generic silver box PSU, just forget it. ;)

Check the fourth link in my sig re. this. I am determined to eradicate generic silver box PSUs!

---

### Post by coldraven on 2015-01-09
> According to the STLabs manual [here]("http://www.sunrichtech.com.hk/UploadFiles/Products/2014011416072085/Manual%28N-143%29.pdf") the box is drawing 600ma. 

My original post was based on guesswork but 600mA sounds about right. A DC power supply should always be able to supply slightly over the requirements of the device it's powering. As mentioned above, with cheap gear you cannot always trust the labels :(
Time to buy some more AC power sockets! :)

---

### Post by efflandt on 2015-01-09
I used a PSU out of an old PC to charge RC batteries with a 12V input electronic battery charger made for charging LiIon batteries. I found instructions for that somewhere. There is a 5V circuit that needs to have a load on it, so a simple switch connecting that load (10 ohm 5 watt resistor which on 5V is 2.5 watts) turned all PSU circuits on. I also connected a 12V LED across connections to the resister which worked fine on 5V as power indicator. I guess if you tied that 5V circuit to a USB cable for something that needed around 500 mA (0.5 A), that would work in place of the resistor.

However, the PSU has a protection circuit on it to prevent shorts and connecting the battery charger after the PSU was on was enough of a sudden draw (maybe due to a capacitor in the charger) that the PSU would shut down. But if I connected the battery charger first, then turned on the PSU, everything worked fine. I think that old PSU only had about an 8 amp 12V circuit.

So an old inadequete PC PSU can possibly be recycled for other uses.

---

### Post by Bucky Ball on 2015-01-09
> **efflandt said:**
> ... the PSU has a protection circuit on it to prevent shorts and connecting the battery charger after the PSU was on was enough of a sudden draw (maybe due to a capacitor in the charger) that the PSU would shut down.

Be aware that not all PSUs have safety switches in built. That's why I keep banging on about generic silver boxes. Just cos one does, doesn't mean your does. Be careful. ;)

---

### Post by pqwoerituytrueiwoq on 2015-01-09
Typically DELL PSUs are weak but there labels are not a flat out lie
there are few retail silverbox PSUs i trust (seasonic/antec 380w)
just cause it is a block box does not make it good

if you are just adding 1amp or less you are probably fine, you would have to add up your total amperage pull on each rail to be sure
now if you are using a old PSU for a powerbrick and not powering a computer just short the green wire to a black wire on the 24pin and the unit will turn on (not all PSUs will do 7v when turned on this way)
* there was a time when dell used a proprietary pinset on the 24pin plug and used the same physical plug, consider that a warning (dell loves there proprietary plugs as much as apple)

---

