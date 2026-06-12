---
title: "TEMPERATURE on NVIDIA 9600gt"
date: 2009-10-10
forum: Hardware
---

### Post by katon on 2009-10-10
i think is not good 104 degrees in my GIGABYTE 9600gt SILENT card....its working well but it sounds like not real...fake

this is the info via NVCLOCK and a picture for you,

[I]root@mati-desktop:~# nvclock -i
-- General info --
Card: 		nVidia Geforce 9600GT
Architecture: 	G94 A1
PCI id: 	0x622
GPU clock: 	486.000 MHz
Bustype: 	PCI-Express

-- Shader info --
Clock: 1296.000 MHz
Stream units: 64 (1111b)
ROP units: 16 (1111b)
-- Memory info --
Amount: 	512 MB
Type: 		256 bit DDR3
Clock: 		756.000 MHz

-- PCI-Express info --
Current Rate: 	16X
Maximum rate: 	16X

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: 104C

-- VideoBios information --
Version: 62.94.11.00.03
Signon message: GV-NX96T512HP F1 
Performance level 0: gpu 450MHz/shader 1200MHz/memory 750MHz/0.00V/100%
Performance level 1: gpu 720MHz/shader 1800MHz/memory 1008MHz/0.00V/100%
VID mask: 3
Voltage level 0: 1.00V, VID: 0
Voltage level 1: 1.05V, VID: 1
Voltage level 2: 1.10V, VID: 2[/I]

---

### Post by katon on 2009-10-11
anyone ?

---

### Post by JHan816 on 2009-10-11
It looks like the program is reporting the temperature in Fahrenheit maybe a bug... 
 
My Nivdia (Evga) GTX 260 runs about 40C on my windows PC. I use a program called Precision which is a windows application to display the temperature and adjust the fan speed. My son's 9800gt runs about 40-45C normally.
 
Sorry I can't be of more help. I don't use my Nvidia card in my Linux computer.
 
--John

---

### Post by katon on 2009-10-11
Thank you, 
my card is gigabyte is GV-NX96T512HP F1 model
and DON"T have cooler is SILENT model.
It writes Celsius

---

### Post by antonkedrov on 2009-10-11
it's idle temperature? or you run something hard-graphical application like 3d-game?

---

### Post by katon on 2009-10-11
idle :(

---

### Post by antonkedrov on 2009-10-11
> **katon said:**
> idle :(

can you run top command to determine processes, which high use your cpu/gpu?
which nvidia drivers you use now? you can see it in nvidia-xserver-settings application

---

### Post by mivo on 2009-10-11
I'm not sure the program is working properly. If it was 104 degrees Celcius, I think it would have melted. :)

---

### Post by tuxxy on 2009-10-11
Even for farenheit thats a little hot hot heh Ideally that card should be idling at half those temps.  Whats your top processes maybe a game didnt shut down correctly and its causing the overheat.

---

### Post by katon on 2009-10-12
I understand what you say, first don;t forget mine is a SILENT MODEL , without ventilator (fan cooleR) ,
second when i touch it i can burn my hands is really hot , you almost can not touch it.
and finnaly im not playing games, is in idle

---

### Post by katon on 2009-10-12
> **antonkedrov said:**
> can you run top command to determine processes, which high use your cpu/gpu?
which nvidia drivers you use now? you can see it in nvidia-xserver-settings application

im using the newest driver 190.36

---

### Post by yossell on 2009-10-12
If you can almost not touch the card then those temps may be right. Graphics cards can reach such temperatures, but it's not at all healthy for them and that temperature is not good. You need to get it down. 

Does your computer have good air flow? I know the card is fanless, but those fanless designs normally require *some* airflow through the computer. Are the fans in the case working and is air being blown across the graphics card? If not, that could be part of the problem. 

Has the heatsink been properly seated? If there's not idea contact between the heatsink and the chip temperatures can get high. Might you have put too much thermal compound on? It may be worth taking it off, cleaning the old compound, and re-trying. In my current portable, there wasn't proper contact between the graphics chip and the heatsink, and my idling tempratures were 76c (with fan!), at load, 100+ then shut down. Simply cleaning, replacing thermal compound and reseating brought down idle temps to 54, load to 70.

Looking at
[http://www.quietpc.com/gb-en-gbp/products/vga-cards/gv-n98tsl-1gi](http://www.quietpc.com/gb-en-gbp/products/vga-cards/gv-n98tsl-1gi)

which is another fanless heatsink, the comments suggest their getting reasonable temperatures, 43-45 - which would, I think, be warm, but not too hot to the touch. 

yossell.

---

### Post by cascade9 on 2009-10-13
> **mivo said:**
> I'm not sure the program is working properly. If it was 104 degrees Celcius, I think it would have melted. :)

Nah. Depending on the chip model, nVidia tests them at over that- up to 127c IIRC. 

@ katon- I wouldnt be at all surpised if that is in F not C. My very similar 8600GT (silent cooler as well) tends to idle at 40-50C, depending on background temps, CPU use, etc. 105F = 40C so it would be fine. It shouldnt be that hot to touch though, at 45C my card ifeels warmer than body temp, but not hot. So maybe it is 105C. 

I would try yossells idea- take off the heatsink, clean it, put some heatsink paste on the heatsink, put it back on. 

You could also try using a desktop fan as a test. Just take the side panel off your case, point the fan into the case, turn it on, then check to see if the temp is dropping.

---

### Post by paul440 on 2009-11-26
Hi there, 
 
I have the same card and the same problem just started happening after 12 months. I dont use ubuntu but feel there are enough similarities to share and maybe help the original poster.
 
I've used this card for about a year without problem. Just recently I had many BSOD and noticed internal case temperature at about 60+ degrees (CPU still ok at around 40).
 
I tracked it down to this card sitting for several days at 95 degrees with compute idle. In the last two days it sits at 85 degrees all the time with computer doing nothing. These are very high temperatures for this card with not load. It never used to do this. I am about to try an alternate card. 
 
The theory that the heatsink may have separated from the GPU is a good one to investigate. I have not done that yet, but will have a look. 
 
Now that I see that OP is having same problem I'm starting to think its a hardware problem. 
 
I tried various drivers and booted XP and Vista, so I dont believe its an OS or driver problem. I think its either graphics card failure or possible MB is failing and causing graphics card to do crazy things and heat up.
 
Wonder if anybody else has similar problems or possible solution.
 
Paul,
 
> **katon said:**
> i think is not good 104 degrees in my GIGABYTE 9600gt SILENT card....its working well but it sounds like not real...fake
 
this is the info via NVCLOCK and a picture for you,
 
*root@mati-desktop:~# nvclock -i*
*-- General info --*
*Card:         nVidia Geforce 9600GT*
*Architecture:     G94 A1*
*PCI id:     0x622*
*GPU clock:     486.000 MHz*
*Bustype:     PCI-Express*
 
*-- Shader info --*
*Clock: 1296.000 MHz*
*Stream units: 64 (1111b)*
*ROP units: 16 (1111b)*
*-- Memory info --*
*Amount:     512 MB*
*Type:         256 bit DDR3*
*Clock:         756.000 MHz*
 
*-- PCI-Express info --*
*Current Rate:     16X*
*Maximum rate:     16X*
 
*-- Sensor info --*
*Sensor: GPU Internal Sensor*
*GPU temperature: 104C*
 
*-- VideoBios information --*
*Version: 62.94.11.00.03*
*Signon message: GV-NX96T512HP F1 *
*Performance level 0: gpu 450MHz/shader 1200MHz/memory 750MHz/0.00V/100%*
*Performance level 1: gpu 720MHz/shader 1800MHz/memory 1008MHz/0.00V/100%*
*VID mask: 3*
*Voltage level 0: 1.00V, VID: 0*
*Voltage level 1: 1.05V, VID: 1*
*Voltage level 2: 1.10V, VID: 2*

---

### Post by katon on 2009-11-27
i have changed the card by a similar new one ... i will try it tomorrow and tell you...

---

### Post by roharme on 2009-11-27
But nVidia Cabinet 3500
 
Around 7 fans surrounding the cabinet, with 2 big fans surround your Graphics card.

---

