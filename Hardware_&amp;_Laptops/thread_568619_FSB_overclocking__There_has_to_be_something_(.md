---
title: "FSB overclocking ?? There has to be something :("
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by pishiman on 2007-10-06
My board doesn't offer OC tweaks but I've managed to crank up the FSB in Windows thanks to nTune. I was truly shocked to learn that nobody, and I mean nobody even bothered creating a utility for CPU overclocking under Linux. I'm desperate to overclock my ubuntu system because it's so slow right now. Is there any hope? nTune for linux? 

I also tried a whole bunch of OC programs via WineHQ, but they all freeze :(
Can someone create an OC utility for linux, or translate ntune?

---

### Post by kerry_s on 2007-10-06
most people just use a faster desktop. no need to risk frying your system.

---

### Post by pishiman on 2007-10-06
> **kerry_s said:**
> most people just use a faster desktop. no need to risk frying your system.

Ok so i've been Ocing for over 3 years now and i'v never heard a pop. Motherboards and CPU's integrate thermal sensors that shutdown the system if temperature reaches critical figures. I'm still looking for a linux OC utility. How hard can it be to create something like ntune for linux?

---

### Post by dinub1 on 2007-10-06
> **pishiman said:**
> My board doesn't offer OC tweaks but I've managed to crank up the FSB in Windows thanks to nTune. I was truly shocked to learn that nobody, and I mean nobody even bothered creating a utility for CPU overclocking under Linux. I'm desperate to overclock my ubuntu system because it's so slow right now. Is there any hope? nTune for linux? 

I also tried a whole bunch of OC programs via WineHQ, but they all freeze :(
Can someone create an OC utility for linux, or translate ntune?

Come on :) You create one. Show us how smart can you be :)

---

### Post by pishiman on 2007-10-06
> **dinub1 said:**
> Come on :) You create one. Show us how smart can you be :)

If only I knew how to write a program :( Wasn't there supposed to be an nTune for linux?

---

### Post by pmj0383 on 2007-10-06
If you were serious about overclocking you'd have bought a decent motherboard that supports overclocking. Overclocking utilities via software are garbage and are not the same.
And every computer I've owned for the past 4+ years has been overclocked at least 1 ghz, it's very stable if you do a little research into the parts you are buying and have adequate cooling.

---

### Post by dinub1 on 2007-10-06
> **pishiman said:**
> If only I knew how to write a program :( Wasn't there supposed to be an nTune for linux?

I dont know... Linux drivers are by nature simplified. I havent heard of one. why not learn how to program one and write an application for it?

After years of experience with PC's I beleive that OC'ing may be a dangerous technique that shoud be avoided. In any case won't reder your PC system run visibly faster, then why risk counting on thermal devices when sometimes they can fail too and render your system useless?

BTW I have a nVidia graphic card on my main Windows XP PC I am aware of nYune progeam but I never tried to use it.

---

### Post by pmj0383 on 2007-10-06
> **dinub1 said:**
> 
After years of experience with PC's I beleive that OC'ing may be a dangerous technique that shoud be avoided. In any case won't reder your PC system run visibly faster, then why risk counting on thermal devices when sometimes they can fail too and render your system useless?


Overclocking developed because people realized that alot of times, cpu manufacturers just repackage the same chip at different speeds. 
You have to understand how they make the chips. The engineers basically design the chip and say, "this should be able to go 3 Ghz at 1.5v". So they crank out a bunch and then test them for stability. Some chips may not work perfectly at 3 Ghz but work just fine at 2.6 GHz. And then sometimes, they ALL work at 3 GHz but people still want to buy the 2.6 GHz model because it's fast enough for them. So Intel or AMD just underclocks them to 2.6 Ghz and slaps a sticker on em. 
It's cheaper for them to just make one chip than make 10 different models that are actually different. People caught on that the $100 chip was the same as the $400 chip except the $100 chip had a lower multiplier or FSB setting. It's not like this in all cases, but if you research what you buy, and look at what other's are doing with certain models, you can find out which chips the manufacturer is doing it with. 

That's when you buy the cheaper one, get a motherboard that supports manual speed settings, and start changing settings so the chip can actually do what it was made for. It's ill-informed to think that overclocking is simply increasing voltages and trying to make something go where it shouldn't. In most cases, it's making it go where it can.

Now of course there are people that like to see how far things can really go, and use advanced cooling like water cooling and liquid nitrogen, but in most cases nowadays, it's very easy and resonable to get more for your money by overclocking, without messing with voltages at all or increased temperatures.

---

### Post by dinub1 on 2007-10-06
*[COLOR="Navy"]Now of course there are people that like to see how far things can really go, and use advanced cooling like water cooling and liquid nitrogen, but in most cases nowadays, it's very easy and reasonable to get more for your money by overclocking, without messing with voltages at all or increased temperatures.[/COLOR]*

Ha... :) I liked your post from an engineering reasonably point of you. You need to know that I am a degreed one but not an electrical engineer though I have some backgrounded in electrical circuits and electronics.

All sounded reasonable until your last sentences. You claim that over clocking is possible without increasing voltages or increase int temperatures. That is perhaps 1/2 true. I know to do over clocking by increasing the CPU basic operating frequency, soem call it increasing the FSB speed. That is indeed one of the techinique mostly used to overclock a system, without increasing the voltage. But that by itself, causes the CPU temp to increase, given the same cooling capacity. So therefore your sentence was not totally accurate. 
Also I hope you know that this process is a trial and error thing and it is highly dependent on the motherboard and the hardware abilities to undergo over clocking. I always knew what I wanted and what I can buy for my money.Say if now I have an AMD X2 6000 AM@ CPU which runs at 3 GHZ, would it be beneficial for me to try increasing its frequency say to 3.2 GHz? For what :) ? Would I see a visible improvement in CPU performance? Why? I have 4 GB of PC6400 of RAM running in dual channel memory configuration. Just how fast do I need these memry chips to run :) ? Also a nVIDIA GeForce 8800 GS graphic card which occupies 2 slots and needs a separate 12 V on board power source. Just how fast do I need these memory chips to run :) ? Why? Would I benefit anything if I increase its internal clock, say from 500 MHz to 600 MHz? I am nor runiing games. Perhaps perhaps the most powerful applications I am running on this machine are Adobe Photoshop CS 2 and CATIA 5.

Ultimately over clocking is for people who are bored and have nothing better to do in life than that... :) I did my over clocking experiments and I after a while arrived to the conclusion that it is not beneficial.
__________________

---

### Post by tgalati4 on 2007-10-07
>sudo apt-get install powertweak
>sudo gpowertweak

---

### Post by pmj0383 on 2007-10-07
> **dinub1 said:**
> *[COLOR="Navy"]Now of course there are people that like to see how far things can really go, and use advanced cooling like water cooling and liquid nitrogen, but in most cases nowadays, it's very easy and reasonable to get more for your money by overclocking, without messing with voltages at all or increased temperatures.[/COLOR]*

Ha... :) I liked your post from an engineering reasonably point of you. You need to know that I am a degreed one but not an electrical engineer though I have some backgrounded in electrical circuits and electronics.

All sounded reasonable until your last sentences. You claim that over clocking is possible without increasing voltages or increase int temperatures. That is perhaps 1/2 true. I know to do over clocking by increasing the CPU basic operating frequency, soem call it increasing the FSB speed. That is indeed one of the techinique mostly used to overclock a system, without increasing the voltage. But that by itself, causes the CPU temp to increase, given the same cooling capacity. So therefore your sentence was not totally accurate. 
Also I hope you know that this process is a trial and error thing and it is highly dependent on the motherboard and the hardware abilities to undergo over clocking. I always knew what I wanted and what I can buy for my money.Say if now I have an AMD X2 6000 AM@ CPU which runs at 3 GHZ, would it be beneficial for me to try increasing its frequency say to 3.2 GHz? For what :) ? Would I see a visible improvement in CPU performance? Why? I have 4 GB of PC6400 of RAM running in dual channel memory configuration. Just how fast do I need these memry chips to run :) ? Also a nVIDIA GeForce 8800 GS graphic card which occupies 2 slots and needs a separate 12 V on board power source. Just how fast do I need these memory chips to run :) ? Why? Would I benefit anything if I increase its internal clock, say from 500 MHz to 600 MHz? I am nor runiing games. Perhaps perhaps the most powerful applications I am running on this machine are Adobe Photoshop CS 2 and CATIA 5.

Ultimately over clocking is for people who are bored and have nothing better to do in life than that... :) I did my over clocking experiments and I after a while arrived to the conclusion that it is not beneficial.
__________________

If you change the speed without increasing the voltages, you will rarely see a noticable difference in temps. Even increasing voltages to achieve higher clock speeds is safe in small increments is usually safe.  In your case, an AMD 6000+, that specific processor isn't a good overclocker, due to it being near the end of the spectrum of that series capabilities. Yes, I'd still overclock it another 200 MHz, just because, you'd still be well within it's normal capacity and you'd be getting more for your money, but there are better options if you actually want to overclock with the purpose of getting your money worth. 
Your argument is counter-intuitive. If you don't want an increase in speed, why did you buy those parts? A difference for 200 MHz in an AMD chip usually means a different model. Why not just underclock it 200 MHz and lower the voltage to make it even more stable! And consume less power/generate less heat! Overclocking is the same reason you bought those expensive parts, to have a fast machine. 

There's nothing about overclocking that would lead someone to assume overclockers are bored or have nothing better to do. I researched before I bought, which you should do anyway, bought a Core 2 Duo 6300 @ 1.86 GHz, over a year ago, immediately overclocked it to 3 GHz, and haven't seen a single problem yet and literally never spent another second after the intial half hour of incrementally raising the clock speed and testing it. That is still the fastest clock speed sold for a Core 2 Duo, although now there are other differences like more cache and even quad core. Mine is running a 1700 MHz FSB, while the new ones are what, 1333 MHz now? I'd say I got my money worth.

---

### Post by pishiman on 2007-10-07
> **pmj0383 said:**
> If you change the speed without increasing the voltages, you will rarely see a noticable difference in temps. Even increasing voltages to achieve higher clock speeds is safe in small increments is usually safe.  In your case, an AMD 6000+, that specific processor isn't a good overclocker, due to it being near the end of the spectrum of that series capabilities. Yes, I'd still overclock it another 200 MHz, just because, you'd still be well within it's normal capacity and you'd be getting more for your money, but there are better options if you actually want to overclock with the purpose of getting your money worth. 
Your argument is counter-intuitive. If you don't want an increase in speed, why did you buy those parts? A difference for 200 MHz in an AMD chip usually means a different model. Why not just underclock it 200 MHz and lower the voltage to make it even more stable! And consume less power/generate less heat! Overclocking is the same reason you bought those expensive parts, to have a fast machine. 

There's nothing about overclocking that would lead someone to assume overclockers are bored or have nothing better to do. I researched before I bought, which you should do anyway, bought a Core 2 Duo 6300 @ 1.86 GHz, over a year ago, immediately overclocked it to 3 GHz, and haven't seen a single problem yet and literally never spent another second after the intial half hour of incrementally raising the clock speed and testing it. That is still the fastest clock speed sold for a Core 2 Duo, although now there are other differences like more cache and even quad core. Mine is running a 1700 MHz FSB, while the new ones are what, 1333 MHz now? I'd say I got my money worth.

I know I agree. People just don't realize that they buy a $ 500 FAST CPU which is essentially just a a repackaged $ 200 chip. I don't see anything wrong with OC but it's plainly stupid to buy a $ 200 board just to get an extra 200 MHz. I'd rather spend extra on the CPU because companies like ASUS and DFI (known for excellent OC boards) simply charge too much. I'm currently running a sub $ 50 board with a sub $ 50 CPU :) and I can easily push my system(ntune)  to gain at least 15% performance boost. So do some math,

      15% performance boost = pay extra $ 100 for CPU/mobo upgrade
      15% performance boost via OC = your gf is happy

:)

---

### Post by dinub1 on 2007-10-07
[I][COLOR="Navy"]If you change the speed without increasing the voltages, you will rarely see a noticable difference in temps. 
[/COLOR][/I]

I do not know the case with Intel Core 2 Duo but with a Prescott (P4- 3 GHz single core) that I still have, temp rose after I increased the FSB. From both a logical and technical point of view, increasing the CPU frequency, increases its power consumption and hence the heat production/dissipation. Therefore it would produce more heat and if that is not dissipated accordingly, that by itself will show as a raise in CPU temp. Sorry. The Core Duo may have better heat disspation than the P4 Prescott, but the physics are the same. So the above is not convincing me.

*[COLOR="Navy"]Even increasing voltages to achieve higher clock speeds is safe in small increments is usually safe. [/COLOR]*

I did not disagree with that. But raising it over a certain limit and abbruptly, it is not safe. in my view, one increses the CPU voltage, to make it (and the chipset) more stable at higher frequencies. Because systems tend to be unstable at higher frequencies without corect voltage compensations.

*[COLOR="Navy"]In your case, an AMD 6000+, that specific processor isn't a good overclocker, due to it being near the end of the spectrum of that series capabilities.[/COLOR]*

I have no interest overclocking it. I run it at its rated speed. 

[I][COLOR="Navy"] Yes, I'd still overclock it another 200 MHz, just because, you'd still be well within it's normal capacity and you'd be getting more for your money, but there are better options if you actually want to overclock with the purpose of getting your money worth.
[/COLOR][/I]
Explain the above. What is "getting your moeny worth"? 3 GHz (rated) speed is not my money worth? Would say 3.2 GHz operation benefit me of any visible advantage? Pls explain. 

[I][COLOR="Navy"]Your argument is counter-intuitive. If you don't want an increase in speed, why did you buy those parts? A difference for 200 MHz in an AMD chip usually means a different model. Why not just underclock it 200 MHz and lower the voltage to make it even more stable!
[/COLOR][/I]
Who are you trying to convince? If it runs perfectly at rates speed which is already high, why would I need to underclock it to make it more stable? :) You make no sense. I bought those components because I could afford them. OK ? Whoever desires to play with overclocking, "get their money worth" etc, they should feel free to do it. On their own responsabilty. 

[I][COLOR="Navy"] And consume less power/generate less heat! Overclocking is the same reason you bought those expensive parts, to have a fast machine. 
[/COLOR][/I]

Nope. Overclocking is not the reason why I bought these expensive components. I prefer to invest in more expensive parts (if I can aford them), run them safely at their rated speed and enjoy the capabilities of my system. Is this a failed approach :) ?

*[COLOR="Navy"]There's nothing about overclocking that would lead someone to assume overclockers are bored or have nothing better to do. I researched before I bought, which you should do anyway, bought a Core 2 Duo 6300 @ 1.86 GHz, over a year ago, immediately overclocked it to 3 GHz, and haven't seen a single problem yet and literally never spent another second after the intial half hour of incrementally raising the clock speed and testing it. That is still the fastest clock speed sold for a Core 2 Duo, although now there are other differences like more cache and even quad core. Mine is running a 1700 MHz FSB, while the new ones are what, 1333 MHz now? I'd say I got my money worth.[/COLOR]*

OK. From 1.86 GHz to 3.00 GHz is that an increase of raughly 40%? If your system runs stable, then you should be happy. I was never able to overclock and to run my system stable say to more than 25% over the rated speed. Maybe that the hardare did not supprot higher overclocking rates. In the end I resumed rated speed of components and I do not regret it.
Let's recapitulate. My claim was that overclocking is a dangerous procedure, it shoud be performed carefully, one needs to know what he does, otherwise the disadvantages in performing it, are bigger than the advantages. This was all I said.

---

### Post by pishiman on 2007-10-07
> **tgalati4 said:**
> >sudo apt-get install powertweak
>sudo gpowertweak

I'm greeted with this error when I try to sudo gpowertweak

Error creating socket to : /var/run/powertweakd Connection refused
Segmentation fault (core dumped)

what now?

---

### Post by dinub1 on 2007-10-08
[COLOR="Navy"][I]15% performance boost = pay extra $ 100 for CPU/mobo upgrade
15% performance boost via OC = your gf is happy
[/I][/COLOR]
:) Well, question is, 15% performance boost or 15% overclocking, are your applications running 15 % faster ? No, no no :) How much performance boost one gets from upgrading say a 2 GHz CPU to a 3 GHz one? (50% "power boost")? Do application run 50% faster? No way. Except for heavy applications like Photoshop, video editing or perhaps 3D CAD modelling that may benefit from the extra power, other "standard" applications will run more likely at the same speed. You can improve PC performance by adding more RAM. So overclocking, other than achieving perhaps personal satisfaction for making your system run faster, to its limit... there is not much advantage, in my views.


__________________

---

### Post by Yellow Onion on 2007-10-09
> **pishiman said:**
> My board doesn't offer OC tweaks but I've managed to crank up the FSB in Windows thanks to nTune. I was truly shocked to learn that nobody, and I mean nobody even bothered creating a utility for CPU overclocking under Linux. I'm desperate to overclock my ubuntu system because it's so slow right now. Is there any hope? nTune for linux? 

I also tried a whole bunch of OC programs via WineHQ, but they all freeze :(
Can someone create an OC utility for linux, or translate ntune?

Are You Running an AMD?
Just cause AMD (939 and perhaps above) doesnt have a FSB since the memory controller is in the CPU They now have the HT and HTT I think it is alot of people call the link between CPU and Memory The FSB even though it Isn't Perhaps Your motherboard calls it HTT or HT?

---

### Post by dinub1 on 2007-10-09
> **Yellow Onion said:**
> Are You Running an AMD?
Just cause AMD (939 and perhaps above) doesnt have a FSB since the memory controller is in the CPU They now have the HT and HTT I think it is alot of people call the link between CPU and Memory The FSB even though it Isn't Perhaps Your motherboard calls it HTT or HT?

Hold. there was a post here... there is an over clocking utility for Linux I downloaded and ran it. I will elt you know soon. 
Yes I am running AMD. An X2 6000 socket AM2 but also a XP3200 64 bit single core S939 CPU. The fact that the memory controller has been moved from the motherbiard chipset to the CPU has nothing to do with FSB and over clocking. in my Understanding what peopel call FSB or Bus is the "Network" or connections that components talk to each other. it is also governed by a clock and runs at a frequency adjusted to the CPU's freq. Over clocking is increasing the system frequency over its "rated" one.
You can still raise the sytstem frequencies, that is CPU's video card , RAM etc by setting thie BIOS to manual adjustments, provided that mothrhboard allows it.  Another parameter that is sometimes adjustable is the multiplier on the CPU. On some models it is locked, but on other, it is not. Provided that it is not locked you can adjust that in order to achieve over clocking. I have seen many boards where the CPU multiplier is locked and cannot be adjusted, but I do not remember any motherboard that would not allow the CPU or FSB's frequencies to be changed (if set to manual).
What CPU and what motherboard are you using ? BTW your mention of the nTune to adjust the chipset or FSB frequencies.That only works if that specific motherboard uses a NVIDIA chip set. For other brand of chip sets, Sys, ALI, VIA, AMD, etc  that utility may not work.

---

### Post by dinub1 on 2007-10-09
$ sudo apt-get install powertweak
$ sudo gpowertweak

---

### Post by pishiman on 2007-10-12
> **dinub1 said:**
> [COLOR="Navy"][I]15% performance boost = pay extra $ 100 for CPU/mobo upgrade
15% performance boost via OC = your gf is happy
[/I][/COLOR]
:) Well, question is, 15% performance boost or 15% overclocking, are your applications running 15 % faster ? No, no no :) How much performance boost one gets from upgrading say a 2 GHz CPU to a 3 GHz one? (50% "power boost")? Do application run 50% faster? No way. Except for heavy applications like Photoshop, video editing or perhaps 3D CAD modelling that may benefit from the extra power, other "standard" applications will run more likely at the same speed. You can improve PC performance by adding more RAM. So overclocking, other than achieving perhaps personal satisfaction for making your system run faster, to its limit... there is not much advantage, in my views.
__________________

I do PS, CAD and video editing all the time :) As for the RAM, it's a storage device, not a performance booster. If you're talking about high-speed low-latency RAMs 1) My budget board won't accept it 2) they cost 3x more so I'd rather buy a new CPU. If you're just telling me to increase RAM capacity, well I've already got 2 GB and it's largely sufficient.

Btw, gpowertweak doesn't work :( I get an error, see above

---

### Post by dinub1 on 2007-10-12
> **pishiman said:**
> I do PS, CAD and video editing all the time :) As for the RAM, it's a storage device, not a performance booster. If you're talking about high-speed low-latency RAMs 1) My budget board won't accept it 2) they cost 3x more so I'd rather buy a new CPU. If you're just telling me to increase RAM capacity, well I've already got 2 GB and it's largely sufficient.

Btw, gpowertweak doesn't work :( I get an error, see above

I agree with you that RAM is a storage device. However for the same given CPU and motherboard, you can boost performance by adding more RAM (provided that you have 512 MB or less of it). This by simply  minimizing the need for a swap file on hard disk which is slow.

Otherwise I agree with you that 2 GB of RAM is sufficient and you wouldn't gain anything sensible if you add more. But over clocking  won't get you much better. You may see a raise in overall clock count but that does not reflect much in the PC performance.

The gpowertweak seems to work without any error on my laptop. However I did not try to play with it yet.

---

### Post by nibsa1242 on 2007-10-14
I have a related problem. My computer is overclocked, and would like the over clock to work in Linux. With my current configuration (allowing for Powernow support in the BIOS), my cpu always gets set to the factory max 2.200 GHz, I'd like to to be set to what ever the bios tells it that it should be set to. Some times that is 2.420 GHz, other times that is 2.56 GHz depending on my mood at the time.

However, as far as I can tell I can't seem to overwrite sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq even as root. Can anyone help me?

---

