---
title: "First computer build help/suggestions"
date: 2008-07-26
forum: Hardware
---

### Post by Widow_Maker on 2008-07-26
First off, I am really new to Ubuntu and these forums (so if this is in the wrong place, sorry)

I am planning on building my first computer for the sole purpose of audio editing. I will be using the program 'Goldwave' to process recordings. (I will be using 'Wine')

My current system is extremely slow (and old)... something like a 2 gigahertz pentium 4 processor/512 ram, etc. Anyway, it takes around 20 minutes to process about 40 minutes worth of sound. I already checked my current motherboard, and it can't support anything that would significantly improve the performance, so I decided to get a new system.

I really don't care how much all this will cost (within reason), and figure that a quad core processor, at least 4 gb ram, and a very nice sound card would be a good start... but I'm not really sure what all to get.

Such as: 
-what motherboard will support a good processor/ram?
-does Ubuntu have certain limits to how much ram it will support (Like windows XP 32 - bit supports 3.5 gigs max)?
-any other general advice/suggestions to make all this run smoothly with Ubuntu?

(and since I will be using this for audio editing, I can skimp on the video card)

Thanks to any advice you all can give - greatly appreciated!

---

### Post by waspbr on 2008-07-26
oh how much I envy you... 

building a computer is a lot of fun... I remember the good old days when I build my first PC, good times...

If I am not mistaken the limit of most motherboard nowaydays is 8Gb, I would definitely recommend ubuntu64, actually ubuntustudio 64 bit. 

As for the processor, I have traditionally picked AMD processors due to their commitment to open source and all,if ya looking for quad core, the phenom is a good choice not extremely expensive, but I have heard that performance wise it lags a bit behind intel... you are probably going to look for AM2(+) socket motherboards for AMD's , not sure what the socket for intel's are haven' t used them in a long time. Also I have traditionally stuck with ASUS for that.

graphics card wise, well, that' s your call.

Now the soundcard, I am not an expert on this, but for average use ASUS had been making good cards. I was going to recommend CREATIVE if not for that whole drivers debacle. 

i know this is a little superficial but it is a start...

---

### Post by pytheas22 on 2008-07-26
Ubuntu should be able to support as much RAM as you can expect to be able to put into one motherboard.  The limitation on how much memory you can have usually comes from what your processor can support (with ia64 processors, made for servers, I know that Linux can support up to something ridiculous like 64 gigabytes of memory), not the operating system.  Four gigabytes should be fine; eight would probably also work; even 16 may be alright as long as you're sure that your motherboard and processor support it.  Just make sure to read the motherboard and processor specifications carefully so that you select an appropriate amount, type and speed of RAM.

As the poster above says, you'd definitely get more out of your system if you run a 64-bit kernel.

For graphics I'd recommend looking for a motherboard with integrated Intel video.  Intel graphics are nice because, unlike nvidia and ATI cards, they don't require closed-source drivers to support 3d-acceleration in Linux; they're also generally a lot cheaper.  You can't play really fancy 3d games with Intel video, but otherwise it's always been nice and zippy for me (including desktop effects).

You probably know more about sound cards than I do.  All I'll say is to do your research first and make sure that it's supported well by alsa.  I know that there are issues with some of the newer Intel sound cards.  But as long as you do a few Google searches ("[sound card name] + ubuntu") before buying, you should be able to avoid any problems.

---

### Post by Widow_Maker on 2008-07-26
Thanks for your advice! I plan on going to Fry's in a day or two and will definitely look into your suggestions.

---

### Post by madman92 on 2008-07-26
I agree with the above posters about RAM and graphics and sound, however look into Intel processors. I'm not saying this because I'm an Intel fanboy (I run an AMD system), but because recently their processors have been leaps and bounds above AMD, and they also offer more 45nm processors which equates lower heat and power -> better overclocking. 
Also try newegg.com, they generally have better prices, although you might get lucky at fry's

---

### Post by SoloSalsa on 2008-07-26
> **madman92 said:**
> I agree with the above posters about RAM and graphics and sound, however look into Intel processors. I'm not saying this because I'm an Intel fanboy (I run an AMD system), but because recently their processors have been leaps and bounds above AMD, and they also offer more 45nm processors which equates lower heat and power -> better overclocking. 
Also try newegg.com, they generally have better prices, although you might get lucky at fry's
I *am* an Intel fanboy, and "leaps and bounds" is exactly right.  Disregarding overclocking, the efficiency means lower electric bill.
> **waspbr said:**
> As for the processor, I have traditionally picked AMD processors due to their commitment to open source and all,if ya looking for quad core, the phenom is a good choice not extremely expensive, but I have heard that performance wise it lags a bit behind intel... you are probably going to look for AM2(+) socket motherboards for AMD's , not sure what the socket for intel's are haven' t used them in a long time. Also I have traditionally stuck with ASUS for that.
Intel has been using socket T (LGA 775 [http://en.wikipedia.org/wiki/Socket_T](http://en.wikipedia.org/wiki/Socket_T)) since 2004.
> **pytheas22 said:**
> For graphics I'd recommend looking for a motherboard with integrated Intel video.  Intel graphics are nice because, unlike nvidia and ATI cards, they don't require closed-source drivers to support 3d-acceleration in Linux; they're also generally a lot cheaper.  You can't play really fancy 3d games with Intel video, but otherwise it's always been nice and zippy for me (including desktop effects).
Very true.  All Intel chipsets have open drivers.  Same goes for Intel NICs, wired and wireless.
[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)


> **pytheas22 said:**
> You probably know more about sound cards than I do.  All I'll say is to do your research first and make sure that it's supported well by alsa.  I know that there are issues with some of the newer Intel sound cards.  But as long as you do a few Google searches ("[sound card name] + ubuntu") before buying, you should be able to avoid any problems.
ALSA compatibility:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)


> **Widow_Maker said:**
> -any other general advice/suggestions to make all this run smoothly with Ubuntu?
Get a good power supply.  Unless it has a super discount, do not pay less than fifty USD.  **[If you can, get one that is 80 PLUS rated.]("http://www.80plus.com/manu/psu/psu_join.aspx")**  My personal favourite PSU brand is Corsair (they make the best RAM, too, IMO).  They are actually manufactured by SeaSonic.  Both SeaSonic and Corsair power supplies are always highly rated and reliable.  They back them with a five year warranty (cheap brands only have a one or two year warranty; that is not very assuring, for a vital part of any system).  Another great power supply brand is Silverstone.  They are famous for being quiet, particularly popular in home theatre PCs and media machines.  But they are expensive, so you should probably pick some other brand.

My favourite store is Newegg.  These are their Corsair PSUs:
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=50001459+40000058&Manufactory=1459&SubCategory=58&SpeTabStoreType=0](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=50001459+40000058&Manufactory=1459&SubCategory=58&SpeTabStoreType=0)
I have the smallest one, 450 watts, and my system only uses two-hundred.  To determine how strong your PSU needs to be, estimate your total average power usage.  Add up the average power needs of every component, or search for a power supply estimator tool online.  Your total power usage should be between half and three-quarters of the PSU's maximum capacity.  That leaves room for any future changes, and that load range is also the most efficient.

---

### Post by jimv on 2008-07-26
Just a bit of trivia - 2 ^ 32 = about 4 billion = so a 32 bit processor can only address 4 giga(billion)bytes of ram.

---

### Post by Widow_Maker on 2008-07-27
Thanks for the additional suggestions!

I did some research and am looking at this configuration (not complete yet):


Power supply: Corsair CMPSU-650TX 
CPU: Intel Core 2 Quad Processor Q9450 (4x 2.66GHz/12MB L2 Cache/1333FSB) 
Processor cooling:  INTEL Certified Liquid CPU Cooling System kit **Is this necessary?**
Motherboard:  Asus P5K Premium Intel P35 CrossFire Chipset     ***I am pretty clueless on this***
Ram: Corsair Dominator DDR2-1066 PC2 8500 4gb (2 X 2gb)
Video Card: Nvidia GeForce 8400gs 512MB
Hard Drive: 320 gb serial - ata - II, 3 gb, 7,200 RPM, 16M cache (maybe times 2, but I might add it later)
CD/DVD drive: 20X Dual Format/Double Layer DVD±R/±RW + CD-R/RW Drive (with lightscribe)
Sound Card: Creative Lab Sound Blaster X-Fi Titanium Fatal1ty Champion Series    
Network card: ***I have no idea =(***... but it should be 802.11n compatible

*And I need a suggestion on a good case. 

...I think thats what I need to start off - did I forget anything important or select something that won't work with Ubuntu well?

And I plan on using this for audio recording/editing, which takes my current set up a very long time.

Thanks for any advice you could throw my way!

ps-do any of you all know of a good link to a pc build walkthrough (preferably with pictures/etc)? Thanks!

---

### Post by pytheas22 on 2008-07-27
I think it all looks good.  The only thing I'd caution about is that according to [Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131180"):
> 
The chipset officially supports the memory frequency up to DDR2 800MHz. Tuned by ASUS Super Memspeed Technology, this motherboard natively supports up to DDR2 1066MHz

I don't know what "Super Memspeed Technology" is, but you may want to make sure it's not some stupid thing that can only be configured easily through Windows (unlikely, but doesn't hurt to check).  Otherwise you may not be able to get your memory to run at full speed.

Also this board has somewhat low ratings on Newegg, which doesn't necessarily mean anything, but you may want to read through the customer comments to see if there's anything that would bother you.

> Network card: ***I have no idea =(***... but it should be 802.11n compatible

Probably an Intel card will be the best way to go.  Their support for 802.11n is good and, as with Intel video, there are very good open-source wireless drivers for Intel chipsets.  Here is an [example]("http://www.compuvest.us/ProductDetails.aspx?ProductID=317671") (it's just the first result that came up on Google).
> 
ps-do any of you all know of a good link to a pc build walkthrough (preferably with pictures/etc)? Thanks!

I don't have anything specific to recommend, but there are plenty of guides that you can find through Google, as well as some useful videos on youtube.  More importantly, any decent motherboard should come with a good manual to guide you through the setup, which in my experience is the most useful resource.

---

### Post by Cresho on 2008-07-27
i like my fry's of city of industry.

I purchased a
amd 64bit dual core black edition 6400
gigabyte GA-M61P-S3
audigy gamer 24bit (gigabyte onboard gpu and audio sucks)
a data ddr800 2gb
2 sata drives 3gb/s trans both maxtors @500gb each
BFG 8800gt oc nvidia
kworld115 high definition television tuner
avermedia stereo tv
coolermaster wave master all aluminum case
thermaltake power 550 watts (cheapee but goodeee)
all aerocool fans 15db audible.  like nothing sound.
zalman main cpu fan
thermaltake south or northbridge cooler with fan
thermaltake gpu faun(original gpu temp with stock was 74c but with thermaltake and a zalman fan controller set to minimum temp is now 44c)
silverstone fan controller and silverstone multimedia front bay with lots of extras.
pioneer dual layer dvd burner(useless if you want to make dual layer movies and if your home dvd player doesnt accept only singler layer)
5.1 logitech thx system.
HP2408 24 inches of 92% eyeblinding gamut @ 6bit color(best color dithering in the market)!  you see banding of colors in other brands but not this one

for video and pictures, i use a sanyo xacti HD100 high definition.  Compatible in ubuntu with a few tricks i found.

i did my research and all is compatible in ubuntu.  everything loads and everything runs even the multimediabay.  nothing is left behind.
it is all compatible in ubuntu right off the bat!


I love the fact that in ubuntu while i am typing this, i am rendering one video in vegas demo version under virtualbox windowsxp, running wine rendering more videos under virtualdub, still be able to play savage2 at full framerates, doom3 at full speed.  it is just nice to see how technology has come. Compiz running too!  one of my cpu cores is at 87% while the other is 0.  but when I run those other intensive cpu software, I still don't get bothered.  Compiz runs very smooth.  my gtk apps run fast, nautilus doesnt suffer.

To sum this up, my rig is silent.  I can barely hear the hardrive.

---

### Post by jimv on 2008-07-27
Instead of the 8400gs, I'd get a 8800GT, it's not too much money and it's a much much better card.

Also, instead of the Corsair RAM, i'd get Gskill:
[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16820231122](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16820231122)
It's excellent RAM, and you save quite a bit of money, which you can put toward the video card.

AND you don't need to buy a CPU fan as long as your CPU comes with one.  The stock fans are more than enough to keep your chip cool.

---

### Post by kspncr on 2008-07-27
First off, I wish I had the money right now to be building another computer...

> **Widow_Maker said:**
>  
Processor cooling:  INTEL Certified Liquid CPU Cooling System kit **Is this necessary?**

I would say no, it probably isn't necessary. Even though I'm sure you're using this for gaming: I'm sure the fan and heatsink included with your cpu is enough.

As for case suggestions, it really depends on how much you want to spend. I you want to spend $150+ then Lian-Li has some high-quality cases (I think they may have some cheaper ones as well). On my second computer build, I was a little shorter on money and got a pretty nice Apevia for around $80.

I'm an AMD fan, but I hear Intel has been putting out some fine products as well.

Again, I'm envious. Good luck and remember to have fun!

---

### Post by Widow_Maker on 2008-07-27
For a better mother board, what do you all think of this?

ASUS P5E3 Deluxe/WiFi-AP LGA 775 Intel X38 ATX Intel Motherboard
([http://www.newegg.com/Product/Product.aspx?Item=N82E16813131218](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131218))

and then the 8800GT video card (why not?)

and for ddr3:
CORSAIR XMS3 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333 ([http://www.newegg.com/Product/Product.aspx?Item=N82E16820145198](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145198))... or is there a better alternative that you all know about?

I think it would be a good idea to change my memory choice to ddr3, but besides that, does it look like the rest would work?


And I was reading reviews of the intel Q9450 processor, where users were over clocking  it quite a bit. What kind of cooling system would I need? What I mean to say is, would I just be better off getting a good fan if I plan on over clocking my system or just leaving it as is?


And for the case - I am looking for something with a lot of room/easy to use-

NZXT Apollo Black SECC Steel Chassis ATX Mid Tower Computer Case ([http://www.newegg.com/Product/Product.aspx?Item=N82E16811146025](http://www.newegg.com/Product/Product.aspx?Item=N82E16811146025))

or

something like APEVIA X-Plorer ATXB8KLW-BL ([http://www.newegg.com/Product/Product.aspx?Item=N82E16811144104](http://www.newegg.com/Product/Product.aspx?Item=N82E16811144104)) although I kind of like the looks of the NZXT better...

or if any of you have had experience with cases, I would be willing to drop somewhere around $100 to about $150 plus or minus... with emphasis on ease of installation or hardware.

Thanks again to everyone!

PS- according the the newegg product description, the motherboard has onboard lan... so does this mean I don't have to buy a network card?

---

### Post by Widow_Maker on 2008-07-27
And what is the word with all of the drivers working with Ubuntu? (like video/sound card; etc) and where can I find them before I buy anything?

Thanks

---

### Post by pytheas22 on 2008-07-27
> and then the 8800GT video card (why not?)

I'd still highly recommend that you just stick with Intel video instead of nvidia, for the reasons that 1) the nvidia card is going to put more of a load on your PSU and generate extra heat; and 2) with Intel, you install Ubuntu and your graphics will "just work" perfectly.  With nvidia you have to fuss with getting the proprietary driver installed, which in principle is trivial but in reality can be a real hassle.  I like nvidia and have an nvidia card in one machine for gaming, but on other machines I use Intel, simply because it's easier to configure, more efficient and does everything besides run state-of-the-art 3D games, which I don't need.

Also, I don't know what the deal is with the onboard wireless on this motherboard.  I've tried helping some people with the same family of Asus boards, and the wireless does strange things...like the device doesn't appear anywhere in lspci or lshw, and I have no idea which kind of driver it's supposed to use.  I know it's supposed to be some kind of super wireless card that supports master mode and everything, but my sense is that it's difficult to get working in Linux (take a look [here]("http://ubuntuforums.org/showthread.php?t=729480&page=1") for an example specific to that model of Asus board).  You'd be better off buying a wireless card with an Intel, Ralink or (in most cases, but there are exceptions so research first) Atheros chipset...it will "just work."
> 
And I was reading reviews of the intel Q9450 processor, where users were over clocking it quite a bit. What kind of cooling system would I need? What I mean to say is, would I just be better off getting a good fan if I plan on over clocking my system or just leaving it as is?

If you want to overclock seriously, then you should buy a heavy-duty cooling system.  But so long as you're not going to do anything ridiculous (you shouldn't need to with a quad-core processor), a fan should be alright.  The new generation of Intel processors run much cooler than the old Pentium IVs anyway.  Just keep your eye on the CPU temperature; if it is running too hot, you could always add a better cooling system later.
> 
And what is the word with all of the drivers working with Ubuntu? (like video/sound card; etc) and where can I find them before I buy anything?

With the possible exception of wireless and non-Intel video, Ubuntu comes with drivers for virtually all standard hardware already built into the kernel--it's not like Windows where you have to install drivers for each new device.  There are exceptions, but as long as you do your research you should be fine.  Just do some Google searches for "[product name] + ubuntu" and if there are problems, they will be obvious, as will workarounds or solutions if they exist.  Look on Newegg under the "specifications" tab for the specific chipsets used by each component of a motherboard.

You should also pay special attention to your sound, since you need it to work 100%--make sure that the alsa driver will support all audio channels, et cetera.  If you were planning on using the onboard audio on the Asus model mentioned above, you may want to look for something else (get a PCI card): [http://www.google.com/search?q=%22ADI+AD1988B+%22+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=%22ADI+AD1988B+%22+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Widow_Maker on 2008-07-28
Very good information - thanks pytheas22!

Good point on the graphics card and motherboard.

---

