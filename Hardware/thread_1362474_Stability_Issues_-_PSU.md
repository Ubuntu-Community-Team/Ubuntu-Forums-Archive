---
title: "Stability Issues - PSU?"
date: 2009-12-23
forum: Hardware
---

### Post by meep_meep on 2009-12-23
Hi all,

I've been having problems in both my Vista SP2 and Ubuntu 9.10 installs.  I recently built the computer myself with parts from ebuyer.  I've been having complete system freezes in Vista, normally when using Chrome.  I would not be doing anything intensive (apart from Flash) just using Spotify + Chrome or just Chrome with iPlayer (flash).  Nothing comes up in Event Viewer!

In Ubuntu it would have complete system freezes when watching Flash iPlayer full screen using my 23" widescreen with the audio running on a small loop.  I disabled compiz to use metacity and I removed pulseaudio and replaced it with ALSA.  Again nothing comes up under Messages in the kernel log viewer.

I thought that it could be my graphics card or the drivers but the fact that it crashes in windows and linux makes me think it is a hardware problem.

I thought that maybe it was an issue with my RAM but I have Corsair RAM which I did a memtest86+ on and it came out fine! I also changed the timinings in the BIOS and my BIOS recognises the RAM properly.

So I was wondering if it was my PSU?  My system is

AMD Phenom II x4 955 black edition
4gb corsair ram ddr3 unbuffered
msi 770-c45
gigabyte 9600 gt silent cell
d-link wifi card dwl-g510
2 fans connected

The PSU is Artic Power 500w which I had never heard of but on ebuyer they have 5 stars [http://www.ebuyer.com/product/124922/show_product_reviews?offset=10&review_type=both&review_order_by=RUF](http://www.ebuyer.com/product/124922/show_product_reviews?offset=10&review_type=both&review_order_by=RUF)

What do you guys think?

---

### Post by IcarusR on 2009-12-23
You could check the voltages in the bios.

---

### Post by meep_meep on 2009-12-23
My computer crashed again as soon as i booted back into vista from another crash just now!!

Anyway my CPU temp is 56 C (this is not from cold boot).

The voltages are

CPU Vcore  1.376 V
3.3V 3.328 V
5V 5.061
12v 11.88V

What does this mean?

---

### Post by TitanusEramius on 2009-12-23
> **meep_meep said:**
> 
The voltages are

CPU Vcore  1.376 V
3.3V 3.328 V
5V 5.061
12v 11.88V

What does this mean?

The Vcore voltage can vary, but the three bottom-lines are always the same and should be within 10% of 3,3, 5 & 12 volts, so to me this looks fine.

Apparently i can't find any articles that can describe the four different voltages, but if you suspect the psu-unit is not working probably, the easiest way to test this would be to switch it out with a psu you know works.

---

### Post by meep_meep on 2009-12-23
Ok thanks.

If my CPU were to overheat would I experience complete system freezes or simply just a reboot.  I was looking at my CPU temperature and in BIOS with obv no load it was climbing to 64 degrees C !!! 

I checked my heatsink and it moves from side to side when I touch.  So there might be a contact problem which would mean my computer is over heating.

What do you think?

---

### Post by TitanusEramius on 2009-12-23
Finally i found something:

" They had a 5 volt rail because   that was the voltage needed to power most of the standard silicon chips of   the time. The 12 volt rail was used primarly to operate fans and floppy disk   drive motors."

From:
[http://www.playtool.com/pages/psurailhistory/rails.html](http://www.playtool.com/pages/psurailhistory/rails.html)

---

### Post by meep_meep on 2009-12-23
I just looked at my heatsink and took it off.  There are no burn marks but I realised that I hadnt locked in place properly so maybe the lack of contact between my heatsink and CPU caused it to overheat and freeze.

Would i need to re-apply thermal paste?

---

### Post by TitanusEramius on 2009-12-23
That actually sounds right, because when you connect the computer it probably stands upright so the heatsink looses the contact with the cpu?

I would start by checking all for corners where the plastic frame goes through the motherboard, but besides from that, i don't know, it depends on the heatsink itself.

---

### Post by TitanusEramius on 2009-12-23
Yes, always use a little thermal paste when the heatsink is put back on.

You are a bit lucky, i did this a few years back, and it burned the cpu beyond repair...

---

### Post by meep_meep on 2009-12-23
Thank you for your help!

---

### Post by meep_meep on 2009-12-23
I have re-fitted my heatsink which is great but my system is still over heating :S

I havent overclocked or anything.  In idle i've had the system drop to 33 C at best after i installed a fan inside the case but when I run Counter-Strike Source in Vista SP1 which is quite intensive in terms of computing, I have reached temperatures as high as 79 C.

I read that thermal paste takes time to settle and maybe I put too much on but thats not the point why I am writing this.  I was watching my temperature in Core Temp and it said that my VID (vcore) was fluctuating.  Normally my vCore is at 1.35v but after playing CS:S it started to fluctuate to 0.9750v, 1.15v, 1.25v and 1.35v.  

Will this affect the stability of the system?  Is this the PSU not being able to sustain the load?

---

### Post by TitanusEramius on 2009-12-23
It could sound like the motherboard and cpu not receive the power they need.

I still think it would be easiest to try with another psu (if you have one off course) but i have a few ideas:

Have you checked and double-checked all connections from the psu, fans and so on? There should at least be the big 24-pin connector (the computer won't start without it, but make sure it sits all the way in), one 4, 6 or 8 pin power-cable that goes in right next to the cpu, and then the graphics-card probably needs a power-cable of some sorts. Also, check that the fans actually goes around when you turn the system on.

The next thing i can think of is that you cold try to "save some power", to see if this stops the computer from freeze. If you have more than one harddisk then unplug the rest from the psu. The same goes for the cd-roms. In the bios, under the Overclocking-section, try to do some "underclocking" on the cpu if you can, and try to get the vcore voltage as low as possible.

The last thing is the power-output of your psu, is it rated high enough? I use a 1000 watts psu for my system because of sli, but even without sli i would get en trouble if tried to run my system with a psu below 500 watts.

Good hunting :)

---

### Post by gwagchunks on 2009-12-23
Hi

I have the same PSU as you, got it from ebuyer nearly a year ago now and have not had any issues with it. After I bought it I found on ebuyers forums a guide to PSU's. Artic did not come high up on the list! But I guess you get what you pay for and I'm happy with mine after the "jet engine" sounding one I used to have! I did have some weird lock ups with XP, but tracked it down to the gigabyte utilities I was running. I removed them and things were better. Ubuntu runs fantastically on the system though, can't fault it. I have had issues with other builds I have done with memory not being correctly seated and will still pass a memory test. The gigabyte board I have can be picky about RAM. Have you tried one stick? Good luck

---

### Post by meep_meep on 2009-12-24
> **meep_meep said:**
> I was watching my temperature in Core Temp and it said that my VID (vcore) was fluctuating.  Normally my vCore is at 1.35v but after playing CS:S it started to fluctuate to 0.9750v, 1.15v, 1.25v and 1.35v.

Ignore what I said earlier, this fluctuation was there because of AMD cool and quiet technology lowering the mulitpliers on the CPUs.  I switched off C'n'Q and left the mulitpliers at x16 and the VID/vCore remained stable.

Now that gwagchunks verified the quality of the PSU and i have refitted my cpu heatsink, I will check all the power connections in my computer.  After that I will see if my system is stable with this setup!

Thanks for your help guys and girls! :)

---

### Post by meep_meep on 2009-12-24
> **meep_meep said:**
> Ignore what I said earlier, this fluctuation was there because of AMD cool and quiet technology lowering the mulitpliers on the CPUs.  I switched off C'n'Q and left the mulitpliers at x16 and the VID/vCore remained stable.

Now that gwagchunks verified the quality of the PSU and i have refitted my cpu heatsink, I will check all the power connections in my computer.  After that I will see if my system is stable with this setup!

Thanks for your help guys and girls! :)


Ignore what I said.  I ran Prime95 (to stress test my computer) and it automatically sent all my cores to 100% of use.  I was watching the temperature and that was hitting about 65+ C and then my computer restarted!  I have ran my computer continuously at 70+ C while playing CS:S so temperature was not an issue.  I think that my PSU can't handle the load.

What do you guys think?

I'm going to try with one stick of RAM but as its Corsair im more inclined to believe its the PSU.

---

### Post by meep_meep on 2009-12-24
This so fustrating!!!!!!

I ran Prime95 again and it didnt restart immediately but my temperature rocketed to 90+ C :s this is not cool!

My system idles at 35 C but under load, it goes up to 80+ C which isn't good.  I don't know what it is any more whether its my PSU, RAM, Motherboards or Cooling.... or a combination of these

why did i bother building a computer....i should have brought one...

---

### Post by cascade9 on 2009-12-25
> **meep_meep said:**
> I just looked at my heatsink and took it off. There are no burn marks but I realised that I hadnt locked in place properly so maybe the lack of contact between my heatsink and CPU caused it to overheat and freeze.
 
 Would i need to re-apply thermal paste?
 
 Oh dear, this can be bad. It theoretically shouldnt be that bad, but running with a badly attached heatsink can cause major problems.

I really hope you havent burnt the CPU or something in your motherboard. But your last 2 posts make me think you've done something nasty (you really shouldnt hit 80C+ under load...and the system shouldnt restart at 65C)

> **TitanusEramius said:**
> It could sound like the motherboard and cpu not receive the power they need.

I still think it would be easiest to try with another psu (if you have one off course) but i have a few ideas:

Have you checked and double-checked all connections from the psu, fans and so on? There should at least be the big 24-pin connector (the computer won't start without it, but make sure it sits all the way in), one 4, 6 or 8 pin power-cable that goes in right next to the cpu, and then the graphics-card probably needs a power-cable of some sorts. Also, check that the fans actually goes around when you turn the system on.

The next thing i can think of is that you cold try to "save some power", to see if this stops the computer from freeze. If you have more than one harddisk then unplug the rest from the psu. The same goes for the cd-roms. In the bios, under the Overclocking-section, try to do some "underclocking" on the cpu if you can, and try to get the vcore voltage as low as possible.

The last thing is the power-output of your psu, is it rated high enough? I use a 1000 watts psu for my system because of sli, but even without sli i would get en trouble if tried to run my system with a psu below 500 watts.

Good hunting :)

Good advice. 

Its a 'black edition' so its unlocked, it should be totally underclockable. 

500 watts is fine for that system. People tend to massively over-estimate how many watts they need. See here- 

[http://www.xbitlabs.com/articles/coolers/display/system-wattage.html](http://www.xbitlabs.com/articles/coolers/display/system-wattage.html)

In that test, they ran a intel i7 920, 3GB DDR3, 1TB 7200 HDD, DVD-RW, 1792MB GTX 295 (which is pretty much SLI on a card) Total max power use- 502 watts.

---

### Post by TitanusEramius on 2009-12-28
Now that we all survived yet another christmas, would it be possible to get an update?

Setting up new hardware can be very tricky in the beginning, but in my opinion the reward by doing yourself (and get it to work) is worth the trouble :P

---

### Post by meep_meep on 2009-12-29
> **cascade9 said:**
> Oh dear, this can be bad. It theoretically shouldnt be that bad, but running with a badly attached heatsink can cause major problems.

I really hope you havent burnt the CPU or something in your motherboard. But your last 2 posts make me think you've done something nasty (you really shouldnt hit 80C+ under load...and the system shouldnt restart at 65C)



Good advice. 

Its a 'black edition' so its unlocked, it should be totally underclockable. 

500 watts is fine for that system. People tend to massively over-estimate how many watts they need. See here- 

[http://www.xbitlabs.com/articles/coolers/display/system-wattage.html](http://www.xbitlabs.com/articles/coolers/display/system-wattage.html)

In that test, they ran a intel i7 920, 3GB DDR3, 1TB 7200 HDD, DVD-RW, 1792MB GTX 295 (which is pretty much SLI on a card) Total max power use- 502 watts.

so this is the update.....

I have underclocked my PC to the lowest setting using a mulitplier of x4 (i think) which gives four cores at 800Mhz.  I'm still using cool and quiet enabled but the vCore (VID) voltage is not going down.  It is staying at 1.35v which means the computer idles quite hot at 50C but the voltage seems steady and stable.  I even tried to change the hyper threading speeds to see if it affects the idle temp but this resulted in the computer not booting at all and i had to manually reset the BIOS. :S

I've tried various mulitpliers and tested them with Prime95.  Using 800Mhz x4 cores, the temperature goes to about 63 and in the increase in temperature is very very slow.  Any higher mulitpliers on my core would make my worried about my computer under load.  Since then I have suffered no crashes from using full screen flash or playing civ 4 in windows or counter strike!  This gives me a stable and quick (ish) computer.

I've posted on the AMD forum but I am yet to hear back.  So now I think that definitely I have damaged my CPU :( because without my fan being fitted properly the temperatures must have been extremely high.  I'm guessing that I would not be able to return the CPU because it was my fault that I have damaged it....what do you think? 

I am now hoping that my motherboard or any other parts arent too damaged :S  I'm going to order a phenom II x2 black edition in which i might be able to unlock a core or two :D for £70 as I dont want to spend another £ 133 on a CPU :(

what do you guys think I should do?

---

### Post by meep_meep on 2010-01-04
MY COMPUTER SUCKS!!

i got my new CPU, AMD Phenom II x2 BE and it runs cool and under load (using Prime95) it goes slowly up to over 68 degrees C.  It then restarted so it must be my PSU or motherboard or RAM i mean which could I choose!!!!??!?!?!  My old CPU when underclocked down to 800Mhz for each core using a x4.0 mulitplier was completely stable running at vCore (VID) 1.35 all the time.  So what could it be?  Voltage seems stable when underclocked, so i dont know what it is... maybe my RAM is faulty but its Corsair!!  (it is quite close to my heatsink so maybe it got too hot when my CPU overheated from before.

i want to return all my computer parts and go and buy myself an apple...

F*** this, thats £500+ of computer thats junk, I can't trust it to do anything....

---

### Post by cascade9 on 2010-01-05
I doubt your RAM is the issue. 

I think that you have done something nasty to your motherboard. Its possible that your old X4 CPU is fine, but without something to test it on there is no way to be sure....

Umm, without trying to sound 'I told you so' (cause I didnt) this is why you really need to be careful when yuo build computers. Just one minor thing like forgetting to make sure the heatsink is attached properly can ruin the whole experience. :|

---

