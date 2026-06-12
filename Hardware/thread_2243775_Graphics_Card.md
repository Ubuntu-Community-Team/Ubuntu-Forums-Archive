---
title: "Graphics Card"
date: 2014-09-11
forum: Hardware
---

### Post by 3dmatrix on 2014-09-11
I have an old computer on which I am trying Xubuntu 14.04.
It has an Intel inbuilt graphics card. But the graphics performance of that computer is very bad.
I wish to add a good but inexpensive graphics card in that computer that is well supported by Ubuntu 14.04 and is easily available at the same time.
Kindly advise some popular graphics cards.

---

### Post by slickymaster on 2014-09-11
*Moved to the ***Hardware*** sub-forum.*

---

### Post by Yellow Pasque on 2014-09-11
First, you need to make sure what slot your motherboard has. Do you have a PCI-E slot or AGP? If you're unsure, use dmidecode to tell us what motherboard you have:
```
sudo dmidecode -t baseboard
```

You might also tell us what budget you have and what applications/games you're looking to run.

---

### Post by 3dmatrix on 2014-09-13
> **Temüjin said:**
> First, you need to make sure what slot your motherboard has. Do you have a PCI-E slot or AGP? If you're unsure, use dmidecode to tell us what motherboard you have:
```
sudo dmidecode -t baseboard
```

You might also tell us what budget you have and what applications/games you're looking to run.

[B]dmidecode 2.12
SMBIOS 2.3 present.

Handle 0x0200, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Dell Inc.          
	Product Name: 0J8885
	Version:    
	Serial Number: ..CN6986157S0CC7.

Handle 0x0A00, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: Intel Graphics Media Accelerator 950

Handle 0x0A02, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: Intel PRO/100 VE Network Connections

Handle 0x0A03, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description: High Definition Audio Controller
[/B]

I do not wish to play any very high end graphics game. May be just Steam's Team Fortress 2 will be enough. My main reason to buy that card is that computer's extremely poor performance when it comes to playing online videos. The movement is very jerky and at times the video simply stops where as the sound keeps playing.
Do you think we can get anything suitable in $15-20 catagory ?

.

---

### Post by Yellow Pasque on 2014-09-13
It looks like you have a PCI-Ex16 expansion slot, so that's good news: [http://mxdtr.com/dell-0j8885-motherboard-specs-0j8885/](http://mxdtr.com/dell-0j8885-motherboard-specs-0j8885/)

$15-20 is a very limited budget. You may be able to find a used Nvidia GT430/440 or a Radeon 5450 for that price.

---

### Post by 3dmatrix on 2014-09-18
> **Temüjin said:**
> It looks like you have a PCI-Ex16 expansion slot, so that's good news: [http://mxdtr.com/dell-0j8885-motherboard-specs-0j8885/](http://mxdtr.com/dell-0j8885-motherboard-specs-0j8885/)

$15-20 is a very limited budget. You may be able to find a used Nvidia GT430/440 or a Radeon 5450 for that price.

I remember I saw that card in some shops in that price. But have to recheck.

[LIST]
[*]Seems that card does not have a VGA output. In case I wish to use a VGA monitor then what should I do ?
[*]Will using a good graphics card solve the choppy streaming video problem ?
[/LIST]
[LIST]
[*]I also find **Blender** rendering time to be very long. For that, is using a better graphics card enough, or do I need to increase the RAM also ?
[/LIST]

---

