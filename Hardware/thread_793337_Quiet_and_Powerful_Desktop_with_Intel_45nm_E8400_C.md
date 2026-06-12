---
title: "Quiet and Powerful Desktop with Intel 45nm E8400 Core 2 Due, NSK 2480 case, 120mm fan"
date: 2008-05-13
forum: Hardware
---

### Post by limejuice on 2008-05-13
I just built a new computer last week, with the main requirements:
[LIST]
[*] fast
[*] best bang for the buck, i.e. knee in the price-performance curve.
[*] quiet -- use 120mm fans and quiet components
[*] integrated graphics ok -- I don't care about 3D
[*] case as small as possible, but not to the deteriment of any of the above requirements.
[/LIST]

I picked Intel 45 nm E8400 Core 2 Duo chip because smaller process gives you more power for less wattage/heat, and also you can overclock it on air.

I picked NSK2480 case because it is a nice size for workstation and has good design for cooling the processor with big 120 mm fans blowing right on it.  It uses a micro ATX motherboard.

I threw a quiet HD and also some OCZ memory with a heat sink (good if you want to overclock).

I am using the onboard Intel graphics since I don't care about 3D graphics.  If you want better graphics, you will need to add a PCIx16 Express video card.

Or, another option is to pay $5 and get the Intel x3500 integrated in the Intel BOXDG35EC LGA 775 Intel G35 Micro ATX Intel Motherboard.   I didn't notice this board at the time I ordered my components; Otherwise I probably would have bought the Intel mobo rather than the Gigabtye mobo since Intel has better graphics for about the same price. 

**Configuration**

I put the box together in about 3 hours. Initially it wouldn't boot up, due the 4pin power connector being loose. After fixing that, it booted up fine, and I popped in my Ubuntu 8.04 64bit Desktop installation CD, and I had a the system up and running in about 30 minutes. Everything worked out-of-the-box with no problems. I did have to install the "restricted" package to get MP3 and adobe flash to work, but I had no hardware compatability problems.

The next night I installed Virtual Box 1.6.0, and then I installed Windows XP from a slipstreamed Wincows XP SP3 DVD, and I got that also working with zero problems! I still need WIndows XP because my company's VPN remote access software only works with windows, so in order to remote desktop to my workstation at my work, I have to run windows xp in virtual box, and then connect through the VPN, and then run remote desktop. I was pleasantly surpised it all worked great!
So, I thought I'd share my configuration with everyone in case someone else is looking to build a new box to run Ubuntu 8.04 with requirements similar to mine.

Following is the component list.
Cheers,
-Limejuice

**Linux Ubuntu 8.04 Quiet Powerful Desktop With Intel 45nm E8400 Core 2 Duo, NSK 2480 case, 120mm fans**

**Qty. 	Product Description 	Price**]
1 	Antec New Solution NSK2480 Black/Silver 0.8mm cold-rolled steel MicroATX Desktop Computer Case 380W Power Supply - Retail
Model #: NSK2480 $104.99
    
1 	GIGABYTE GA-G33M-S2L LGA 775 Intel G33 Micro ATX Intel Motherboard - Retail
Model #: GA-G33M-S2L 	  	$94.99

1 	Intel Core 2 Duo E8400 Wolfdale 3.0GHz LGA 775 65W Dual-Core Processor Model BX80570E8400 - Retail
Model #: BX80570E8400 $198.99

1 	OCZ Reaper HPC Edition 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model OCZ2RPR800C44GK - Retail
Model #: OCZ2RPR800C44GK	$109.99

1 	SAMSUNG HD250HJ 250GB 7200 RPM SATA 3.0Gb/s Hard Drive - OEM
Model #: HD250HJ $59.99

1 	Microsoft ZG6-00006 Black PS/2 Wired Standard Keyboard 500 - Retail
Model #: ZG6-00006 	$11.99

1 	Pioneer 20X DVD±R DVD Burner Black IDE Model DVR-115DBK - OEM
Model #: DVR-115DBK $26.99

1 	Scythe SCMNJ-1000 80mm Sleeve "NINJA MINI" CPU Cooler - Retail
Model #: SCMNJ-1000	$34.99

**Subtotal: 	$642.90**

All prices are prices I paid at newegg. You can probably get the components slightly cheaper on some other sites, but I just ordered in from newegg for the convenience and service (in case I had to return something.)

---

### Post by teaker1s on 2008-05-13
pc building / customising can be a addiction, I've got 6 computers and it's great to have a pc :popcorn:exactly as you want

---

### Post by ManicDeity on 2008-06-01
Excellent.  Glad to hear that everything went well.  My laptop went to hell (dragged it all over Afghanistan so not really shocked), so I decided to switch over to ubuntu and build a new pc from scratch.  I was curious how the Wolfdale would work out so I was happy to see your post.  Now I just need to order the parts and learn how to use linux (part of the process which I want to do).

My only difference is that I will be adding a GPU because I really want dual monitor support.

Cheers.

---

### Post by froghunter on 2008-07-04
limejuice, 

not sure if you will respond to this followup, but how is the box treating you? still quiet, change anything? i have become a bit obsessed with figuring out the components for my home server which one day will become morph into a HTPC, and came across your post. I was wondering what the power draw is on your system (if you happen to know) and the sound? Also, wasn't sure if you had any board recommendations if you were more concerned with sound output (for video I can always put a card in since there appears to be plenty of room). Thanks for the input, I really appreciate it.

---

### Post by limejuice on 2008-07-04
Hi froghunter,

The box is still working great. The only thing I would have changed is what I mentioned in my post, i.e. switch to newer G35 mobo chipset like Intel BOXDG35EC LGA 775 Intel G35 Micro ATX Intel Motherboard.  

The box is very quiet with the two 120 mm fans running on low speed and the power supply fan on back. I don't hear anything with the box 3 ft away from me under my desk. Each of the Antec 120mm fans have a three position switch low-medium-high speed (default is low).

One thing I didn't mention is that I reversed the 120 mm fans so they are blowing air into the case to create positive air pressure, and I placed a air filter over each of the 120mm fans.

The original setup with the fans blowing out is definitely better for keeping the cpu cool. One of the 120mm fans is right next to the Scythe Ninja heatsink, and so it gets the hot air out very well;  This looks like a very good setup to overclock the e8400 with air cooling. If you wanted to overclock, you could bump up the speed to medium or high for the 120mm fan next to the heatsink.

Re: power. I don't have a kill-o-watt meter so I can't tell you exactly, but this setup should be relatively low power for the performance, i.e. high power per watt,  because the e8400 chip is 45nm (smaller chips uses less power), dual-core as opposed to quad-core (quad core unnecessary except for certain applications like media encoding,etc.), and uses onboard video and audio.  One way to use even less power would be use a Winchester Digital GreenPower HardDrive instead of the Samsung drive I used.

BTW the onboard video works fine with most of compiz (just makes sure you switch to Intel modesetting drivers). One thing that isn't working is rotating the cube. For onboard video, it works very well.

Re: sound, I can't really help you. I'm not an audiophile.  I've been listening to stuff like Billy Joel, Elton John, Jason Mraz, etc. using the default sound output to my crappy 10w speakers and the sound seems fine to my ears.

On newegg, I posted my wishlist with the parts I used. You can search for "ubuntu". It's titled "$650 Linux Ubuntu 8.04 Quiet Powerful Desktop With Intel 45nm E8400, NSK 2480 case, 120mm fans'

---

### Post by froghunter on 2008-07-05
Thanks for the info. Personally, right now I don't really think I need the HDMI outputs, and reading around, it looks like the D-Sub can do whatever I need for now. But considering the Intel board is the same price as the G33 mobo you put in yours, I guess I can't go wrong.  Thanks for the suggestions on the fans, though I am not sure what setup I will go for, but I will also be putting a Ninja mini in. And, this is going to sound horrible, but I think for now, until I am ready to beef up the system (only server now, HTPC one day), I am going to put a single core processor in it, the $40 the [Celeron 430 Conroe-L 1.8GHz]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116039"). So basically, I am getting the base for a system I want later, so when prices drop some more and/or I have more cash, I have a board and box which are perfect for my expandability. Any thoughts on that? And last question, since you have gotten in the antec case, do you think with the extra heat-pipe on the Intel board I will run into any issues, and also, I was still going to use the Ninja mini (since I can always put it on my uber fast Wolfdale when that happens)? Thanks again, I know what I am thinking sounds a little counter-intuitive, but I like to buy things I can keep around (versus a one shot KPC or something). Thanks for answering a noobs questions, I appreciate it.

---

### Post by froghunter on 2008-07-25
Limejuice,

After much hemming and hawing, I am going back on my post and going for a Wolfdale chip. Quick question: so you aren't using the fan with mini ninja, but just reversed the fan closest to the ninja? Do you think the ninja's fan would have made that much more noise, and since you aren't using it, any thoughts about an interesting place to put it (i.e., over on that chamber with the HDD)? I am about to pull the trigger on a decent setup, though unfortunately it might run XP as the host with a VM for a server due to hardware conflicts with ALSA audio over HDMI (ASUS P5E-VM HDMI mobo). Thanks again for all the help.

---

