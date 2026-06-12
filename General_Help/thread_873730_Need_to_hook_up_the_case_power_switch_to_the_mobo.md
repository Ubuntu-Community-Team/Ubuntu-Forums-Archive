---
title: "Need to hook up the case power switch to the mobo"
date: 2008-07-29
forum: General Help
---

### Post by PsychedelicWonders on 2008-07-29
Alright, I need to hook up the power supply on the outside of the case to turn it on and off manually.

Now behind the external power button is a Power Switch circuit.  Here it is here...

[IMG]http://i208.photobucket.com/albums/bb38/PsychedelicWonders/Picture001.jpg[/IMG]

Notice there are the 4 pins on the bottom and they are labeled...

GRD +12V PW-SW
           
So what 2, of those 4 prongs do I plug this cable into (the cable says POWER SW on the actual plug)...

[IMG]http://i208.photobucket.com/albums/bb38/PsychedelicWonders/Picture005.jpg[/IMG]

Now obviously the other end of the plug goes into the bridge on the mobo.

thanks guys.

---

### Post by Potatoj316 on 2008-07-29
I would guess +12 and ground, but dont take my word for it, I am just guessing.  It might damage something if hooked up incorrectly.  Try looking up what those other 2 pins are/what their letters stand for.

---

### Post by Samuel-Sama on 2008-07-29
I think it should go on the PW-SW pins, look for a + sign on one of them, the red wire should go on the + pin.

---

### Post by tamoneya on 2008-07-29
definately pw-sw.  The 12v and gnd pins are most likely just controlling the LEDs.

---

### Post by Potatoj316 on 2008-07-29
yup, dont know what Im talking about.  

Remember: Documentation is your friend, so is google.

---

### Post by tamoneya on 2008-07-29
> **Potatoj316 said:**
> yup, dont know what Im talking about.  

Remember: Documentation is your friend, so is google.

you learn something every day.  

The way to think about it though is that a switch never uses power.  Basically the motherboard puts out 5 V on one of the pins and sees if it comes back on the other.  It doesnt even matter in which order the pins are connected.

---

### Post by PsychedelicWonders on 2008-07-29
Please only answer if you are 100% sure.

So the POWER SW gets plugged into the 2 prongs labeled PW-SW?

Does it matter what color wire is on the PW?

I'm not sure what LED's this computer case actually has on it... I dont have a wire to hook up LED's.

If I had a wire and i took it from the GRD +12V... where would it then go on the mobo?

---

### Post by stalkingwolf on 2008-07-29
If you put your switch on the GRD and 12v pins the first time
you turn it on you will have a direct short.  A switch is a simple make/on or break/off circuit. so when you turn it on with it connected to the GRD/12v pins it will run power directly to ground.
Think about touching the ends of jumper cables together or when
you touch the end of the rod to the metal with an arc welder.

---

### Post by PsychedelicWonders on 2008-07-29
alright, so POWER SW to PW-SW.

thanks guys.

going to plug it on on lunch.

---

### Post by tamoneya on 2008-07-29
> **PsychedelicWonders said:**
> Please only answer if you are 100% sure.

So the POWER SW gets plugged into the 2 prongs labeled PW-SW?

Does it matter what color wire is on the PW?

I'm not sure what LED's this computer case actually has on it... I dont have a wire to hook up LED's.

If I had a wire and i took it from the GRD +12V... where would it then go on the mobo?

I'm sure that you want PW-SW.  There is no need for orientation as switches work no matter which way you connect them.

---

### Post by PsychedelicWonders on 2008-07-29
There is no need for orientation as switches work no matter which way you connect them.

What do you actually mean by that?  the idea and terms are kinda new to me... what do you mean orientation of the switches work either way?

---

### Post by tamoneya on 2008-07-29
> **PsychedelicWonders said:**
> There is no need for orientation as switches work no matter which way you connect them.

What do you actually mean by that?  the idea and terms are kinda new to me... what do you mean orientation of the switches work either way?

I mean it doesnt matter in which order the wires are connected.  Red could go to PW or SW.  Same for black.  This is because a switch is just a connection or lack of connection.  It doesnt have any directionality (firefox says that is a word).

---

### Post by PsychedelicWonders on 2008-07-29
alright thanks for the help, power switch is all up and running.

here is my mobo...

[http://c1.neweggimages.com/NeweggImage/productimage/13-131-277-05.jpg](http://c1.neweggimages.com/NeweggImage/productimage/13-131-277-05.jpg)

On the right middle/top are the 3 blue USB ports and the 1 red firewire port.

Now I have 3 addtional wires that I need to figure out where to hook up.

2 are usbs
1 is a firewire

Here is a picture of the 1st usb, it goes to my card reader (sorry for the shitty pictures, i have a cannon 5.0 megapixels and dont know why they are so shitty)... it is a 3-1 and is labeled as...

VCC1
USB 1-
USB 1+
GND

[IMG]http://i208.photobucket.com/albums/bb38/PsychedelicWonders/Picture004.jpg[/IMG]

Now I take this and plut it right into the actual USB port on either side correct?  No bridge is needed?

The pins in the port of the USB goes like...

USB+5V    USB+5V
USB_P11-  USB_P12-
USB_P11+  USB_P12+ 
GND       GND
          NC

Now these numbers range in numerical value from 7-12 between all three usb ports... does that mean I can hook up 2 addtional mini usb cables to each single port?  

There by giving me 6 total mini usb ports?

---

### Post by tamoneya on 2008-07-29
> **PsychedelicWonders said:**
> alright thanks for the help, power switch is all up and running.

here is my mobo...

[http://c1.neweggimages.com/NeweggImage/productimage/13-131-277-05.jpg](http://c1.neweggimages.com/NeweggImage/productimage/13-131-277-05.jpg)

On the right middle/top are the 3 blue USB ports and the 1 red firewire port.

Now I have 3 addtional wires that I need to figure out where to hook up.

2 are usbs
1 is a firewire

Here is a picture of the 1st usb, it goes to my card reader (sorry for the shitty pictures, i have a cannon 5.0 megapixels and dont know why they are so shitty)... it is a 3-1 and is labeled as...

VCC1
USB 1-
USB 1+
GND


Now I take this and plut it right into the actual USB port on either side correct?  No bridge is needed?

The pins in the port of the USB goes like...

USB+5V    USB+5V
USB_P11-  USB_P12-
USB_P11+  USB_P12+ 
GND       GND
          NC

Now these numbers range in numerical value from 7-12 between all three usb ports... does that mean I can hook up 2 addtional mini usb cables to each single port?  

There by giving me 6 total mini usb ports?

yes that would be correct.

---

### Post by PsychedelicWonders on 2008-07-29
Alright now next for the firewire situation...

First off, the firewire isnt long enough to reach the port on the mobo... so are there firewire internal extension cords?

There were 7 "mini" plugs all coming out of the firewire.

I've hooked 6 of the 7 up to the red bridge, the final yellow mini plug that is left labeled VCC. I need help figuring out exactly where the last wire goes.

TPA+ TPA-
GRD GRD
TPB+ TPA-
+12v +12V
(Blank) GRD

So the +12v are both open still and so is that last ground.

The firewire started out like this...

[IMG]http://i208.photobucket.com/albums/bb38/PsychedelicWonders/Picture002.jpg[/IMG]

and now looks like this...(sorry its a really shitty picture)

[IMG]http://i208.photobucket.com/albums/bb38/PsychedelicWonders/Picture003.jpg[/IMG]

---

### Post by tamoneya on 2008-07-29
this site is the first I could found that sells the extensions: [http://www.performance-pcs.com/catalog/index.php?main_page=product_info&products_id=3203](http://www.performance-pcs.com/catalog/index.php?main_page=product_info&products_id=3203)

Feel free to price shop.  They also provide a nice picture showing the pinouts and cabling.

---

### Post by PsychedelicWonders on 2008-07-29
ok so according to their diagram:

VCC goes on the +12V

But which one of the two +12V do I put it on?

The row with the negative or positives next to the number? (TPA+ OR TPA- side?)

---

### Post by tamoneya on 2008-07-29
> **PsychedelicWonders said:**
> ok so according to their diagram:

VCC goes on the +12V

But which one of the two +12V do I put it on?

The row with the negative or positives next to the number? (TPA+ OR TPA- side?)

Both 12V pins are the same.  It doesnt matter.  If it says 12 V it is always 12 V.

---

### Post by PsychedelicWonders on 2008-07-29
Alright, I really appreciate the help.

now I have one last series of cables to figure out.

They are in the same fashion as the firewire, where there are 7 "mini" plugs coming out the end of the wire.

they go to my front panel and go to a mic port and an speaker in/out of some kind.

The picture I actually listed above is of this cable I am speaking of now.

These are the following labels on the miniplugs in no particular order:

RET-L
RET-R
GROUND
R OUT
L OUT
MIC IN
MIC PWR


there is another area on the mobo that just has a bunch of pins itself but the labels references the following and is labeled as:

Legacy AC 97 audio pin definition:

NC       / LINE OUT L
(BLANK)  / NC
NC       / LINE OUT R
NC       / MICPWR
AGND     / MIC2

I can figure out easily where the 

R OUT
L OUT
MIC PWR

But where do the remainder 4 mini plugs go?...

RET-L
RET-R
GROUND
MIC IN

---

### Post by tamoneya on 2008-07-29
one of them is AC 97 the other is intel HD audio.  They are backwards compatible. Look at this page for instructions: [http://www.intel.com/support/motherboards/desktop/sb/CS-015851.htm](http://www.intel.com/support/motherboards/desktop/sb/CS-015851.htm)

---

### Post by PsychedelicWonders on 2008-07-29
yeah im not doing the HD... the layout I gave you was for the 97 series... 

Now i just gotta figure out where those other 4 mini plugs go... nothing really makes sense or matches up with what i have compared to that chart?

---

### Post by PsychedelicWonders on 2008-07-29
.

---

### Post by PsychedelicWonders on 2008-07-30
Legacy AC 97 audio pin definition:

NC / LINE OUT L
(BLANK) / NC
NC / LINE OUT R
NC / MICPWR
AGND / MIC2

I can figure out easily where the 

R OUT
L OUT
MIC PWR

But where do the remainder 4 mini plugs go?...

RET-L
RET-R
GROUND
MIC IN

heres the chart in case someone needs a reference:

Pin  Signal Name  Description  
1 MIC Front panel microphone input signal (biased when supporting stereo microphone) 
2 AUD_GND Ground used by analog  
3 MIC_BIAS Microphone power / additional MIC input for stereo microphone support 
4 AUD_GND Ground used by analog audio circuits 
5 FP_OUT_R Right channel audio signal to front panel (headphone drive capable) 
6 FP_RETURN_R Right channel audio signal return from front panel (when headphones unplugged) 
7 AUD_5V Filtered +5 V used by analog audio circuits 
8 KEY No pin 
9 FP_OUT_L Left channel audio signal to front panel (headphone drive capable) 
10 FP_RETURN_L Left channel audio signal return from front panel (when headphones unplugged)

---

### Post by tamoneya on 2008-07-30
RET-L and RET-R are the returns.  They are pins 10 & 6.
GROUND = AUD GND 2 or 4 will work.  Doesnt matter which.
MIC IN = MIC  pin 1.

---

### Post by PsychedelicWonders on 2008-07-30
And then the MIC PWR just goes to pin # 3 labed MIC_BIAS right?

I have a blue usb bridge left over... can I plug these mini cables into this bridge and then plug it into the mobo so it will be a million times easier to install then putting each mini plug right on the mobo?

And which way do i put the motherboard to know which pin is 1 and which is 10?  Is the 10th pin towards the back of the mobo?  

Is that picture looking from the front of the board?

This is the actual configuration listed in the mobo book... does it matter that the labels are different from that 10 pin config link you gave me?

Legacy AC 97 audio pin definition:

NC / LINE OUT L
(BLANK) / NC
NC / LINE OUT R
NC / MICPWR
AGND / MIC2

---

### Post by PsychedelicWonders on 2008-07-30
bump

---

### Post by tamoneya on 2008-07-30
> **PsychedelicWonders said:**
> bump

please dont bump for 24 hours.

---

### Post by PsychedelicWonders on 2008-07-30
sorry.

But can I use that extra blue bridge I have for these mic and speaker mini plugs?

or do I have to put them on one by one?

---

### Post by tamoneya on 2008-07-30
No. you cannot connect audio wires into the blue USB header.  They arent the same thing.

---

### Post by PsychedelicWonders on 2008-07-30
dang.  alright.  its going to be hard it seems.

thank you very much for all your help.

---

### Post by PsychedelicWonders on 2008-07-31
I tried to put the mini plugs on last night, but realized I dont know which way the numbers go.  

Is it...

678910
12345

or

246810
13579

?

---

### Post by PsychedelicWonders on 2008-07-31
also to reference above, is there any type of bridge to help plug the mini plugs into?

---

