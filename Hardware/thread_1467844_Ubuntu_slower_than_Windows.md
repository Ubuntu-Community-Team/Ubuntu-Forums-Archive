---
title: "Ubuntu slower than Windows?"
date: 2010-05-01
forum: Hardware
---

### Post by burhangondal on 2010-05-01
Hello,

I am a decent user of Ubuntu and a big fan. I have always loved Ubuntu but recently, i got disappointed when i installed Ubuntu on my old laptop. Obviously, Ubuntu would run super fast on a brand new laptop i just bought but u can tell the real difference when it comes to old hardware and which OS runs it efficiently. I also have Windows 2000 and Windows XP with SP3 installed on the same laptop and they runs WAY better than Ubuntu. Faster, no slow down, and very smooth. My question is why Ubuntu runs slower on my laptop? Isn't Linux suppose to run faster on older hardware? and i m sure that my old Toshiba Laptop has more than enough specs to run ubuntu. Here the specs of my Toshiba Laptop from CPUz and GPUz. I have also tried Xbuntu but no luck and Kubuntu is out of the question. I would like some input what can i do to make it faster than Windows? i have done so many things but no luck.....

Toshiba A60 with Intel Celeron 2.8GHZ with 128k L2 cache (Single core)
1.5GB of DDR Ram
ATI 7000 IGP with 128MB of shared Video Memory
Realtek A97 Sound
80gb HD with 5200 RPM
And Chipset is from ATI too u can see in attache CPUz image

---

### Post by dino99 on 2010-05-01
you only have 1.5gb and not a big monster video card, so thats is, i suppose swap is heavily used :lolflag:

which ubuntu have you installed ? have you installed all the eyecandy kiddy stuff ?

if you want something smooth with your hardware, choose xfce desktop

---

### Post by burhangondal on 2010-05-01
I did use Xubuntu but it didn't really make any difference. Youtube videos are not watchable with Ubuntu or Xubuntu but Windows XP is running Smooth. I dont know whats wrong with ubuntu or Xubuntu. Probably they dont support these stuff anymore, that could be the reason.....but i think 1.5GB should be Plenty for ubuntu....as i never seen it using above 500MB anyways and i make only 600MB swap to prevent it  to swap out all the stuff....i think the problem is ATI 7000 IGP open source video drivers that makes it super slow, where on windows they r available fully optomized with ati cataylst...

---

### Post by dino99 on 2010-05-01
you need ubuntu-restricted-extras

---

### Post by acfreema on 2010-05-01
I would like to know what solution you find to this problem.  Because I will be doing Ubuntu installs on a couple of older hardware machines (Pentium M 1.6ghz and Turion 1.8ghz), it would save me some time and potential frustration to learn if I'd be better off using 6.06 or 7.04.

---

### Post by burhangondal on 2010-05-01
Dont install Ubuntu version 8.04 and up on any older hardware which i assume i m refering to the low end hardware of that time...for example, i have Desktop PC with Pentium 4 2.8GHZ with Hyperthreading with 1.5Gb of ram and i have just recently upgraded my video card from intel extreme shared shyti graphics to Nvidia 7300GT with 512Vram which helped ALOT to boost the performance and free up the load on my CPU. Ubuntu and even windows 7 runs very fast on it and its almost 7 years old desktop system i built from MSI....now my laptop is hopeless cuz i cant upgrade the video card on it to free the load on my cpu which is intel celeron 2.8GHZ (no HT) and also same ram as desktop 1.5GB and shared ATI 7000 igp graphics with 128MB share VRAM....Toshiba provides graphics and chipset drivers for windows 2000 and windows xp which has ati cataylst support but on LINUX, they have open source drivers which are DAM SLOW and make it worse for the CPU to DO ALL THE WORK....atleast in windows, drivers are optimized and they run fairley smooth....

NOW, FLASH PLAYER is everywhere and to run youtube on minimum quality on LINUX is not watchable, infact, it doesnt even run and laptop freezes but on windows it doesnt happen....THATS THE MAIN REASON i wont install linux on my laptop...

Point is...it depends if drivers are available and they r fully optimized for the system....i can run PUPPY LINUX on my laptop but it comes back to the same point that everywhere no matter wat distro linux has, got the same open source drivers for my graphics in my laptop so IT DEPENDS....ritenow....linux is a NO NO for my laptop but on desktop its runs super fast...again IT DEPENDS....search for drivers before you install....my laptop system specs are pretty decent but wat can we do wen ati dropped support for it...

oh and sorry for the god dam essay...

---

### Post by xflbret on 2010-05-04
This is disappointing to me, as well.

I have always wanted to use Ubuntu, but I can't. My lappy has the integrated Intel video which can't be upgraded, so I'm stuck with it. Trust me, I want to use Ubuntu long-term so badly that I would upgrade to a nvidia chip if it were possible. It's the Intel 915 shared chip.

Now, I understand much of the blame for this lies with Intel, or with Dell for putting it in. But come on...this is a common chip (unfortunately) and has been around for a while. No disrespect to anyone, but why in the world can't the Ubuntu folks make a driver for this that works well?

I'm not fond of giving Microsoft credit for anything, but their intel video drivers works well, no choppyness, and as a result of this better video driver, the battery lasts a hell of a lot longer. So, I'm still stuck with Windows, and will be stuck with Windows until the Ubuntu folks can make an intel driver that works.

In the M$ folks can write a good intel video driver, why can't the Unbuntu folks?

---

### Post by acfreema on 2010-05-16
> **burhangondal said:**
> Dont install Ubuntu version 8.04 and up on any older hardware
I have only run the live cd on my extra laptops, but 10.04 is superb.  These are two machines that each have 512mb RAM and a Turion 1.8ghz or a Pentium M 725 (1.6ghz).  I even used the live cd on my mom's home machine (Athlon XP 2600+ w/768mb RAM), and it's amazing.  

My only complaint is grub2 (from my 9.10 installation).

---

### Post by -Jeremy- on 2010-05-16
> **xflbret said:**
> 
In the M$ folks can write a good intel video driver, why can't the Unbuntu folks?


Neither Microsoft nor Canonical is responsible for making drivers for Intel chips or any other hardware for that matter. Intel makes drivers for Intel chips, Nvidia makes drivers for Nvidia chips etc. And sometimes a few good independent programmers make drivers as well but don't blame Canonical for not making drivers!

---

### Post by ronnielsen1 on 2010-05-16
I've had xubuntu run fast on certain computers and slow on others. LXDE has a much smaller footprint. You could try that

---

### Post by Vinddraken on 2010-05-16
> **-Jeremy- said:**
> Neither Microsoft nor Canonical is responsible for making drivers for Intel chips or any other hardware for that matter. Intel makes drivers for Intel chips, Nvidia makes drivers for Nvidia chips etc. And sometimes a few good independent programmers make drivers as well but don't blame Canonical for not making drivers!

As Jeremy pointed out, all the hardware manufacturers are very keen on keeping how their hardware works a secret. So mostly the drivers comes from them, the drivers that come in Linux is either thanks to the manufacturers sharing some of their source code or some fellow programmer has created one through trial and error until he has found a way to make it work in Linux.

It's sad that most hardware producers and also software either are happy that their products works just in Windows or they think to them self that anybody running Linux are that good in programming and the community is strong that they can figure out a workaround without have to spend any money or share any information.

I'm running Ubuntu on a HP tx 2000 tablet pc, it was released 2008 so hardware support is much much much better now and most works out of the box with newer versions of Ubuntu but there is still two buttons that doesn't work on the screen because nobody has figured out how they work and what signals they are sending to the motherboard.

Ps. Flash runs smooth on this computer :P

---

### Post by xflbret on 2010-05-16
> **-Jeremy- said:**
> Neither Microsoft nor Canonical is responsible for making drivers for Intel chips or any other hardware for that matter. Intel makes drivers for Intel chips, Nvidia makes drivers for Nvidia chips etc. And sometimes a few good independent programmers make drivers as well but don't blame Canonical for not making drivers!

This is a HUUUUUUGE part of the problem right there. It's not exclusive to Ubuntu or Canocial. The Linux-maker points the finger at the hardware manufacturer. The hardware manufacturer points the finger a the Linux-maker. In all this blame-placing, no one steps up to take responsibility, nothing ever gets done, and one of the world's most common video chips (unfortunately) doesn't get a decent driver written for it.

You know, here I am...I want to be initiated into the Linux cult and cast off the chains of the evil Microsoft monster. But, I can't because of this driver issue. I refuse to accept I'm the only one. There has to be thousands out there in my same situation. Wouldn't someone making a decent driver for this too-common chipset be worth the end-result of having a few thousand more folks drink the kool-aid?

---

### Post by mr clark25 on 2010-05-16
i dont get all of the "to slow" stuff!

i have an old pentium4 that runs at 1.3ghz with 512mb of rdram, and an nvidea geforce4 graphics card, and has 10.04 installed...

it does everything i need it to. it plays youtube videos with 4 other tabs open, and just about everything else.

---

### Post by jrusso2 on 2010-05-16
Intel drivers are open source so anyone of the thousands of eyes is welcome to fix it.

---

### Post by burhangondal on 2010-05-16
i think no one got the point...Point is, ubuntu runs decent....it opens up all website and i have no problem using anything....but the problem is with video driver....if it runs in windows why not ubuntu?....i cant even watch youtube video properly, infact, flash videos are so slow and laggy....i dont care about anything else...all i care about is that if youtube runs decent on 360P atleast then i m happy with ubuntu but it cant even run that and in windows youtube runs smooth....HECK, i install WINDOWS 7 with VGA drivers and it ran youtube better than UBUNTU open source video drivers.....i think thats the only thing ubuntu is lacking....not supporting old graphics card....the laptop i use is plenty for everything...i m not a gamer or hardcore photoshop addict but atleats it should run flash videos properly.....everything else is decent.....wit 1.5gb ram and 2.80ghz celeron cpu with 128k L2cache..i think it should be plenty for ubuntu....and in xfce or lxde, everything runs faster than ubuntu but same story with youtube....every distro uses the same open source driver so it doesnt really make sense to try any other distro...no matter u come from east or west u r gonna end up at the same spot...

---

### Post by Jart44 on 2010-05-17
You think no one got the point? Pardon.
I thought there was some insightful comments concerning your problem. This is a great  forum, yet your calling into question the Ubuntu community and the support network that took many years to develop. I run Lucid 10.04 on a dog tired IBM NetVista 1.6Mhz 512 Mb ram with a 2004 Nvidia GeForce 6600Gt video card. Most old laptops have more spit than my antique, yet this meager set-up is running Compiz Fusion at remarkable speed. I mean full Cube GUI on demand with strong animation properties. If you can't run this perhaps you need to do more research or stay with the proprietary monster Windows,

---

### Post by Keith1212 on 2010-05-17
i only have a gig of ram and integrated gfx in my dell and i play everything fine. even with all the eyecandy stuff on max.

Edit o and my laptop is hooked up to my dell 22" screen all the time so it has to output to 1080p all the time. Which I'm sure hits the cpu or gpu pretty good. Considering normally it just does the 1024x768.

---

### Post by cascade9 on 2010-05-17
> **burhangondal said:**
> i think no one got the point...Point is, ubuntu runs decent....it opens up all website and i have no problem using anything....but the problem is with video driver....if it runs in windows why not ubuntu?....

It runs in ubuntu as well...or else you wouldnt have any display at all. 

> **burhangondal said:**
> i cant even watch youtube video properly, infact, flash videos are so slow and laggy....i dont care about anything else...all i care about is that if youtube runs decent on 360P atleast then i m happy with ubuntu but it cant even run that and in windows youtube runs smooth....HECK, i install WINDOWS 7 with VGA drivers and it ran youtube better than UBUNTU open source video drivers.....

Linux flash is never as good as the versions made for microsoft. Blame adobe for that. 

> **burhangondal said:**
> i think thats the only thing ubuntu is lacking....not supporting old graphics card....the laptop i use is plenty for everything...i m not a gamer or hardcore photoshop addict but atleats it should run flash videos properly.....everything else is decent.....wit 1.5gb ram and 2.80ghz celeron cpu with 128k L2cache..i think it should be plenty for ubuntu....and in xfce or lxde, everything runs faster than ubuntu but same story with youtube....

Same story in youtube? Proves its flash, not anything to do with system speed. 

> **burhangondal said:**
> every distro uses the same open source driver so it doesnt really make sense to try any other distro...no matter u come from east or west u r gonna end up at the same spot...

Well, actually, no. While all the distros tend to use the same drivers, they can be very different in what version they are using. That can make a major difference to how well they run, etc.. 

If you are using an ATI 7000, it would have to be using the free opensource ATI drivers. Ubuntu is probably a fair way behind some of the more 'cutting edge' distros as far as the ATI opensoruce drivers go (eg Arch, Debian Sid). 

> **burhangondal said:**
> Dont install Ubuntu version 8.04 and up on any older hardware which i assume i m refering to the low end hardware of that time....

Insane advice. 8.04 is the last (desktop) version to recive support, updates, etc. 8.04 is the earliest version anyone should be running if the computer is hooked up to the internet IMO. 

> **burhangondal said:**
> I am a decent user of Ubuntu and a big fan. I have always loved Ubuntu but recently, i got disappointed when i installed Ubuntu on my old laptop. Obviously, Ubuntu would run super fast on a brand new laptop i just bought but u can tell the real difference when it comes to old hardware and which OS runs it efficiently. I also have Windows 2000 and Windows XP with SP3 installed on the same laptop and they runs WAY better than Ubuntu. Faster, no slow down, and very smooth. My question is why Ubuntu runs slower on my laptop? Isn't Linux suppose to run faster on older hardware? 

 I would like some input what can i do to make it faster than Windows? 

Wel, from everything else you have posted, I dont think that its quite a slow as this post implies.

Linux isnt always 'faster on older hardware'- some distros are faster than others, and some of them are very slow. 

If you do want to have a faster ubuntu, and one that should be faster than Win2K/WinXP, try a minimal install (either using gnome, or better yet, xfce or lxde)

---

### Post by mastablasta on 2010-05-17
OK i did and plan to still do a couple of instalations on old computers. So first off i would like to say that *fast* is a very relative term and doesn't say anything about the speed. 
 
Second i've installed on the following maschine and everyhting works very well. Onyl when running a bit more applicaitons at the same time it might get a bit sluggish (but so did win XP):
 
AMD 833 Mhz (it seems the mobo is blocking it to get highee frequency from it)
1.3 MB ram (1GB + 256 MB)
30 GB disk for Ubuntu
And old 16 MB Rage ATI graphics card (didn't install any drivers, just using how it came with Linux)
 
All special desktop effects are off. 
 
 
I also tried Live CD Ubuntu 9.10 (was carshing as well as Xubuntu -reason unknown) and Lubuntu 10.04 (works really well and will probably be installed unless Mint9 LXDE gives a better offer when released) on the following laptop:
 
AMD 1.2 Ghz
256 MB RAM
16 MB S3 built in graphics card (i think the memorry is scalled down to 8 MB but i am unsure)
16 GB HDD (not really used since it runs form live CD)
 
So you guys must have done something wrong in instalation by installing a bad driver, using some system resources hogs or simply the driver for the card is a bad one. Point is 512 MB, 1+ Ghz processor enough hard disk space and descent card should run the system fine.

---

### Post by Geffers on 2010-05-17
> **xflbret said:**
> This is disappointing to me, as well.

I have always wanted to use Ubuntu, but I can't. My lappy has the integrated Intel video which can't be upgraded, so I'm stuck with it. Trust me, I want to use Ubuntu long-term so badly that I would upgrade to a nvidia chip if it were possible. It's the Intel 915 shared chip.



Dual boot seems to be the answer, any video work use Windows, any other boot in to Ubuntu.

I have an old AMD 900mhz desktop running Hardy Heron, video is dodgy but for the use I put this particular machine to it is fine.

Video on my Acer Netbook with Intel Atom (not the fastest in the world) is fine.

Problem is Linux has to keep up to date to match Windows, that means use memory

Geffers

---

