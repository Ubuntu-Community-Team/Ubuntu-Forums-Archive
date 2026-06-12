---
title: "Ubuntu Feisty on Dell E1505"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by Amol_Karmarkar on 2007-04-28
Hello,

I am thinking of purchasing a Inspiron E1505  and intend to dual boot with Ubuntu 7.04 (feisty) and run Aero and Beryl. I want to minimize the tweaking I will need to do post installation and I hope everything will work out of the box since E1505 is shown as compatible with Ubuntu in the Ubuntu HCL ( [http://doc.gwos.org/index.php/DellLT](http://doc.gwos.org/index.php/DellLT) ). The configuration I am looking at is :

Inspiron E1505  	  Intel® Core™ 2 Duo T5600 (1.83GHz, 2MB L2 Cache, 667MHz FSB)
Operating System	Genuine Windows Vista™ Home Premium
LCD Panel 	             15.4 inch UltraSharp™ Wide Screen SXGA+ Display with TrueLife™
Memory 		             2GB Shared Dual Channel DDR2 SDRAM at 533MHZ, 2 DIMM
Video Card 	            256MB NVIDIA® GeForce® Go 7300 TurboCache*
Hard Drive 	            80GB 5400rpm SATA Hard Drive
Network Card	         Integrated 10/100 Network Card and Modem
DVD+RW Drive 	      8X CD/DVD Burner (DVD+/-RW) with double-layer DVD+R write capability
Sound Options 	        Integrated Audio
Wireless Networking  Dell Wireless 1390b/g (54Mbps)
Primary Battery 	53 WHr 6-cell Lithium Ion Primary Battery

I intend to use the laptop mostly for the usual stuff - word processors, spreadsheets, music, movies, browsing, photo editing, downloads etc and will  generally use Ubuntu though I might need to end up using Vista occasionally. I do not play computer games at all. I needed advise on my configuration and I want to optimize it considering that my budget is limited and I want the laptop to last for atleast 3 years.

1)  What processor must I choose ? Does Intel Core2 Duo T5600 ( 1.83 GHz ) offer significant performance improvements over Intel Core Duo T2350 (1.86 GHz) ?

2) What video card I must choose ? I am totally confused between Intel GMA 950 / ATI Radeon X1400/ NVidia GeForce Go 7300.  I would like some eye candy on my desktop and want to run Aero and Beryl. Is there a significant difference when watching movies / running "eye candy" stuff like Aero / Beryl between Intel GMA 950 and ATI / NVidia cards ? What video card drivers run best on Ubuntu ? Should I get a bigger hard drive plus a 9 cell 80 WHr battery by sacrificing the NVidia Video card ?

3) Shall I go for Dell Wireless 1390b/g or Intel PRO/Wireless 3945a/g ? I hear that people are facing issues with Dell Wireless card in Ubuntu. Which card is well supported in Ubuntu Feisty and will work out of the box ? Or do I need to resort to tricks ( like using ndiswrapper ) to make it work for both cards ?

Kindly advise.

Regards,
Amol

---

### Post by Syke on 2007-04-29
1. The Core2Duo is a nice boost in performance over the CoreDuo. The T5600 also has a higher Front Side Bus than the T2350, so that too will increase your performance.

2. The Intel video is good, and it's open source which is great. As much as I like Nvidia hardware, they don't open source their drivers.

3. The Intel 3945 is well supported in Feisty.

---

