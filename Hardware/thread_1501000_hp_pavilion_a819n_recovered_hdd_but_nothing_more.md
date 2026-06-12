---
title: "hp pavilion a819n recovered hdd but nothing more"
date: 2010-06-03
forum: Hardware
---

### Post by David-IT on 2010-06-03
hello everyone I had a custom build tower with a geforce6100 pm m2-v2.0 motherboard and it had a 6150se integrated graphics card etc.. well that pc crashed horribly from the power supply to the sound card completely fried :( not sure how this happened but I guess that is what happens when you leave your pc alone with hula-gins for a week lol. well I managed to save the HDD aka the only part of my computer that actually really had any value since I have a lot of important documents etc. well long story short I popped this HDD into my pavilion a819n old school tower and have gotten the Internet up even successful installed the old nvidia drivers I believe. but I cannot seem to get any restricted drivers for this integrated card that this tower has which is a integrated graphics media accelerator 900 with 128mb of shared video memory(this is what my tower says personally I have no clue what it has or how to check it). and I understand this is a cheap integrated card but I just would like not to lag while surfing web-pages :) etc... so I am just curious is there anyway that I can get ubuntu hardware drivers to detect my integrated card or if I can install it manually without having to reinstall ubuntu since i have no other hdd's to backup any of my data onto and i recently got laid off so I am trying to save money so I don't live on the street's :( I have tried google and searching your forums I could not find any other posts or help anywhere sadly :( so if anyone can help me I would greatly appreciate it thank you in advance David :)
oh and i found out alot of people were asking for the xorg.conf file while assisting others on 900 GMA so here is myne not sure if it will help 
==================================================
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
==================================================

well i reconfigured my xorg server but it says know i am using the versa driver and i cannot seem to get 1024x768 resolution working.. and if i am not mistaken isnt versa driver a older driver?

---

