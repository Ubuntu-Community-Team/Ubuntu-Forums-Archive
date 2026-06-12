---
title: "unknown Asus desktop"
date: 2011-01-30
forum: Hardware
---

### Post by Antarctica32 on 2011-01-30
I just got an Asus desktop. It has no labels, markings, or stickers besides one that just says "Asus" and another that says "windows XP". There was no HD or RAM in the thing. On the inside printed on the network cable to motherboard attachment it says "Phoenix Bios D686 Bios Phoenix 1998 148209448". On the back it has 4 USBs, 1 Ethernet cable slot, 1 mouse PS2, 1 keyboard PS2, 1 s/pdif out, 1 parallel port, 1 VGA, 1 audio input, 2 audio output mini-jacks, 1 serial port. The power supply is a VPower 400 Wat "made for Pentium4" model number LC-8400BTX. It has a 3 1/2 floppy, and a CD rewritable ultra speed. There is a little door thing with 2 additional frontal USBs behind it. The power button looks kinda like pac-man. The CPU is under a fan and I have had some trouble removing cpu fans in the past, so I don't know the CPU.

---

### Post by cascade9 on 2011-01-31
That is probably not an 'asus desktop', its just a 'white box' running an asus motherboard. 

All that I can say from the shots is that is a P4 motherboard, probably a P4SP-MX-

[http://www.asus.com/product.aspx?P_ID=ZGKRf3vVr8Bq39Gm](http://www.asus.com/product.aspx?P_ID=ZGKRf3vVr8Bq39Gm)

The easiest way to tell if I'm right is to check the model number that asus normally screenprints onto the motherboard, typically its between the PCI slots. 

To get much more than that you would need to boot the computer. The CPU model, motherboard model number, BIOS version (and lots of other info) you can see from the BIOS. A liveCD, then running the command-

sudo lshw 

Should get you even more information on the system.

---

### Post by Antarctica32 on 2011-01-31
Well it's definitely an asus cuz the white box says ASUS near the bottom. I plugged in an 80GB HDD and 512MB RAM and installed 10.04. The CPU is a Pentium4. The reason I didn't just lift up the cooling fan and look for what it says on the CPU was because one time my Dad did that and he bent the little wires on the bottom. He tried just putting it back in but it didn't boot. Luckily I was able to very carefully bend the wires back in place. I know I could of just used the Bios to see what CPU it was, but I am going to use the machine for my eagle project. [http://ubuntuforums.org/showthread.php?t=1676724]("http://ubuntuforums.org/showthread.php?t=1676724")
The link was very similar, but mine has 4 RAM slots not 2. You were right there was a model number, but it's very old and I can barely read it. I'll try reading it latter on.

---

### Post by Antarctica32 on 2011-01-31
Here it is,
P4S533-MX

I already researched all I could on it. It looks like I got a really good deal:

P4S533-MX motherboard
P4 CPU
very good condition 400 Watt power supply
good condition floppy drive, not that I'll use it
old Cd rewrite drive
durable Asus computer case

All for just $12 total
:guitar:

---

### Post by cascade9 on 2011-02-01
> **Antarctica32 said:**
> Well it's definitely an asus cuz the white box says ASUS near the bottom.

That sounds like acase badge sticker, and asus gives them out with motherboards ;) I know I've seen those cases before as well. 

Then again, I cant find the P4S533-MX which is typical of any manufacturering that asus does for 3rd parties. 

I'd still guess that its an asus board in a white box, 'corporate' computers never came in that style case, and asus wasnt making retail desktop systems at that time as far as I know (I'd expect a lot more asus branding if it was made by asus as well)

---

### Post by Antarctica32 on 2011-02-01
OMG your right. The Asus symbol is a sticker. On closer review it reads, "powered by," in very small letters, then in huge letters "Asus". Also the motherboard appears to not fit the case very well. The motherboard takes only 3 drives, but the case was made for 5. Also, the chassis the CD drive is mounted to on the inside was made for 6. The power supply is overkill for the motherboard. The case also has 3 extra fan slots. What I have must be a PC someone made themselves. This would also explain how the RAM and HD were missing as the previous owner must have been a techy, and most people have no clue what RAM even stands for. You were right all along. Thanks       

The only question I have is why did the previous owner throw it out? Techys don't tend to throw out old PCs especially ones they make themselves, they usually fix them or make them better. :-k

---

### Post by cascade9 on 2011-02-02
I'd doubt that its been made by a 'techie'. Well, it was probably assembled by one, but not made for his/her (its? some techies you'd never know) use. 

The microATX motherboard in a full ATX case is typical of smaller computer companies. Rather than buy 1 case for the top of the line, full ATX systems, and another case for smaller microATX systems, they would rather just buy 1 case in as big a number as they can, as this makes it cheaper. It also helps with stock control, inventory, etc.. 

That would also be why there is a 400watt power supply in there. Though you've got to be careful of 'yum-cha' power supplies, they have been known to just slap a sticker saying whatever power output they think will sell on power supplies, even if the power supply cant even get close to that output. 

Pulling the RAM and HDD is pretty common, even for 'normal' users. 

As for why its been got rid off...its a farily old computer, unless I'm having another blonde moment the motherboard isnt up on the asus website (which makes updating the BIOS pretty much impossible, and getting new drivers more difficult). The real kicker is that you cant run the faster 800MHz FSB P4s, or DDR-400 (probably limited to DDR-266 or 333) in that board, and the 800MHz FSB P4s are a nicer CPU than the 533MHz P4s.

---

