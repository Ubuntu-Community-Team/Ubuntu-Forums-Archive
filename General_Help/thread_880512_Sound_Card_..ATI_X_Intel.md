---
title: "Sound Card ..ATI X Intel"
date: 2008-08-05
forum: General Help
---

### Post by Uchiha_madara on 2008-08-05
the soundcard worked before : but the sound was Like the Radio voice .....not Clear

When I re-installed Ubuntu Again .... there is no sound

I did a mass with three Components :
1 - the alsa-base file
> sudo nano /etc/modprobe.d/alsa-base
2 - Sound Options from Prefrences Menu
3 - the Volume Control in the Corner of the screen (with Devices)
4 - the Modules > sudo nano /etc/modules


In the Alsa base file : 
When I Typed in the Last Line :
> 
options snd-hda-intel index = 0 mpu_port=0x330

and rebooting the System well give the Beep Sound Only
but the Sound such as Music there is no Sound
But The System Will Give me This Message :
> there is no Sound card Defined

when I Type in the Alsa base file
> 
options snd-atiixp index=0


the System See The Devices and controlling the volume Degree But there is No Sound 

in The Volume Options and the Volume Control

I put the Drive is ATI HDA ALSA Drive
in Both

 -- I need to to ask how can I know the Correct Mpu_port =??
and The Guide Lines for that

 -- Please visit the Site [http://www.alsa-project.org](http://www.alsa-project.org)
then Choose the soundcards in the most Left of the screen
Choose ATI

 there is modules.conf what do this mean ??
 the Aliases ???? how can i reach this Files 
 and this Method of installation of the soundcard  is Legal in Ubuntu Hardy ??

Please help

---

### Post by Uchiha_madara on 2008-08-05
I need how can I Know The True value 

of the mpu_port of the sound ??

---

