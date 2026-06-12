---
title: "Need help with Ubuntu and old laptop for a teen Streaming Video and World of Warcraft"
date: 2011-05-06
forum: Hardware
---

### Post by scampbell70 on 2011-05-06
I have two HP G60-125NR and they came with Vista installed. They are about 3 years old now and starting to run slow so I am passing them down to my children since I have bought two new laptops. 99% of the time they are on the laptop they are streaming music, watch videos or doing homework. They are also avid World of Warcraft players. With Vista they are unable to play WoW at all and it takes forever to do any word processing or watch a movie. 

I have installed several flavors of Ubuntu and was unable to get anything newer then 10.04 to recognize the network card which I see is common with this laptop. I am having some issues with 10.04 though. I can get WoW to play but it is choppy even at the lowest settings under Wine 1.03 does anyone have any advice to fix this or improve play? I know WoW never plays as good in Wine as in Windows but seeing as its unplayable in windows on this laptop anything is better then nothing. 

Also I am going to install a old copy of Windows xp that I have through virtualbox for when they want to stream netflix since there is not a way to do this natively. Any thoughts or suggestions about this?

**I am wondering if I go with an older version of Ubuntu like 7, 8, or 9 would that help improve speed or functionality at all on an older laptop**. I want to get the best results I can so that they can get at least a year or so of use out of them.

[CENTER][SIZE=4]**_Laptop SPECS_**
[/SIZE][/CENTER]

Processor 
[LIST]
[*] [SIZE=1]**Processor**  AMD Turion X2 mobile processor RM-70 / 2.0 GHz [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Multi-Core Technology**  Dual-Core [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**64-bit Computing**  Yes [/SIZE]
[/LIST]
[SIZE=1] [/SIZE]**[SIZE=1]Cache Memory[/SIZE]**

[SIZE=1] [/SIZE]
[LIST]
[*][SIZE=1] [/SIZE][SIZE=1]**Type**  L2 cache [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Installed Size**  1.0 MB [/SIZE]
[/LIST]
[SIZE=1] [/SIZE]**[SIZE=1]RAM[/SIZE]**

[SIZE=1] [/SIZE]
[LIST]
[*][SIZE=1] [/SIZE][SIZE=1]**Installed Size**  3.0 GB / 4.0 GB (max) [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Technology**  DDR2 SDRAM [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Form Factor**  SO DIMM 200-pin [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Configuration Features**  1 x 1 GB + 1 x 2 GB [/SIZE]
[/LIST]
[SIZE=1]Storage [/SIZE]
[LIST]
[*][SIZE=1] [/SIZE][SIZE=1]**Floppy Drive**  None [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Hard Drive**  250.0 GB - Serial ATA-150 - 5400.0 rpm [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Storage Removable**  None [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Hard drive type**  Portable [/SIZE]
[/LIST]
[SIZE=1] [/SIZE]**[SIZE=1]Optical Storage[/SIZE]**

[SIZE=1] [/SIZE]
[LIST]
[*][SIZE=1] [/SIZE][SIZE=1]**Type**  DVDï¿½RW (ï¿½R DL) / DVD-RAM [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Disc Labeling Technology**  LightScribe Technology [/SIZE]
[/LIST]
[SIZE=1]Display [/SIZE]
[LIST]
[*][SIZE=1] [/SIZE][SIZE=1]**Display Type**  15.6 in TFT active matrix [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Max Resolution**  1366 x 768 ( WXGA ) [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Widescreen Display**  Yes [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Features**  BrightView [/SIZE]
[/LIST]
[SIZE=1] [/SIZE]**[SIZE=1]Video[/SIZE]**

[SIZE=1] [/SIZE]
[LIST]
[*][SIZE=1] [/SIZE][SIZE=1]**Graphics Processor / Vendor**  NVIDIA GeForce 8200M G [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Total Available Graphics Memory**  1407.0 MB [/SIZE]
[/LIST]
[SIZE=1] [/SIZE]**[SIZE=1]Audio[/SIZE]**

[SIZE=1] [/SIZE]
[LIST]
[*][SIZE=1] [/SIZE][SIZE=1]**Audio Output**  Sound card [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Features**  Altec Lansing speakers [/SIZE]
[*][SIZE=1] [/SIZE][SIZE=1]**Audio Input**  Microphone [/SIZE]
[/LIST]

---

### Post by slooksterpsv on 2011-05-06
For WoW did you follow any steps like force using OpenGL and setting GL_ARB_vertex_buffer_object as a disabled OpenGL Extension in the registry?

See this guide here:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)


Also I VBOX Windows XP for Netflix. I would allocate 1GB of RAM (1024MB), I wouldn't install any antivirus or that, and even disable the graphical appearances, otherwise it'll be choppy at best. I find that gives the best performance. If it's still choppy, allocate both cores instead of one.

EDIT: I forgot, I wouldn't go with a lower version of Ubuntu. I'd use 10.04, try to stay with LTS. The older kernels I found with my systems, would drop the wireless and give me less performance. Also the Software Center was only introduced in 10.04, so if they need other Apps yeah.

EDIT 2 - Changed Wine to VBOX above.

---

### Post by scampbell70 on 2011-05-06
slooksterpsv 

I will try the WoW tweaks and let you know how it goes. Are you saying that you installed windows xp itself under wine? If so how did you get windows to install under wine and does it run better under wine then virtualbox or wmware player? I have an old copy of 98 I was going to try that and see if it would work better but I am worried that it wont see my hardware.

---

### Post by slooksterpsv on 2011-05-06
> **scampbell70 said:**
> slooksterpsv 

I will try the WoW tweaks and let you know how it goes. Are you saying that you installed windows xp itself under wine? If so how did you get windows to install under wine and does it run better under wine then virtualbox or wmware player? I have an old copy of 98 I was going to try that and see if it would work better but I am worried that it wont see my hardware.

OMG I totally fubared that one, I meant I vbox Windows XP (VirtualBox Virtualization software), the reason I put WINE is cause of WoW and I was installing WINE actually while replying to this yesterday haha. But not I use VirtualBox to run Windows XP under Ubuntu.

So sorry about the confusion.

---

