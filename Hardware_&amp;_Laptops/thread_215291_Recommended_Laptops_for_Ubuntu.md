---
title: "Recommended Laptops for Ubuntu"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by eqisow on 2006-07-13
I am looking for a new laptop to run Ubuntu on. The three must-have requirements are complete Ubuntu compatibility, a < $1000 price, and competative pricing when compared to Dell and other major retailers. Also, I would like to avoid the Windows tax if at all possible. Either Linux pre-install or no OS is fine.

Other preferences that are not quite as important include having an AMD processor, Nvidia graphics chipset, and a widescreen display. Speed is not a major concern, but 512 MB of RAM and a HD > 40 GB would be nice.

Normally I wouldn't come to a forum for shopping advice, but I just can't seem to find anything that really meets these requirements.

---

### Post by didobuntu on 2006-07-13
Hello, 

I personally have an Asus W2JC laptop ... which cost much more than 1000$

The laptop that I can recommend you is the Lenovo 3000 N100 ... It is a core duo processor, with 1Gb Ram (667MHz), beautiful WSXGA screen (1680X1050) .. and an nvidia video card ... Look and compare with, for instance, Dell.

Good luck

---

### Post by constitutionrules on 2006-07-14
"The laptop that I can recommend you is the Lenovo 3000 N100 ... It is a core duo processor, with 1Gb Ram (667MHz), beautiful WSXGA screen (1680X1050) .. and an nvidia video card ... Look and compare with, for instance, Dell."

I am also looking for a new laptop, do you know if the Lenovo/Ubuntu works wireless? As my now Dead Dell 5150 would not work wireless, no matter what I did.. Also, I am looking at an 	Acer TravelMate 8104WLMi w/ 802.11a/b/g Wireless LAN Card.. do you know of any wireless problems I may have with this L/T. The other one I am looking at is a DELL INSPIRON 9300 with an 2915 PRO Wireless Card. Any thoughts on this one?

Thanks for any help... CR

---

### Post by K.Mandla on 2006-07-14
I had an M170 with an Intel PRO/Wireless 2200BG and it worked fantastic. Since Dell has dropped those machines for the dual core laptops, you might be able to pick one up at discount. Might still be more than you're willing to pay, though.

Otherwise, I'd suggest an Inspiron 600m with a MiniPCI 1370, which works with ndiswrapper. I also have Dapper on Inspiron 8000/8100 machines, but in that case, the wireless will depend on the PCMCIA you buy. :D

---

### Post by hugo.lovhoiden on 2006-07-14
> **constitutionrules said:**
> .. Also, I am looking at an 	Acer TravelMate 8104WLMi w/ 802.11a/b/g Wireless LAN Card.. do you know of any wireless problems I may have with this L/T.

Ubuntu works well on Travelmate 8104WLMi. You can even make Xgl/compiz work using fglrx driver, although suspend/resume works most reliably using the stock xorg ATI driver. Wireless just worked, at least for me. The only customization I had to do was to add LED=1 as an option to module ipw2200. The radion on/off button works regardless, but it is nice to get visual feedback.

I created a new file "ipw2200" (can have any name) in /etc/modprobe.d an added "options ipw2200 led=1" to it.

I don't know the other laptops you asked about...

- Hugo

---

### Post by rajeshrs on 2006-07-14
I have a Lenovo 3000 N-100 laptop which I bought a month back, and I would like to install Ubuntu on it. I don't have any problems with installing linux (have done it before on PCs), but I had a query related to the warranty issues.

There is only one partition on the hard drive. There is a backup partition on the hard drive with Windows XP and the software which comes bundled with the machine. I am interested in keeping this drive. I obviously would have had the good sense of creating 2 partitions but that wasn't the case when the machine was shipped to me. I didnt change the partition space since I wanted to do minimal changes to the system. As it turns out I have plenty of free disk space and I would like to allocate maybe 7-8 GB of space to linux and all the files associated.

Trouble is, I do not know if I can modify the partition table and still retain my warranty. Please let me know if you guys have any idea about how I can retain the warranty, the back up partition, as well as install Ubuntu on my system.

Thanks and Regards
Rajesh R S
India

---

### Post by philippe_carlo on 2006-07-14
Not a ver y cheap solution, but one that works for sure: either install linux on a separate hardrive, or buy another hard drive and keep the original aside in case you run in warranty-problems.

---

### Post by didobuntu on 2006-07-14
If you create a disk partition to install Ubuntu that won't shout down your waranty because you use a free space and keep Win$ unchanged ...

Moreover, since I bought my computers, I never had to return my laptops for software problems. Linux is now more and more safe. 
Try the UbuntuLive CD and see how this runs ... I am sure its wonderful .. then create new partitions to install the system ... just be carefull of what you do when you select the partitions you formate to install the root system, the /home and the swap .... minmum 15 Go its ok .. I personally have 40 Go (of 100 Go of my hard drive) for Ubuntu ... Because it's worth it .. LOL

---

### Post by constitutionrules on 2006-07-15
> Ubuntu works well on Travelmate 8104WLMi. You can even make Xgl/compiz work using fglrx driver, although suspend/resume works most reliably using the stock xorg ATI driver. Wireless just worked, at least for me. The only customization I had to do was to add LED=1 as an option to module ipw2200. The radion on/off button works regardless, but it is nice to get visual feedback.

I created a new file "ipw2200" (can have any name) in /etc/modprobe.d an added "options ipw2200 led=1" to it.

I don't know the other laptops you asked about...

- Hugo
Reply With Quote

I won the Acer off of ebay.. Hope to get it in the next cpl days, I'll post what I find with it, and the duel-boot of Pro/Ubuntu

---

### Post by didobuntu on 2006-07-15
Now with the latest core duo processors the ipw3945 runs perfectly and ubuntu install the necessary drivers without creating any additional file

---

### Post by chichilalescu on 2006-07-17
I have a cheap laptop that works great for me.
It's a Prestigio Nobile 150, and I suppose if you want more performance (like the wide screen), you could get a better model of Prestigio Nobile --- the thing is I think ubuntu would work just as great as it does on my model (all works great from first install), but Prestigio Nobile has Pentium processors (I noticed that you said something about AMD).
I haven't tested if wireless works, since I didn't buy a wireless card yet, but besides that everything seems to be working fine, including all ACPI functions (it did get weird on me a couple of times, rebooting without unmounting the hard drive, and other stuff like that, but I guess it was mostly my fault).
The only problem that I do have is that when I connect an external monitor and turn off the LCD on the laptop, the external monitor switches off too, but again, I didn't investigate this very thoroughly.
Anyway, if you want an affordable notebook that should run well under linux, you should search for an older model --- these days an older model is enough for mostly anything but games or real computing (simulations and stuff like that).

---

