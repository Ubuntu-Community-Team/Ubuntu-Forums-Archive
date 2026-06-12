---
title: "AMD system suggestion for Linux"
date: 2011-01-31
forum: Hardware
---

### Post by tareq.mhd on 2011-01-31
I'm gonna buy AMD processor and motherboard. Give me suggestion.
My initial choise is -

AMD Athlon II X4 640 or AMD Phenom II X4 955
Gigabyte 880GM-USB3 or MSI 880GM-E41 
4 GB DDR3 RAM 

This is going to be my next 3 yr System. I am not an addicted gamer, mainly I will use the system for downloading. It will run 24x7 (!!!). My present PC is -

Intel C2D E7500 2.93 GHZ
ASUS g31 P5KPL-AM
4 GB DDR2

Now tell me guys is it good choice or I need to change my decision.

Main point is I have to use Ubuntu, Opensuse as operating system with Windows 7. I'm little bit concern about reputation of MSI motherboards on linux.

---

### Post by gradinaruvasile on 2011-01-31
I would say go with ASUS. I have seen some Gigabytes kicking the bucket lately (not to mention MSI...).

As for CPU, go with the Phenom if you want real power. The Athlon II quad cores are a bit slow core for core because of low amount of cache.
On top of this, i would also recommend an nvidia video card if you want games to work properly.
Although the newer integrated Atis are quite good if you dont need them for 3d-wise complex games.

---

### Post by cascade9 on 2011-01-31
I'd say go with gigabyte. I've seen some of the newer asus boards die very quickly. IMO they arent as good as the used to be (and its been a long, long road downhill). But better asus than MSI, or asrock....

That is very subjective though.

---

### Post by tareq.mhd on 2011-01-31
In our country Gigabyte and MSI are available for AMD. So I have to buy one of them. I am giving a list of available motherboards -

Gigabyte GA-880GM-USB3
Gigabyte GA-880GM-UD2H
Gigabyte GA-MA78LMT-S2
Gigabyte GA-M68MT-D3

MSI 740GM-P25
MSI 760GM-P33
MSI 880GM-E41
MSI 880GMA-E45
MSI 890GXM-G65

Now tell me among them which one would be most linux friendly.

---

### Post by khamil8686 on 2011-01-31
i use a gigabyte board (MA78GPM-DS2H) with an am2+ amd phenom II 955 cpu and i never have any problems with it, im very satisfied with the board and cpu :) board has run for 3 years (not non-stop :P i turn it off at night to save energy since standby still uses some electricity)

---

### Post by KegHead on 2011-01-31
Hi!

I have an old AMD based compaq laptop.

Not sure about the mobo, but it seems much slower that my Intel machines (3).

KegHead

---

### Post by gradinaruvasile on 2011-01-31
Lol. That will help him make an informed decision...

> 
In our country Gigabyte and MSI are available for AMD. So I have to buy one of them. I am giving a list of available motherboards -

Gigabyte GA-880GM-USB3
Gigabyte GA-880GM-UD2H
Gigabyte GA-MA78LMT-S2
Gigabyte GA-M68MT-D3

MSI 740GM-P25
MSI 760GM-P33
MSI 880GM-E41
MSI 880GMA-E45
MSI 890GXM-G65

Now tell me among them which one would be most linux friendly.


In this case, go with Gigabyte. The 880GM  looks nice with its onboard AMD Radeon HD 4250 card (has hardware decoding via libva, it can be used in vlc). I dunno about USB3, may be helpful in time if the kernels will support it.
Their Linux-friendliness is about on the same level, maybe the USB3 support might be a problem until it will be integrated in Ubuntu's kernels. 

Do not buy a M68 chipset board - regardless its onboard nvidia card (this is a plus, but the 7000 series has no hardware decoding) that is an old chipset and has limited its HyperTransport Bus speed to 2000 MT/s, whereas the other newer boards have 5200 MT/s thus greatly improved performance with the same AM3 CPU.

---

### Post by tareq.mhd on 2011-02-01
Now I am thinking of getting AMD Phenom II X4 and Gigabyte GA-880GM-USB3.

---

### Post by cascade9 on 2011-02-01
+1 gradinaruvasiles post. As an aside, I've got a board with a USB 3.0 chip. It works, but as I only have USB 2.0 devices I cant speed test it. BTW, that machine is not running ubuntu, but I didnt need to do anything for the USB 3.0 ports to work. I've used them with kernel 2.6.35+ (rolling release) 

Given those options, I'd get the GA-880GM (the only difference between the versions is USB3.0)

---

### Post by khamil8686 on 2011-02-01
> **tareq.mhd said:**
> Now I am thinking of getting AMD Phenom II X4 and Gigabyte GA-880GM-USB3.

its extremely similar to my MA78GPMDS2H, like an updated am3 and usb 3.0 version, my mobo works out of the box on a new kubuntu install so i dont forsee any problems with that setup :)

---

### Post by tareq.mhd on 2011-02-01
I am using XFX 8600 GT now but looking for new card after making the AMD system. My choice is AMD radeon graphics card. Like 5750 or 5770; what's your opinion on this ?

---

### Post by khamil8686 on 2011-02-01
i have a GeForce 8400 GS PCI-e graphics card, id go with Nvidia because they seem to have great support for linux, the integrated ati card my mobo came with had poor support and the drivers seemed buggy, after switching to the GeForce nvidia card ive had no problems and graphics are clear, crisp, and ive never had problems with it, however now that amd has absorbed ati im not sure if they support linux better now or not, but until i hear otherwise id recommend going with an nvidia card :)

---

### Post by cascade9 on 2011-02-01
> **tareq.mhd said:**
> I am using XFX 8600 GT now but looking for new card after making the AMD system. My choice is AMD radeon graphics card. Like 5750 or 5770; what's your opinion on this ?

If you dont game, keep the 8600GT. 

Also, if you are getting a vdeo card, a 770/870 chipset motherboard is a better way to go. The only reasons to get a 880 over a 870 is either you wantt o use a microATX case, or supply issues.

---

### Post by MooPi on 2011-02-01
I have been using MSI lately for builds and find them very nice. The computer I'm using is a 790X-G45 with a Phenom II X2 545 dual core. Picked up the cpu and motherboard on special price and is functioning perfectly and is of good quality. I also have used and will continue to use 870-G45. I have a Propus chip as well as a Phenom and you will get more raw performance from the Phenom but for the price difference the Propus chips are amazing. I would also recommend the AMD graphics as well as I use it for both gaming and every day tasks. Currently have a Saphire 5870 in my gaming rig and an inexpensive ATI 4350 for my daily rig. Works straight from the box using compiz eye candy without special proprietary driver.

---

### Post by eflat on 2011-02-01
> **cascade9 said:**
> If you dont game, keep the 8600GT. 

Also, if you are getting a vdeo card, a 770/870 chipset motherboard is a better way to go. The only reasons to get a 880 over a 870 is either you wantt o use a microATX case, or supply issues.
If you don't game or do video/image editing, is there any reason to consider a separate video card?

---

### Post by cascade9 on 2011-02-02
> **eflat said:**
> If you don't game or do video/image editing, is there any reason to consider a separate video card?

Yes, lots. 

The main one if that with most onboard video, the video RAM is taken from the main system RAM. Not only does this reduce the amount of RAM you have to use, it also means that the main RAM is taxed more heavily ('normal' tasks that would go though RAM still do, but now there is also video information as well). 

There are motherboards with onboard video that have extra RAM installed to the motherboard so you dont need to use the main system RAM ('sideport RAM') but they cost more than a motherboard with no video + a cheap video card.    

There are other reasons, that is just the most clear cut reason to have a video card.

---

### Post by slooksterpsv on 2011-02-02
I have a Gigabyte board in my Quad core system. I've had my quad-core AMD for 3-4 years now? It's the 780G, S2H (don't remember exact model).

---

### Post by Vaphell on 2011-02-02
i have a box with quad phenom II and asus mobo with integrated radeon 4250 (128MB of its own memory) which works good enough that i don't feel forced to buy a dedicated card yet. I even played Starcraft 2 on it plus few older games (in windows). There are some issues like the classic screen tearing in movies and lack of hardware acceleration but otherwise i can't complain and have the luxury of waiting before i am forced to choose between dedicated nvidia and radeon - it's almost a year already :)

---

### Post by gradinaruvasile on 2011-02-02
> **cascade9 said:**
> Yes, lots. 

The main one if that with most onboard video, the video RAM is taken from the main system RAM. Not only does this reduce the amount of RAM you have to use, it also means that the main RAM is taxed more heavily ('normal' tasks that would go though RAM still do, but now there is also video information as well). 

There are motherboards with onboard video that have extra RAM installed to the motherboard so you dont need to use the main system RAM ('sideport RAM') but they cost more than a motherboard with no video + a cheap video card.    

There are other reasons, that is just the most clear cut reason to have a video card.

Newer onboard GPUs seem to fare quite well. I for example have a 8200 onboard (dual channel 800 MHz RAM on the mobo) and it outperforms (very visibly) a dedicated 7300. I had 2 GB RAM initially and never felt the 256 MB that was allocated to the card.

---

### Post by cascade9 on 2011-02-02
> **gradinaruvasile said:**
> Newer onboard GPUs seem to fare quite well. I for example have a 8200 onboard (dual channel 800 MHz RAM on the mobo) and it outperforms (very visibly) a dedicated 7300. I had 2 GB RAM initially and never felt the 256 MB that was allocated to the card.

I'm not at all suprised that a 8200 IGP would outrun a 7300. The 8200 has more shaders, more texture mapping units, more render outputs, and depending on the 7300 model more core MHz, and faster memory (even though its using the system memory). IIRC the 7300 card quite often used some system RAM as well...again depending on model (the cheaper models used 'turbocache'). 

Newer architecture helps as well. 

With 2GB, having 256MB stollen isnt so bad.

---

### Post by ridowan007 on 2011-02-07
> **tareq.mhd said:**
> In our country Gigabyte and MSI are available for AMD. So I have to buy one of them. I am giving a list of available motherboards -

Gigabyte GA-880GM-USB3
Gigabyte GA-880GM-UD2H

You are from Bangladesh right? Do you know the price of this two Gigabyte GA-880GM motherboards? Also where you find this boards? I am also from Bangladesh and thinking to buy a pc. By searching net I decided to go with Athlon 2 X4 640 processor(at [http://www.ryanscomputers.com/]("http://www.ryanscomputers.com/") this is listed as 8500Tk). But I can't decided the motherboard. Now reading this I am thinking of buying one of the Gigabytes board. Thanks.

---

