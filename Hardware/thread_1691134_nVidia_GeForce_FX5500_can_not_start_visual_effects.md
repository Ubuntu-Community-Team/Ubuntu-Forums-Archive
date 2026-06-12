---
title: "nVidia GeForce FX5500 can not start visual effects&gt;extra"
date: 2011-02-19
forum: Hardware
---

### Post by Geezanansa on 2011-02-19
I have spent days trying to install/ configure my pc and ubuntu lucid lynx.  I do have a usable pc but quality of media playback is very poor ie choppy video poor sound quality poor.:(
I have sussessfully installed a lexmark x1270 all in one printer with success after reading in forums it can not be done.:P
I have not been able to fully install my nVidia geforce  fx5500 either through synaptic, appearances>visual effects>extra or by terminalcommand line.  There is loads of info available regarding this but as a newbie am overlooking something i feel.
So any body willing to help?


Loads of similar threads but a lot unanswered so please help.

Thanks in advance.

---

### Post by Geezanansa on 2011-02-19
I always find product forums a good reflection of product.

Not one suggestion?  No advice?   Loads of conflicting theories in these forums. several of which have proved unusable/useless.

I have even tried fresh install.  Graphics work on live cd but not after update/upgrade. 


:popcorn: here have some popcorn it might help with the bad taste in mouth.

I start using windows machine while i read ubuntu guide):P

---

### Post by cascade9 on 2011-02-20
Tried installing the video card drivers the easy way? 

system-> administration-> hardware drivers

---

### Post by Geezanansa on 2011-02-20
I have drivers 173 and 96 installed.  I have tried both as well as others.
I cannot access nVidia settings as it tells me x config needs reconfigured.
I can not activate either normal or extra options in Visual effects tab in appearances.
Any pointers?

---

### Post by cascade9 on 2011-02-21
How did you install the 173.xx drivers? 

You might do best to just remove all the nvidia stuff you have installed, then just use the easy way....

---

### Post by Geezanansa on 2011-02-21
Thanks for feedback
I have definatley tried the easy way.
I can have extra graphics applied when i run from live cd but run (extra graphics) on installed/ updated version-no chance?
I have spent much more time on this I am sure I can run this card with extra visual effects applied.  How on my ancient hardware setup?  I am slowly learning but it is a steep learning curve sifting through all the available info.   I have tried connecting monitor to on board grahics rather than agp but have no display at all then so struggle to select bios settings to start ubuntu cd or get to grub screen.
I have disabled all nvidaia drivers using hardware drivers then tried changing visual effects again but still no joy.  Going from what i have read i need to use terminal as root to input commands specific for drivers and do this without x config running?  It may allso be necessary to disable noveau and other graphic programmes/codecs?
Willing to shed some light?

---

### Post by cascade9 on 2011-02-22
Did you update before you used jockey (system-> admin...you know the drill). 

I know that there were some issues wit the 96.xx (GF2-4) and 173.xx (GF5/FX) drivers with jockey. From what is on the launchpad bug report, it should have been fixed with an update. 

If you have updated before you got the drivers (or if removing all the nvidia junk and then regetting the drivers doesnt work) then you might need to add a PPA and try again. 

Annoying, I know. :(

*edit- as far as jockey goes, you dont ned to drop out of the desktop, or do anything like that to get the drivers going, its just a reboot. Its only for manually installing video drivers you need to do that. 

Trying to use the onboard wont work if the nvidia driers are loaded (and will probably bork things if they are half-installed as well). Also, if trh card is installed that normally disables the onboard video as well, you would probably need to remove the card for the onbaord to work.....even if you dont have installed/semi-installed nvidia drivers.

---

### Post by Geezanansa on 2011-02-22
Thanks for pointing me in the right direction cascade9. 
I think you have hit the nail on the head regarding the updates.  I had not updated system BEFORE playing about with drivers and appearance settings.  Following your advice ubuntu is now running extra visual effects.  There was no need to add a PPA.  Easy peasy.
Thank you for your time,  patience and effort cascade9.  You are a :KS. Ubuntu land is a much nicer place now.

---

### Post by cascade9 on 2011-02-23
Thanks for your kind words, and I'm glad its all working well now ;)

---

### Post by theknightlinux on 2012-03-31
Geezanansa, could you please post a solution as to what you did? That would be really appreciated. I have the same problem with my GeForce FX5500 card. I can't seem to have any 3d or visual effects with any of the drivers (173 nor 96, or any post release updates). Can you please provide detailed instructions, as I am a noob to Linux (Ubuntu). I'm running Ubuntu 11.10, and I can only run Unity 2D. Thanks a lot.

---

