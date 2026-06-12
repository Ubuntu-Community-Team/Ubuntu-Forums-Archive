---
title: "Someone please help me with my dead hard drive"
date: 2009-05-04
forum: Hardware
---

### Post by cackles on 2009-05-04
I was about to start backing up all my data after I installed a new HDD, so I left the current one on top of my PC, the monitor got knocked, swung round and knocked the HDD off the top of it.

The HDD now makes a clicking sound and a high pitched squeel that comes and goes and the HDD wont get recognised.

The HDD is only a couple of months old, but it contains the last 14 years of my life. The only thing I had backed up was some of the kids photos, Im probably missing a good couple of years of them now along with all my college work and every project Im working on.

A couple of hours and everything was going to be backed up onto my server and another PC in the livingroom. Usually I have multiple copies but I had to move 4 HDDs between 4 PCs so I was left with only one copy of my data.

Ive been looking for sites that show you the most common things that could be wrong and how to repair them, but aside from a few videos that dont show a lot or go into any great detail I cant see what Im looking for. If someone could just please point me in the right direction and help me out Id appreciate it so much its untrue. Even if I need to buy/build something to recover the data and the HDD itself is lost.

There has to be something I can do, I dont want to send it into somewhere that deals with this sort of thing because there is sensitive and confidential data on it as well so its not really an option.

---

### Post by ddrichardson on 2009-05-04
If the drive had a hard enough impact and the platters have contacted you wont get them to overcome the stiction.

I have managed to get drives to run for around 15 minutes for data recovery using the freezing method but be aware that this is a last ditch recovery method. There's an explanation [here]("http://geeksaresexy.blogspot.com/2006/01/freeze-your-hard-drive-to-recover-data.html") but essentially you freeze the drive to contract the platters overcoming stiction then run it up and pull data off like there's no tomorrow.

What he doesn't mention is silica gel packs - if you can get them (they're in shoe boxes) they help prevent the moisture invading the device.

---

### Post by cackles on 2009-05-04
Thanks Ill start reading this now.

One solution I thought of is buying one exactly the same and ripping them both apart and transferring the platters over, but seems a bit insane if theres other methods, just need to find them.

---

### Post by ddrichardson on 2009-05-04
> **cackles said:**
> Thanks Ill start reading this now.

One solution I thought of is buying one exactly the same and ripping them both apart and transferring the platters over, but seems a bit insane if theres other methods, just need to find them.
They use fluid bearings, I don't know your level of electronics knowledge but I'm an electronics technician and I wouldn't attempt that. Dust could also seriously mess things up.

---

### Post by Mortus Pryde on 2009-05-04
Your only other option is expensive and carries not garenties, that would be to find a local forensic data recovery service when they physically dismantle a damaged hard drive then retrieve any raw data they can from the platters and try to reconstruct it. This is of course for extreme measures and only if the data is worth the cost to you.

---

### Post by Mortus Pryde on 2009-05-04
> **ddrichardson said:**
> They use fluid bearings, I don't know your level of electronics knowledge but I'm an electronics technician and I wouldn't attempt that. Dust could also seriously mess things up.

I must agree, the differnce between the extreme measures meathod I suggested and DIY is that forensic recovery services use a clean room, which is part of why it is so expensive.

---

### Post by cackles on 2009-05-04
Looking at where it landed, the fall wasnt very far (about 40cm) so I 'think' (hope and pray) one of the chips or sm components on the outside pcb might have been shorted when it fell. Before I try and freeze it I will order one exactly the same and swap the PCBs over, this way at least Im not opening it up or going to any real extremes. All its it are 4 torx screws and piece of ribbon connector.

If that doesnt work then I will freeze it and if that doesnt work Ill start crying.

When I told my friend about it his reply was 'and your the one that told me to back things up to about 10 different places'.

The data is definately worth recovering.

All this for the sake of a 2 second lapse in concentration.

Thanks for the input.

---

### Post by ddrichardson on 2009-05-04
Its pretty unlikely that a solid state component's damage would produce a noise, that's much more likely to be a mechanical problem. You never know though.

---

### Post by cackles on 2009-05-08
> **ddrichardson said:**
> Its pretty unlikely that a solid state component's damage would produce a noise, that's much more likely to be a mechanical problem. You never know though.



I dont think they are what is making the noise. I think damage (a short) in one or more of them could have resulted in the drive not doing what it should at all. Like how analogue controllers dont go on how much power you apply but they measure resistance. A shorted res could result in the controller thinking the button/stick/trigger is fully depressed. I think its not a bad theory.

Im going with freezing first, because I can basically and my TORX maybe wont be here until Monday, hope they arrive Saturday. Then I will switch out the PCB if freezing doesnt do it for me. Its typical my set starts at T5 and skips to T10, HDDs are about a T8.

Heres the steps I took to freeze it:

1: Took the HDD out of the 24c ambient room and left it in an 18c room.
2: Stuck it in the fridge for a couple of hours with 'Super Cool' on, meant the air would circulate more and less chance of condensation.
3: Filled a bowl with cold, chilled, water :D
4: Put the HDD in a ziplock bag with as many silica paks as I could find and sealed it 75% shut.
5: Dipped the bag with HDD into the water leaving the opened top out the water and zipped it shut. Had to do this carefully. It meant as much air as possible was pushed out by the water pressure.
6: Dried the bag without puncturing it.
7: Put the HDD into the freezer and hit 'Fast Freeze'.

HDD is currently in a -21c environment for the past hour, just chillin out. Speaking of which, thats what Im gonna do for the next 3hrs, because its -21c not -5c.

Coming soon:
What happens when you mix an HDD with memories, a bowl of water, a freezer and a bottle of vodka.

---

### Post by ddrichardson on 2009-05-08
> **cackles said:**
> I dont think they are what is making the noise. I think damage (a short) in one or more of them could have resulted in the drive not doing what it should at all. Like how analogue controllers dont go on how much power you apply but they measure resistance. A shorted res could result in the controller thinking the button/stick/trigger is fully depressed. I think its not a bad theory.
I'm confused with that. It's not a short, V=IR and if there is a short to earth then resistance is effectively tending to zero - as voltage is the same from the wall supply then the current tends to infinity - blowing fuses, tripping ELCB and ultimately melting components.

Analogue controllers don't measure resistance, resistance is the event and the change in current is the product which is used to drive an op-amp or ADC in the necessary direction. This is what causes the need for damping and can cause runaway.

A theory is the most probable conclusion given the weight of evidence and electronics engineers are the most sinfully anal people on the planet. ;-)

---

### Post by cackles on 2009-05-10
Well I was drunk when I wrote that, probably why I froze the drive even though the TORX were due to arrive the next day so I could swap out the PCB. Anologue controllers, I thought, measured the voltage and when you move your increasing the resistance, dropping the voltage. So even though your pulling a trigger in to make say a car accelerate your dropping the voltage running to the chip and it gets translated as how much you want between 0% and 100%.

Either way the drive looks screwed.

I actually had to wait for the drive to thaw out a bit because it was so cold it wouldnt move, my fingers even got stuck to it when I took it out the freezer after about 3hrs. It was a fail.

I swapped the PCBs and the PCB still worked the new drive.

For the finale I cleaned and hoovered all surfaces, closed the door to my computer room, slapped on a pair of medical gloves and put the extractor on full blast and opened it up.

The top platter has 2 massive rings on it and the heads just jump between them. The heads go into the ramp and move ok on their own, all except reading the actual disk.

Conclusion: Platters are boned so theres nothing I can do except rebuild the collection of things I need and now I have a spare set of heads for my new HDD.

I think in the end all that I've really lost is a couple of months of pics. I can rewrite my CV, redo my projects and at least now I dont have 3500 or so links. Its probably actually a good thing because now I dont have tons of absolutely useless crap lying about that "I'll sort out next week". Been saying that for about 2 years now. Apart from a few things theres nothing I cant research or find again. Also I have about 590GB left to fill now.

---

