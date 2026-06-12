---
title: "Max video card 240w PSU can support?"
date: 2019-05-12
forum: Hardware
---

### Post by Tadaen_Sylvermane on 2019-05-12
I have and use daily a Dell Optiplex 3010. It has an Ivy Bridge i5 3470 in it. It's a custom case with a custom psu, designed for office stuff. Not gaming or anything. I recently put 8 gigs of ram in it to replace the 4 it had, and am now looking at a video card. It has a PCIx16 slot and 7 inches of space, but the psu is the issue at only 240watts. It was given to us as the ati video card didn't work, they thought the whole machine was busted. We play Minecraft at most on this machine and it runs well off the integrated but I figured why not try to max it out as best I can.

Any ideas on the top video card I can use without overloading? And would that video card be worth it at all compared to the existing integrated gpu on the i5? I'm not worried about Linux compatibility at the moment, just best I can get. Would need to be low profile.

---

### Post by him610 on 2019-05-12
Here is a link to a discussion at the Dell Community website about your particular Dell model and the possibility of graphics card upgrade, [https://www.dell.com/community/Desktops-General-Read-Only/Help-With-Video-Card-for-my-optiplex-3010/td-p/4306528]("https://www.dell.com/community/Desktops-General-Read-Only/Help-With-Video-Card-for-my-optiplex-3010/td-p/4306528")

---

### Post by Autodave on 2019-05-12
Have you considered spending about $40 (US) and buying a new power supply?  If the case for this PC takes a standard PSU, they are inexpensive and easy to replace.

---

### Post by mastablasta on 2019-05-13
> **Tadaen_Sylvermane said:**
> I have and use daily a Dell Optiplex 3010. It has an Ivy Bridge i5 3470 in it. It's a custom case with a custom psu, designed for office stuff. Not gaming or anything. I recently put 8 gigs of ram in it to replace the 4 it had, and am now looking at a video card. It has a PCIx16 slot and 7 inches of space, but the psu is the issue at only 240watts. It was given to us as the ati video card didn't work, they thought the whole machine was busted. We play Minecraft at most on this machine and it runs well off the integrated but I figured why not try to max it out as best I can.

Any ideas on the top video card I can use without overloading? And would that video card be worth it at all compared to the existing integrated gpu on the i5? I'm not worried about Linux compatibility at the moment, just best I can get. Would need to be low profile.


low profile usually don't offer that much (in terms of computing power) and the 3rd Gen Intel had descent GPU chips. the PSU is definitelly a bit low. would be good to have at least 350 W. i use GT 730 normal size - it needs about 25W. and it's ok for old games and for the card it replaced on this old box. but if you check some of the low profile ones you will notice that they have somewhat similar specs to your chip.

however there are a few with much better specs, but i am not sure what their power usage is: [https://graphicscardhub.com/best-low-profile-graphics-card/](https://graphicscardhub.com/best-low-profile-graphics-card/) 
maybe investigate GT 1030. or more powerful if you have the money. and change the PSU. 

so you want to max it out - what do you plan on doing on it when it's maxed out? that is the question. play some newer games - you would need better PSU and stronger GPU.

---

### Post by Tadaen_Sylvermane on 2019-05-13
It isn't a normal atx psu. It's long and thin. Here is a picture.

[https://www.google.com/search?q=optiplex+3010&oq=optiplex+3010&aqs=chrome..69i57j69i60j69i59j69i60.2761j0j7&client=ubuntu&sourceid=chrome&ie=UTF-8](https://www.google.com/search?q=optiplex+3010&oq=optiplex+3010&aqs=chrome..69i57j69i60j69i59j69i60.2761j0j7&client=ubuntu&sourceid=chrome&ie=UTF-8)

PSU

[https://www.newegg.com/Product/Product.aspx?Item=9SIAH9B99S5930&Description=dell%20optiplex%203010%20psu&cm_re=dell_optiplex_3010_psu-_-9SIAH9B99S5930-_-Product](https://www.newegg.com/Product/Product.aspx?Item=9SIAH9B99S5930&Description=dell%20optiplex%203010%20psu&cm_re=dell_optiplex_3010_psu-_-9SIAH9B99S5930-_-Product)

The case isn't really designed to add much to it hence the issue.

Ultimately it isn't a big deal, just figured if I could add something halfway decent I might do it. If not, no big worry. I was kind of hoping I could make it a stealth gaming machine. I will be changing to an SSD as well, and all we do with it is Minecraft and general home office stuff. It might be good for some emulators though. It runs Minecraft quite well at 40-50fps when ramdisked.

---

### Post by mastablasta on 2019-05-14
well that's good to know. i don't think i will be buying any small factor types for home use.

[https://www.dell.com/downloads/global/products/optix/en/optiplex_3010_technical_guidebook.pdf](https://www.dell.com/downloads/global/products/optix/en/optiplex_3010_technical_guidebook.pdf)

looks like some people went with lower powered GPU (check the power output).

Apparently [COLOR=#272A34][FONT=&quot]Mini ITX PSU doesn't exactly fit, though you might want to look arround and see if you can find something. there is also plenty of people with same question to yours on the internet. for example: 
[/FONT][/COLOR][https://forums.tomshardware.com/threads/dell-optiplex-390-sff-gpu-vs-240w.3340015/](https://forums.tomshardware.com/threads/dell-optiplex-390-sff-gpu-vs-240w.3340015/)

final solution is also to replace the casing and PSU :-). maybe get a used, larger one.

yes, the i5 3rd gen GPU is descent enough to run some older games. probably even some new ones. i was thinking of getting a refurbished PC for my son. actually he is saving money slowly, but will need a bit of help to get his first PC. found some nice ones, but then the price is not that much different here to new Ryzen when you do some benchmark comparison. i wish i could get some here from work, but they throw them all away and not sell them. weird.

---

### Post by him610 on 2019-05-14
It appears to be similar to a FlexATX PSU. This is from information I have gathered over the years....
```
PSU dimensions			
PSU Standard	Width(in)	Height(in)	Depth(in)
ATX large	5.91	3.39	7.09
ATX – EPS	5.91	3.39	9.06
ATX  PS2	5.91	3.35	5.91
ATX12V / BTX	5.91	3.39	5.51
CFX12V	        5.91	3.39	3.78
[COLOR="#FF0000"]FlexATX	        3.21	1.59	5.91[/COLOR]
LFX12V	        2.44	2.83	8.27
SFX12V	        4.92	2.5	3.94
TFX12V	        3.35	2.52	6.89
```
```

PSU Standard	Width(mm)	Height(mm)	Depth(mm)
ATX large	150	86	180
ATX – EPS	150	86	230
ATX  PS2	150	85	150
ATX12V / BTX	150	86	140
CFX12V	        150	86	96
FlexATX	        81.5	40.5	150
LFX12V	        62	72	210
SFX12V	        125	63.5	100
TFX12V	        85	64	175
```
I replaced a 250W FlexATX with a 300W FlexATX in a Shuttle (SFF) several years ago.

---

