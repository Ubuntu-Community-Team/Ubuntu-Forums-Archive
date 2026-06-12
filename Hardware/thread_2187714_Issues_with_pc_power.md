---
title: "Issues with pc power"
date: 2013-11-13
forum: Hardware
---

### Post by ***J*** on 2013-11-13
A couple weeks ago one of the wires coming out of a hdd hot swap rack ([this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817990016") one to be exact) caught on fire inside of my tower which I had to douse with water to put out. After taking it out my computer surprisingly ran fine for a while but in the last couple of days the following issues have started to surface:

1. Ethernet cable only works intermittently.
2. To get the computer to boot up I have to first either unplug and replug the psu or turn the button on the back of the psu on and off.
3. Unplugging  and replugging the psu gets the computer to boot up if I wait a while before plugging it back in but if I press the  off on button on the back of the psu the monitor doesn't come on.  
4. I've also had the computer shut off when I was in the middle of watching a hd movie though this has only happened once so far.

Unfortunately I don't have a spare PSU to test this with. What do you guys think are likely causes for these problems and what can I do about it? 
Is there any software that I can download to test the psu or motherboard? All the utilities on my motherboard's website are for windows as far as I can tell.

What I've done:
Moved the RAM stick into another slot.
Took out the CMOS battery, tested it with a multimeter (was 3.01), and put it back in.
Tested PSU with multimeter and all the volts were normal.
Made sure all fans were working.
Checked for loose plugs.
Cleared dust.
Went into bios when starting up to check temperatures and got these:
Current System Temperature 27 C
Current CPU Temperature 64 C
Current CPU Fan Speed 3229 RPM
However when using psensor I got this when watching a video:
CPU Temp - Value: 46 C Min: 35 C Max: 55 C

My Motherboard: GA-970A-D3 [http://www.gigabyte.us/products/product-page.aspx?pid=3908#ov](http://www.gigabyte.us/products/product-page.aspx?pid=3908#ov)
My Power Supply Unit: PC Power & Cooling 750W Silencer MK II PPCMK2S750 [http://www.amazon.com/gp/product/B003U29C3Q/](http://www.amazon.com/gp/product/B003U29C3Q/)
My OS: Ubuntu 12.04 LTS
MY CPU: AMD FX-8120 Zambezi FD8120FRGUBOX [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103961](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103961)


If you need any more information let me know.

---

### Post by ***J*** on 2013-11-14
I measured my psu with a multimeter this morning and all the readings came out normal. Does this rule it out as a problem?

---

### Post by ***J*** on 2013-11-15
bump

---

### Post by tgalati4 on 2013-11-15
It's possible that the moisture caused corrosion or (more likely) as the water dried, it left conductive mineral deposits on the motherboard.  Try taking the motherboard apart.  Use isopropol alcohol (get the highest percentage you can find) and clean the board with cotton swabs.  Use a very bright light and magnifying glasses and carefully inspect the entire motherboard for corrosion or other damage.  Let the board dry for 3 days in sunlight resting on a bed of dry rice.  Then reassemble in a minimum configuration--minimum RAM, and a CD/DVD and boot an Ubuntu Live DVD or USB stick.  Let the machine run for several days in the live session and take notes of what works and what doesn't.  

The symptoms that you describe indicate possible damage to the support chips which provide ethernet and on-board graphics.  How much water did you use to put out the fire?

 I have clients that can't understand why I can't rebuild a PC that has been struck by lightning.  Fire, water, and smoke are a close second to killing a PC.

---

### Post by ***J*** on 2013-11-15
Thanks for the post. When it caught on fire I immediately plugged everything out opened the case and dumped a fairly small amount on the burning wire. As far as I can remember not much water came into contact with the motherboard since the wire was to the top right of it and I was trying to avoid hitting it (I'd hate to see what condition it would be in had I dropped more water on it if even this small amount is causing damage). I'd still like to know how exactly the hot swap rack caught on fire, needless to say I'll be taking a lot more precautions with computers and won't be leaving mine on 24/7 under my bed anymore. Luckily I was home to put the fire out this time. Earlier today I thouroughly cleaned under the cpu fan and around the tower with a vacuum which according to the bios decreased the temperature around 10 degrees. I'll be doing your suggestions tomorrow.

---

### Post by tgalati4 on 2013-11-16
Computers need to be kept 1 foot off of the floor, otherwise, they will accumulate too much dust and that will cause problems.

Due to the complex mechanism of the rack, perhaps a 12VDC wire got pinched?

---

### Post by ***J*** on 2013-12-02
Some updates:
Cleaned the board with alcohol and bought a new psu; both of which didn't remedy the situation unfortunately.
The problem with the internet was actually being caused by a faulty ethernet cord.
A new temporary trick I found out recently is to hold the power button for a few seconds instead of pressing it. This has been getting the computer to boot up but I'd still like a permanent fix. Since the psu wasn't the problem I'm guessing either the motherboard or the front case wire connect the power button to the motherboard is the culprit unless anyone else has any other ideas.

---

### Post by ***J*** on 2013-12-08
When I finally got my computer to boot up today I got a black screen with the following message:
"main bios checksum error retrieving recovery source from"
There was more but I didn't have time to write the rest down before the screen went off. After this the computer booted up. Does anyone know how this relates to my problem and how to go about fixing it?

---

### Post by ***J*** on 2013-12-09
bump

---

### Post by ***J*** on 2013-12-24
[COLOR=#000000]Ever since the "main bios checksum error" incident I've been able to power up my pc by pressing the power button without trouble. Recently however if I stepped on my headphones cord or pull on it my monitor goes black temporarily for a second or two and comes back on. This has also started happening today without touching the headphones. I don't think the monitor is to blame since the light on it's power button doesn't change when it goes black. Does anyone know what's happening and what I can do about it?[/COLOR]

---

