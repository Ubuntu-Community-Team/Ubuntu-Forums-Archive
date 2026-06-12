---
title: "Video Card choice"
date: 2008-10-22
forum: Hardware
---

### Post by katon on 2008-10-22
Hi, sorry if i ask something that lot of people asked but i don;t find a thread with this stuff...

I'm buying computer , i don't want to spend all my money and wanted to know what do you recommend about the graphic card , 

i think to buy 

Processor Q6600 (quad core)  
Motherboard Intel DP35DP
4 gb Ram DDR2-800 mhz 
T220 Samsung LCD 22 inch (2 ms) 

I use all the time Ubuntu but thought to install Win XP on a small hardrive , i don't think i will play a lot  , just PRO evolution soccer or something like this NBA LIVE  on Windows XP boot.

So i want NVIDIA but....9800 family? or 8800 family? GT ? GTS ? GTX ? GTX+? 
or maybe i don;t need this high end stuff on linux ?    

thank you very much

---

### Post by katon on 2008-10-22
please??

---

### Post by pelle.k on 2008-10-22
No you don't need GPU horsepower for compiz and that stuff. I'd go for a gt8600, or maybe a ati hd3850 if you want an ATI card. The Nvidia will probably work best out of the box though.

I had a intel dp35dp mainboard a while ago (maybe you researched this and read my posts about it even?) - it was very nice for running ubuntu, but i honestly never got it to suspend sucessfully in any other distro actually.
Also, i had this problem with the CPU fan not starting up after resuming from suspend from time to time.
I would probably go for an asus p5k/p5e (or eqvivalent). Also check the ubuntu HCL for advice.

---

### Post by G-Dub on 2008-10-22
I am running a 9600gt, i love it, but i don't need it for linux. It's for far cry 2 on xp :D

---

### Post by katon on 2008-10-22
okey...understand...
didn;t read your threads but i will
about the 9600...i see that 8800 family is powerfull than 9600

is important if i use large pictures, or video HD , or just for games is the 9800 family?

---

### Post by pelle.k on 2008-10-22
You can forget about Purevide HD acceleration from Nvidia in linux. If that's what you want, ATI/Intel is your best bet. Intel only does IGP (integrated video cards) but they are underpowered for new games on windows.
Works great with linux though. (for the most part).

The 8600GT is dirt cheap, and more than enough, so i don't understand why you would go for a 8800 for compiz and some light gaming?
Also, the 8600GT doesn't get very hot, so it's quiet as well.

---

### Post by katon on 2008-10-23
> **G-Dub said:**
> I am running a 9600gt, i love it, but i don't need it for linux. It's for far cry 2 on xp :D

i see posts that 9600gt doesn;t work very well and driver doesn;t support HD use ..

---

### Post by katon on 2008-10-23
i really don;t know what to buy...is difficult to pick a card reading all the Ubuntu forums! :(

---

### Post by will_s54 on 2008-10-23
You will be going dual boot so I would suggest a good graphics card. From my current experience I would stay away from ATI cards for linux and go for an older Nvidia card. I have an older Nvidia 8800 in my 2nd computer and it gives me no problem in Ubuntu and yet can still play most games in XP or Visa at pretty high resolutions.

---

### Post by katon on 2008-10-23
okey...greats ,,and what about HD movies ? can you?

---

### Post by viper04649 on 2008-10-24
sorry to be a thread jacker. But i am having a similar debate. My desktop right now is running just the integrated Nvidia chip. It is ok, but really bogs down sometimes, and i haven't been able to get Ubuntu working on it. (only tried Feisty) So the issue that i have is that i only have a PC Powere & Cooling 310 watt ps. First, would a card like this: [EVGA 256-P2-N751-TR GeForce 8600 GT]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130085") be pretty easy to set up in Ubuntu? and would my PS be able to handle it. 

*i am running 2 sata HD's, an AuzenTech AZT-XPCINE sound card, and that is about it.

---

### Post by pelle.k on 2008-10-24
> okey...greats ,,and what about HD movies ? can you?
Sure you can. With that cpu, HD hardware acceleration is not an issue.

> First, would a card like this: EVGA 256-P2-N751-TR GeForce 8600 GT be pretty easy to set up in Ubuntu? and would my PS be able to handle it. 
I did run a c2d 8500 (it's not cunsuming much power though) + 1 sata hd + gf8600gt on my chieftech m-atx chassi with a 270 watt PSU. Of course it may have been a quality PSU, but anyway - i had no problems at all.
Hd:s do tend to eat a lot of power though.
Yeah, as i previously said, nvidia cards are pretty much OOTB in linux, unless it's the latest cutting edge stuff.

---

### Post by Crandom on 2008-10-24
Choose nvidia over ati. Ati's drivers are about 3x slower than on xp and come bundled with crashes and lack of hibernation/suspend support. After my experiences with ati, I won't buy with them again (unless they improve their drives :-x)

---

### Post by starcannon on 2008-10-24
Nvidia is easiest to set up. 6,7, and 8 series cards are all excellent. I don't know what to say about HD movies, I haven't been there done that yet on my computer. The 9 series cards will get there, about this time next year I predict the drivers for the 9 series to be nearing maturaty(same thing happened with previous "new" series cards from nVidia).

Anyway +1 for Nvidia.

---

### Post by pelle.k on 2008-11-16
> You can forget about Purevide HD acceleration from Nvidia in linux.
I need to ressurect this thread, and retract that statement i did above ^
As of nvidia driver 180.XX, nvidia will be adding purevideo support for 8x00 series and above; [http://www.phoronix.com/scan.php?page=article&item=nvidia_180_vdpau&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_180_vdpau&num=1)
Just thought you guys would like to hear that. It'll be included in the next release (jaunty jackalope), unless envy will be updated to include the 180.xx driver. But, it's only *beta* yet.

---

