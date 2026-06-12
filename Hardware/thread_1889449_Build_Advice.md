---
title: "Build Advice"
date: 2011-12-01
forum: Hardware
---

### Post by debili on 2011-12-01
I'm looking for advise on the system I'm planning to build:

case              Silverstone LC17
PU BeQuiet!   P5-550W
motherboard  Sabertooth x58 1366socket
hdd               WD 1TB WD1002FAEX 64mb 7200
ssd               OZC Vertex2 60gb
proc.             i7 950 socket1366 quad
videocard      --still open
dvd               --still open
fans              --still open

I've never build a pc myself, but from my first experience - I bought a desk cube with linux preinstalled 2 years ago in the faith that things will work well and i only head troubles with it, so now i'm googling and asking you guys for advise instead.. I've chosen second hands components as I don't have the money for the new stuff.

What are your thoughts on this ?
Could you suggest a good Nvidia quadro card ? 
What about the compatinility of these components with Ubuntu?

My intention with this system would be to use it for video editing as Lightworks (non linear video editor) should be available soon, and recording audio with Ardour, as ver.3 beta has just been released.. so I'm looking into, well high speed performance, while using  sort of a htpc case to keep the operating noise/fans as quiet as possible so it can be used for media playback...

many thanks

---

### Post by Jagoly on 2011-12-02
Don't go for a 1366 CPU; hot, twice superseded, expensive, slow nowadays.

Go for an i7-2600 CPU on an 1155 Z68 motherboard, such as the MSI Z68A-GD80. This will be way faster, cooler, efficient and even cheaper.

As for the Quadro GPU, I'm not sure if it's worth it. For video editing, a huge chuck of RAM (which seems to be missing from your list entirely) of about 4x4gb is a better investment, paired with a 2560mb gtx 570 GPU. A 2gb 560ti would also be great, plus much quieter.

For the power supply, your original design with a quadro gpu would have needed at least an 850w power supply. For this machine, a high effeciancy 750w PSU would be required. Corsair's hx-750 is around that mark.

The hard drives are whatever you require; but a SATA 3 SSD makes more sense.

A blu-ray burner may be useful for you, but any disk drive will work fine.

Plus I wouldn't be too hopeful for lightworks... It's been delayed YET AGAIN :-(

---

### Post by debili on 2011-12-03
Thanks Jagoly!
the i7-2600 sounds great; for this processor i would have an Asus P8 Z68 deluxe motherboard available, would that be a good combo too?
In regards to RAM, do I need to look for a specific brand/speed? I thought I'd use my 'old' 3x2gb 1333 sticks :/
Since the GPU is something I can easily replace later, do you think a cheaper, GTX 560 directcu card would do good with this system?
Same as on performance, i try to focus on how quiet/cool the whole machin will run.

btw. how is it with the power supply and hungry components alltogether - do the still run on their maximum? say I leave the computer switched on overnight with not much load, would it then get cooler, fans quieter, consumption of power lower?

---

### Post by Basher101 on 2011-12-03
> Go for an i7-2600 CPU on an 1155 Z68 motherboard, such as the MSI Z68A-GD80. This will be way faster, cooler, efficient and even cheaper. I got myself the smaller brother, the MSI Z68A-GD65 (G3) and with it the i5 2500k (i dont see THAT much of a performance difference between this one and the i7 2600k that would explain the 100$ price difference...). For graphics i got myself the Gigabyte GTX 570 (overclock) with a 3 fan cooler. Looks alot better than the stock one and will give way better cooling performance. Your RAM looks ok, but 3x2 GB is not Dual-channel memory that all the newer boards use (or is yours tripple channel?). 
Power consumption should get very low on idle. Thats the really great thing about the motherboards with the Z68 Chipset, because those allow you to use the onboard GPU of the i7 2600k AND your discrete card at the same time (like a GTX 570). Thus if you plug your monitor into your CPU HDMI port, it will switch off the discrete card when you only are on the Desktop and not running games. You can also do the other way around and plug it into your discrete card, that way your onboard GPU will be used for additional Video encoding.

p.s. For a power supply i got myself the Be quiet! E9 Straight Power 700W because i plan to use SLI with 2 GTX 570 cards in the future. Yours should be enough for a single card

---

### Post by debili on 2011-12-11
hi again, I've got the asus p8z68 deluxe logic board now, the silverstone LC17b case, and Corsair 2x8 dd3 1600 vengeance ram(will go for some 4x4 pc3-15000 ram later on); also a dvd lightsribe rewriter as i don't need blu-ray. I'm still looking for a 2500 or 2600 processor, but if already investing money into this workstation I think I'll go for the 2600 - looks like it can handle video editing a bit better then the 2500. as for the PSU, I'm going to buy your suggested corsair hx750 - or are there even more quiet psu's out there? 

I now have a question about the CPU heatsink, for my case I have some 14.5cm headroom for a heatsink to fit - could somebody recomend a big heatsink with less then 14.5cm in height? I would like to use a 12cm PWM(probably the Scythe 120mm pwm) on it but would like it to be as big as possible so the fan doesn't need to spin at high rpm..

and how is it with temp/fan conrol in ubuntu? - or is this being taken care of by the motherboard itself? 

thanks!

---

### Post by Jagoly on 2011-12-12
I am very sorry. I just wrote out about 800 words with advice, parts, and links to reviews of them, for memory, CPUs, compatibility and overclocking, however my stupid iPod Touch just crashed and it was lost. I will re-write it in a few hours when I am on my laptop.

---

### Post by debili on 2011-12-13
> **Jagoly said:**
> I am very sorry. I just wrote out about 800 words with advice, parts, and links to reviews of them, for memory, CPUs, compatibility and overclocking, however my stupid iPod Touch just crashed and it was lost. I will re-write it in a few hours when I am on my laptop.

things like that just happen :) thanks anyway..

this**sheenwatson****[B] looks like some sort of spam, or not?**[/B]

---

### Post by debili on 2011-12-18
I would also like to ask, I have a nice IDE dvd-rewriter which can't be connected to the p8z68 board - in case I get a cheap pci-ide controller, would it sufer from any issues under ubuntu ? the only negative I see would be an extra wide cable inside of the case blocking air..but besides that? thanks

---

### Post by MoreOrLess on 2011-12-18
Don't bother with fancy RAM. It doesn't make the difference it used to. You should only spend extra coin on RAM if you're overclocking.

---

### Post by Jagoly on 2011-12-18
> **debili said:**
> I would also like to ask, I have a nice IDE dvd-rewriter which can't be connected to the p8z68 board - in case I get a cheap pci-ide controller, would it sufer from any issues under ubuntu ? the only negative I see would be an extra wide cable inside of the case blocking air..but besides that? thanks

Well, DVD drives can be obtained for about $20 AUD so it would make more sense to just get a sata drive. An IDE ribbon will indeed restrict airflow quite badly. Sorry, for not getting back with my other info, I've been very busy.

Heatsinks will be a big problem for you. You can get plenty of great coolers which will clear your talk vengeance ram, HOWEVER this coolers will not fit in your case, as they are usually about 16cm tall. I don't have any recommendations for you, sorry. I intend to, for my rig, get an nzxt Havik 140 with my tall vengeance, however, my case is a Corsair carbide 500r which has over 17cm of Heatsink clearance. If you don't intend to overclock, however, a small cooler should suffice, so I'll keep looking out for one for you.

---

### Post by debili on 2011-12-21
> **Jagoly said:**
> Well, DVD drives can be obtained for about $20  AUD so it would make more sense to just get a sata drive. An IDE ribbon  will indeed restrict airflow quite badly. Sorry, for not getting back  with my other info, I've been very busy.

Heatsinks will be a big problem for you. You can get plenty of great  coolers which will clear your talk vengeance ram, HOWEVER this coolers  will not fit in your case, as they are usually about 16cm tall. I don't  have any recommendations for you, sorry. I intend to, for my rig, get an  nzxt Havik 140 with my tall vengeance, however, my case is a Corsair  carbide 500r which has over 17cm of Heatsink clearance. If you don't  intend to overclock, however, a small cooler should suffice, so I'll  keep looking out for one for you.

Thanks, so I've ordered a new DVD drives and will try to sell my old one then;) 

As for the heatsink, I've posted on silentpcreview.com and was advised to get the [Noctua NH-U9B SE2 92mm SSO CPU Cooler]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835608016")  which looks pretty good so I'm going to try it out. And as you say, I  don't intend to overclock, so a smaller cooler should be fine i think. 
Also,  my first intention was to get the corsair hx750 PSU but there was a  good price for the corsair hx620 PSU - it's got perfect reviews, silence  and performencewise, and if I do a calculation even with a GTX560ti  (which seems to consume 170W) it seems to be sufficient...I hope i'm not  wrong, I might update to the hx750 or 850 soon though..

For the SSD i've chosen the Vertex3 60gb.

Well  looks like I've got everything ready, just not the GPU, I will put in  my old GT520 silent for now on, until I find one which one to get - is  there such a big difference between the GTX 560Ti and the GTX 550Ti ?  cause in the price there is!... 

my setup so far is:

case              Silverstone LC17b
multi-frontpanel Silverstone SST-FP35B 
PSU Corsair HX620
motherboard  Asus p8Z68 deluxe
hdd               WD 1TB WD1002FAEX 64mb 7200 sata3
ssd               OZC Vertex3 60gb sata3
proc.             i7 2600k quad 1155
heatsink+fan Noctura NH-U9B SE2
ram Vengeance 1600 2x4gb
dvd               LG GH22LS  DVD rewriter, lightscribe, sata
case fans 92mm Renco 18dB, 2x80mm Noctua NF-R8 PWM 7-17dB

videocard - o p e n
videocard heatsink+fan - o p e n

All input is welcome! thanks

---

### Post by Jagoly on 2011-12-21
That's looking like a pretty awesome build :-)

I've never used that cooler, but it looks pretty good. It should work fine as long as it does not overhang the ram. The noctua stuff does carry a price premium, but from my experience, it's worth it.

As for the GPUs, I can't compare those two directly myself, but In my younger sibling's Desktop I have a GT 520 at the moment, but I've gotten him a GTX 550ti for christmas, so I can compare those two. Don't have a 560ti. From reviews it seems to be about 50-60% faster than a 550ti.

I've never owned or even used an SSD, but intend to get one soon. I know that the older vertex 2's from OCZ had a lot of problems, but I think that the vertex 3's are a lot better.

And there probably wouldn't be any problems with the ASUS board, but it might be better to go with MSI, who officially support linux, or ASrock, who tend to be a bit better than ASUS. Steer clear of Gigabyte, they are the worst.

---

### Post by debili on 2011-12-25
> **Jagoly said:**
> That's looking like a pretty awesome build :-)

I've never used that cooler, but it looks pretty good. It should work fine as long as it does not overhang the ram. The noctua stuff does carry a price premium, but from my experience, it's worth it.

As for the GPUs, I can't compare those two directly myself, but In my younger sibling's Desktop I have a GT 520 at the moment, but I've gotten him a GTX 550ti for christmas, so I can compare those two. Don't have a 560ti. From reviews it seems to be about 50-60% faster than a 550ti.

I've never owned or even used an SSD, but intend to get one soon. I know that the older vertex 2's from OCZ had a lot of problems, but I think that the vertex 3's are a lot better.

And there probably wouldn't be any problems with the ASUS board, but it might be better to go with MSI, who officially support linux, or ASrock, who tend to be a bit better than ASUS. Steer clear of Gigabyte, they are the worst.
Oh, i didn't know MSI has official support for linux :/ but the asus one seems to work fine, so far. I had to leave the build for a couple of days as i went visiting my old folks for xmass so i'll get back here begin january. First start and ubuntu install went fine and f a s t. 
Many thanks so far!

---

