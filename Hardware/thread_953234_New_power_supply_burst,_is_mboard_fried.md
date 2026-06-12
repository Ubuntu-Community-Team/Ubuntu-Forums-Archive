---
title: "New power supply burst, is mboard fried?"
date: 2008-10-19
forum: Hardware
---

### Post by mridkash on 2008-10-19
Hello, 
I bought a new power supply after the old one was aging (4yrs) and making weird noises. 
After replacing power supply the computer worked good for 5-6 hrs, but when I started memtest (for checking new RAM) barely 5 seconds after, the computer shut down, and *bang*. The power supply burst with a flash.
Is the motherboard fried? I'm afraid. I reconnected the old power supply to test and pc doesn't start. The light on motherboard glows but it doesn't start.
Motherboard is Intel 915 G with P4 HT 3 ghz prescott processor and 1.5 Gb RAM

How do i check the mboard. And can I claim damages from the power supply manufacturer if the mboard is really damaged?

Thanks

---

### Post by jerome1232 on 2008-10-19
Ouch man, That has the potential of taking anything out in your case. I've had 2 hdd's destroyed by a failing power supply once.

It could be your ram, processer, motherboard, or video card that fried. From the symptoms you described I would look at video card/mobo first. (since if the processor/ram are dead usually the board beeps at you or flashes the keyboard lights rapidly, displays a rapidly blinking cursur... **something** usually happens).

---

### Post by ardvark71 on 2008-10-20
> **mridkash said:**
> Hello, 
I bought a new power supply after the old one was aging (4yrs) and making weird noises. 
After replacing power supply the computer worked good for 5-6 hrs, but when I started memtest (for checking new RAM) barely 5 seconds after, the computer shut down, and *bang*. The power supply burst with a flash.
Is the motherboard fried? I'm afraid. I reconnected the old power supply to test and pc doesn't start. The light on motherboard glows but it doesn't start.
Motherboard is Intel 915 G with P4 HT 3 ghz prescott processor and 1.5 Gb RAM

How do i check the mboard. And can I claim damages from the power supply manufacturer if the mboard is really damaged?

Thanks

Hi...

Oh, wow, I'm very sorry this happened to you! :(

What brand of PSU was this? It's very likely that your motherboard is fried along with (possibly) your other devices like hard drives, any cards plugged into the motherboard's BUS ports, CD-ROM drives, etc. 

I had a hard drive go out with a literal bang one time (on a computer that I was working on) and it took out the IDE controllers on the motherboard. :(

If the motherboard won't POST with any PSU, I would think that it would definately be fried. I'm afraid I don't know of any testing software or equipment that you could use to confirm it, least of all for free. :(

I wish I could be of more help. :( Let us know how everything turns out.

Best Regards...

---

### Post by mridkash on 2008-10-20
I sent the motherboard for checking at a local pc service center and the person has diagnosed that the motherboard has some faulty component that is shorting the power supply. He even said that this mboard burnt one of his test psu too! :shock:
What to do now? Should I get this 4yr old mboard replaced by a newer one? or send it for repair at intel service center? :confused:
I should ask my dad!

---

### Post by jerome1232 on 2008-10-20
motherboards are fairly cheap these days, probably more cost effective to replace it.

---

### Post by Bucky Ball on 2008-10-20
> **jerome1232 said:**
> motherboards are fairly cheap these days, probably more cost effective to replace it.

+1. Did the pc tech tell you that was the only problem? If the tech had a PSU blown up knowingly by this shorting motherboard and didn't tell you of the risk in the first place, I might be thinking about a new tech!

---

### Post by mridkash on 2008-10-20
We've decided to replace the board. But now the question comes what to do with the old one. The processor is fine p4 ht 3ghz, the RAM is brand new DDR1 1.5 gb, Nvidia Video card is good too. And these things might not be compatible with the new board. 
So I should sell them off independently. Maybe, locally or on ebay etc!

---

### Post by jerome1232 on 2008-10-20
It's not hard to find a board with the same specs! I've got three here that my processor/ram/video card work with.  Do you know what slot your cpu uses, what speed the ram is and if the video card is vga or pcie?

---

### Post by ardvark71 on 2008-10-20
> **mridkash said:**
> We've decided to replace the board. But now the question comes what to do with the old one. The processor is fine p4 ht 3ghz, the RAM is brand new DDR1 1.5 gb, Nvidia Video card is good too. And these things might not be compatible with the new board. 
So I should sell them off independently. Maybe, locally or on ebay etc!

Hi...

Like Jerome has said, you can find another board that can use your other components and save quite a bit of money at the same time! :) I'm just hoping those same components were not affected by the blowout.

If you provide the specs that Jerome requested and give a price range along with what you use your computer for (i.e., games, etc.,) I'm sure that either he, myself or someone can provide a link to a new board that will fit your needs.

I have to admit, I was slightly surprised the motherboard was the cause of all of this. :shock:

Best Regards...

---

### Post by Bucky Ball on 2008-10-20
Yep, you could get out of this paying for a new board only (around $60-$80 Australian for a fine board for those specs - maybe about $40us) or spending about 5+ times that much on a new set-up. Of course, if that is what you really want and have the money, do both! But you have the existing hardware and we should keep it running for as long as it fits the need. Maybe a rock solid Ubuntu Studio for audio/video/multimedia creation? The P4 would be nice for that.

As mentioned, get the socket of your old P4 and work from there to include your RAM and vid card. 
Run that hardware into the ground, it doesn't grow on trees! :)

---

### Post by mridkash on 2008-10-21
Thanks, I appreciate your help.
The specs I know are, 
**Motherboard**: Intel 915 GAG
**Processor**: Pentium 4 with HT 3Ghz, Below the socket on board its written LGA 775, is this the socket no. ?
**RAM:** 2x256 Mb DDR (400) and 1x1Gb Transcend DDR (400) (Brand New)
**Graphics:** Nvidia GeForce 6600 512 Mb PCI Card

We also plan to sell off the screen and get a bigger one. My parents have to use spectacles to read and the screen size is small for bigger fonts.
**Screen:** 15' Acer TFT LCD

Today, I'm going back to college in city and will get the board checked there. If it gets repaired for a few bucks then its fine, otherwise, I plan to sell off these parts and get all new and reliable mboard. 

The computer use:
Dad checks email, visits websites, and writes, prints documents
Mom checks stock market, visits websites, make somethings in gimp, inkscape etc, music
Sis websites, music, gimp, and wants to play the new [yofrankie]("http://www.yofrankie.org") game

Thanks again!

---

### Post by Bucky Ball on 2008-10-21
Getting the board repaired will probably set you back more than buying a new one.

Pentium 4 with HT 3Ghz, Below the socket on board its written LGA 775

Yes, that is a socket 775. Same specs as processor I have in my desktop DAW running UbuntuStudio and virtually the same video card. I have a couple of GB of RAM. Machine will be cool with these specs and to do what they are looking to do with it.

The motherboard I am using is an ASRock ConroeXFire-e SATAII which cost me about $70 Australian about 3 years ago; bit dated now but is capable of a lot more than what I have hanging off it so good for upgrading (one of the reasons I bought it). The components you mention would drop straight on. The new versions are about $50 AUS so as I say, think carefully about the price of getting this board fixed against price of a new one.

Something to think about definately is that a lot of modern boards don't offer a lot in the way of IDE. If you have a few drives and a couple of cd/dvds that are all IDE, the board I mention only has 1 IDE cable (effectively two IDE devices) and 4 SATA ports. This seems to be becoming more and more the case. Whatever you buy, think Green Power! Look for RoHS standards on all components and '80+' recommendations on power supplies. Hard drives are also going 'green' now. I bought a WD Green Power 500Gb drive the other day which uses about 2/3 power, runs pretty much cold and silent. Good luck whatever you end up doing. :)

---

### Post by mridkash on 2008-10-21
I have 2 hdds both SATA (WD 80gb and Hitachi 250 gb) and plug into the small SATA ports, and 1 Sony dvd writer which goes into IDE, everything else goes into usb. So these are compatible with newer boards i believe.

---

### Post by Bucky Ball on 2008-10-21
All looks good to go. Just make sure there is at least one IDE on the board, which there usually is but that will eventually disappear I would imagine ... on of these days. :)

---

