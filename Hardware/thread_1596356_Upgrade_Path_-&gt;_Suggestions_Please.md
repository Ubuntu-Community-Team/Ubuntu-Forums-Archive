---
title: "Upgrade Path -&gt; Suggestions Please"
date: 2010-10-14
forum: Hardware
---

### Post by jv2112 on 2010-10-14
I have a a budget of a about $250 and would like to give my system a shot in the arm because I know I wont be able to replace for 2-3 years. 

:confused:

I am interested in opinion of bang for the buck and any insight to any compatibility issues. I currently am using LM 9 and plan on sticking with linux but may experiment with new distro if I upgrade / drive.

Thanks in advance for your input. :cool:

I was considering(I will consider other options)->

CPU's

$160-Under Budget but leaves room for other parts
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103727]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103727")

$265 -> Kills Budget +
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103849]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103849")


Hard Drive-> 
$72 - SSD I thought it would work as a good boot drive giving a system speed boost--> NOT SURE if it works well with Current Linux Distros.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820227393]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227393")

$60 -> Just another 1T of storage. Don't need today but this is cheap. I would perfer a speed boost of the SSD but not sure if it is there.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822152185]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152185")


I would look at a video card but I believe the CPU and or HD would impact my usage more significantly.

Computer Use

Web Surfing
Learning Linux
Media Collection (Video,Pictures,Music)
 --Editing, Ripping, Storage

Occasional Light Games

> 

Current System Highligtts ->
Motherboard: Gigabyte Technology Co., Ltd.
Model: GA-MA770-UD3

CPU-> AMD Athlon(tm) II X2 245 Processor
Current Speed: 2900 MHz
      
Hard Drives: 
( Total Drives 60% of capacity) 

SAMSUNG HD753LJ --> Home & /
serial: S13UJ1KQ715626
size: 698GiB (750GB)


Seagate ST31500341AS --> Archive to both Drives
serial: 9VS2HPZR
size: 1397GiB (1500GB)

Seagate ST3250620AS --> Video Storage
serial: 5QE0CK1D
size: 232GiB (250GB)

Video Card -GeForce 9800 GT

RAM - 4 Gig DDR2 1066



---

### Post by lloyd_b on 2010-10-14
You don't seem to mention the amount of memory you have - this can be a *major* factor in system performance (too little RAM, and the machine is using swap heavily, slowing down processes and increasing the load on your disk drives).

Depending on how much RAM you have now, the best "bang for the buck" upgrade may simply be increasing it.

Lloyd B.

---

### Post by jv2112 on 2010-10-14
Oversight 

4 Gig DDR 2 1066.

---

### Post by cascade9 on 2010-10-14
You're right, video card will not impact on perfromance as much as CPU/RAM/HDDs. Apart from gaming and video playing. With video, if you've got an nVidia card that does VDPAU (nVidia hardware video decoding) then a newer card wont really help much, if at all. All the 9XXX cards onward have VDPAU, and most of the 8XXX cards (those that dont are the 8800GTX, 8800Ultra and 8800GTS 320/640 MB versions). 

BTW, revision 2.0 of that motherboard have ACC (Advanced Clock Control) which alows unlocking cores and/or cache on some AM2/AM2+AM3 CPUs (not the current Athlon II X2s though, but its possible that your version is old enough that it could get some cache or cores). Checking if there is ACC in the BIOS would be easier than somebody trying to figure out which revision you have. If you do have ACC, and want to run a minor risk, you could get a Phenom II X2 550/555 and unlock 2 cores (a X2 555 then runs as a X4 955). Its not always going to work, there is always the chance that one of the 'locked' cores is faulty, but if it does its a cheaper way to get a Phenom II X4. 

A 1090T would help with video ripping more than a 965, but overall the 965 + SSD would be faster. Thats probably the option I'd go for if you dont have ACC, or dont want to risk getting a bad core.

---

### Post by jv2112 on 2010-10-14
Cascad9,

Thanks for the useful insights. My board is a Revision 2 but I would rather not risk it. My budget is set and I want to get the most out of it. 


Have you heard any issue with an SSD in a Linux environment ? My thought was to set it op as the Boot, / & Swap leaving home one one of the others. 


Thanks again for the input. :)

---

### Post by Yellow Pasque on 2010-10-14
The SSD should give you a nice boost. I'm not really sure how much a quad-core CPU would help right now unless you do a lot of video encoding. You might be better off just getting the SSD and saving the rest for the next upgrade.

As for the additional storage, I wouldn't bother if I didn't need it. Mechanical hard disks just keep getting cheaper and better (less platters, less noise, more cache, etc.)

---

### Post by cascade9 on 2010-10-14
Good point Temüjin. They are also nice for gaming, and overall a better multitasking experience, but yeah......you might do better to just sit on the the CPU money for a while. CPUs (like HDDs) just get cheaper and cheaper. The X4 965 was, what, $200+? just a few months ago. 

> **jv2112 said:**
> Thanks for the useful insights. My board is a Revision 2 but I would rather not risk it. My budget is set and I want to get the most out of it. 

Have you heard any issue with an SSD in a Linux environment ? My thought was to set it op as the Boot, / & Swap leaving home one one of the others. 

Fair enough. My X2 550 unlocks to X4 perfectly, and its not that risky (as AMD improves the Phenom II manufacturing process, less and less CPUs have 'bad' cores). but understandable. 

I'm no expert on SSDs, but I dont think that swap is the best idea on a SSD.

---

### Post by jv2112 on 2010-10-16
Thank You for everyones input. I decided to go with ->


[http://www.microcenter.com/single_product_results.phtml?product_id=0344221]("http://www.microcenter.com/single_product_results.phtml?product_id=0344221")

:guitar:

I am going to play with this for a awhile and see if I want to invest more into a CPU. I also want to see if they come down a bit in price as I decided to invest a few more dollars into a better boot drive than I originally thought.


My next question would be to decide on OS install. I like LM 9 but thought about experimenting since I will need to reinstall anyway. 

I was thinking of another Debian based spin but some only come in 32 bit variations and I don't want a performance impact.
[SIZE="4"]
[SIZE="5"]Any thoughts ?[/SIZE][/SIZE]

_Debian Based (Where I have been spending my time)_	

	
    LM 9 Debian (32 Bit -Only Have)
    LM 9 Isadore(64 Bit-Current System)	
Dreamlinux (32 Bit - Only Have)
Ultimate 2.7 (64 Bit)
Debian (64 BIT)
[U]
New Territory [/U]-> Not Sure if I want to take the leap, still learning)

Slackware 
CentOS

---

### Post by Yellow Pasque on 2010-10-16
If you like KDE or xfce, then aptosid (formerly sidux) is awesome.

---

### Post by cascade9 on 2010-10-17
If you've never run debian, its probably the easiest way to get a bit more knowledge about how your system works, as debian wont be quite as easy as ubuntu/mint for some tasks. Having a go with debian also makes distros like slackware less challenging IMO. 

BTW, there is also mepis- 

[http://www.mepis.org/](http://www.mepis.org/)

> **Temüjin said:**
> If you like KDE or xfce, then aptosid (formerly sidux) is awesome.

+1 on 'awesome' (I'm been happily running sidux, now aptosid, for a while).Fluxbox is also a defualt window mananger for aptosid...not that there are huge numbers of fluxbox users. 

> KDE, XFCE and fluxbox are the aptosid defaults. Gnome is not supported by aptosid. Gnome as a window manager in sid repositories is known to be unstable and can cause issues at this point. Some users in the aptosid forums /wiki and IRC chat may have experience and be willing to help you, otherwise you are on your own.

[http://manual.aptosid.com/en/wel-quickstart-en.htm](http://manual.aptosid.com/en/wel-quickstart-en.htm)

---

### Post by jv2112 on 2010-10-17
Thanks for the feedback. 

Mepis looks nice and clean. I will download and check out a live CD. I have always hated KDE but this looks like KDE w/ a crew cut so it might work. 

Currently Testing Ultimate Edition 2.8. A little bloated but the bells and whistles are somewhat entertaining.

Seems like I could go bloated and trim/tweak or go slim and build to taste....... OPTIONS ARE GOOD :guitar:

---

