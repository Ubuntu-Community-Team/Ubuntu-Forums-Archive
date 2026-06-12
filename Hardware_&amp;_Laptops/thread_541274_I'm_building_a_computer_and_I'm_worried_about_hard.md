---
title: "I'm building a computer and I'm worried about hardware incompatibillity with Ubuntu."
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by Explosivo on 2007-09-02
My sister asked me to build her a desktop computer, and after seeing me use Ubuntu she requested that it has only Ubuntu installed. I selected all of the parts on Newegg.com, and that leaves me with a good but affordable parts list. The only problem is that I'm worried that some of the hardware may not be compatible with Ubuntu, or I that I won't be able to find drivers that properly utilize the hardware. I know there are plenty of threads about building an Ubuntu compatible PC, but I want information on my specific parts list with out having to search around, as well as your opinions on the specs. Here is the list.

The  GIGABYTE GA-MA69GM-S2H micro-ATX motherboard.
An  AMD Athlon 64 X2 4200+ processor clocked at 2.2 Ghz (although I may overclock it in the future).
A  COOLER MASTER Centurion 5 case (of course, there's not going to be an compatibility issues with that, I'm just trying to give you an idea of the computer I'm building).
A  Western Digital Caviar SE16 250GB 7200 RPM SATA hard drive.
An EVGA Nvidia 7600GT video card (256MB 128-bit PCI-E).
Thermaltake 400w power supply.
A 1GB stick of DDR2 SDRAM DDR2 800 (G.Skill is the brand).
A Sony NEC Optiarc 18X DVD±R DVD Burner.
A (this is the one I'm most worried about) Creative Sound Blaster Audigy SE 7.1 sound card.
And finally a Western Digital Elements 250GB 7200 RPM external USB hard drive.

Ubuntu is known to be the operating system that "just works", but there are some issues with drivers. Do any of you think I'll have any problems, and also, what do you think of the specs, good or bad?

---

### Post by goatflyer on 2007-09-02
You may be interested in reading this site:

[http://opensource.creative.com/](http://opensource.creative.com/)


Here, Creative talks about which of their cards work using which open-source technology (mostly ALSA).

On the ALSA page I see that the A/D inputs on the card don't work, but if you only plan to use it for playing sound, you should be alright.  Then again, you might want to look through that table and see which cards work better.

Ubuntu does 'just work', but  hardware manufacturers have to give linux the same support as they do for windows or else linux will always have to play 'catch up'  (Windows also does not work with cards where no windows driver exists)  Fortunately more and more manufacturers are giving support to linux so perhaps the problem is gradually improving over time.

---

### Post by Explosivo on 2007-09-02
Thank you for your help. Will Ubuntu have the Alsa driver already on it upon installation? What do you mean by A/D?

---

### Post by Explosivo on 2007-09-02
Never mind, I saw the ALSA sound card page. I'm just going to be using it for outgoing audio, so I should be OK right?

---

### Post by daveshields on 2007-09-02
I think you'll be ok. Though the customer comments for the Gigabyte motherboard you selected make no mention of Ubuntu, I read through the comments on all the other Gigabyte motherboards and several gave postive reports on use with 7.04

I also read through the video card reviews and found several positive reports on use with 7.04

For some further thoughts on buying hardware from newegg (my favorite supplier), see 
[http://daveshields.wordpress.com/2007/08/27/on-buying-and-building-hardware-break-a-leg-with-newegg/](http://daveshields.wordpress.com/2007/08/27/on-buying-and-building-hardware-break-a-leg-with-newegg/)

For my other posts on Ubuntu, see [http://daveshields.wordpress.com/ubuntu-posts/](http://daveshields.wordpress.com/ubuntu-posts/)

---

### Post by Explosivo on 2007-09-02
Thank you VERY much for your help. I'm glad to know that it'll work out all right. Ubuntu forums is a great help!

---

