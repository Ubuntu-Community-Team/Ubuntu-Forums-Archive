---
title: "Can't enable desktop effects and need some help."
date: 2010-02-13
forum: Hardware
---

### Post by Theoutdoorsman on 2010-02-13
If anyone can help me out, i sure would appreciate any advice. I cannot enable desktop effects. I'm very new to the Linux community and don't have a clue where to begin. It seems that all my hardware is functioning properly, except my video. I'm assuming I probably need to install drivers to correct my problem, but I'm not really certain how to do so. I can obtain any relevant information needed to assist in the troubleshooting. I'll list some basics to give you an idea what I'm working with. Thanks to anyone who is willing to help......


lspci, from the terminal,  returns the following information regarding the onboard vga controller:

[I][B]01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01) 
[/B][/I] 

Please assume I know nothing about linux commands when assisting. I have limited knowledge of the OS, but do have some experience, although it isn't much. Thanks again.

I almost forgot, I am running Ubuntu 9.10. In the terminal, "uname -r" returns:

[B]2.6.31-19-generic

desktop:~$ glxinfo | grep direct
direct rendering: Yes

desktop:~$ glxgears
2371 frames in 5.0 seconds
2448 frames in 5.0 seconds
2468 frames in 5.0 seconds
2445 frames in 5.0 seconds

[/B]

---

### Post by Luisnux on 2010-02-13
First you will need to install the drivers.  To do that go to System-->Administration-->Hardware Drivers.  That should recognize the graphics card that you have, and then after it's detected you will have to enable them by selecting the detected drivers and clicking enable.  The system will prompt you to restart, and once you've done that you can finally right click on your desktop, then go to change desktop background, and then click on Effects, and select extra.  If your video card does not have enough memory, then it will not let you select that one.  However if your card has more than 64MB of Ram then it should be able to use it.  After that's done most of the work is done.  However to further configure the effects, such as the "cube", "expo", "fire/water effect" and all of those fancy features that windows only dreams of, then you will have to install "Simple-ccsm".  To do that head to System-->Synaptic package manager, and type "simple-ccsm" (without the quotes :)), and the click enter.  Once it's found you'll be able to install it and it should install another program that will let you do all kind of crazy things, that will make you the envy of the computer world.  Once you've installed simple-ccsm you may want to install "compiz" which by the way should have already been installed by default on Karmic (or at least I think it should have LOL).  After that you can go to System-->Preferences-->Simple compiz settings manager or compiz settings manager and have fun making some of the coolest changes to your system.  I would give you more detail on all of those effects but we'll leave that for another day.  Hope this helps.

---

### Post by Theoutdoorsman on 2010-02-13
System-->Administration-->Hardware Drivers yields "no proprietary drives being used on this system".

I have already installed the "Simple-ccsm" via the package manager. When I try to enable the effects via "extra" or "custom", it informs me that its looking for drivers, then tells me that it can't enable desktop effects. Any other thoughts? Thanks.

---

### Post by Yellow Pasque on 2010-02-13
> Any other thoughts?
It's not going to work with your video chipset.

---

### Post by Luisnux on 2010-02-13
What video card do you have?  If you can give the name of your laptop/pc or the name of the graphics card we might be able to give you more info.  For example do you have a "nvidia 8500gt", "nti hd4890", etc.

---

### Post by Yellow Pasque on 2010-02-13
Look at the OP; the video card is a VIA/S3 Unichrome.

---

### Post by Thomas Garman on 2010-02-13
You can go buy an pretty cheap ($70-$100) nVidia card that will fit in one of your pci slots.  When you put that in then the the system will detect it and give you the option of installing drivers...  at which point you will be able to enable the desktop effects.

Not really worth the effort, though, just for the effects... so you might consider how fun it would be to have TWO monitors, which you could do with a video card in one of your pci slots.

---

### Post by Theoutdoorsman on 2010-02-13
> **Temüjin said:**
> It's not going to work with your video chipset.


What makes you say that it won't work? Am I missing something?

---

### Post by ssulaco on 2010-02-13
Depending on how old the computer is,you will need to determine if you need pci express,agp,etc...depending if you just want to get desktop effects working or you need a high end card,I believe this was the one I bought and effects work great..note,its an AGP,you have to figure out what you need.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130014](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130014)

---

### Post by ssulaco on 2010-02-13
> **Theoutdoorsman said:**
> What makes you say that it won't work? Am I missing something?
Onboard Chipset is not going to power Desktop effects,you will need a Graphics card

---

### Post by Yellow Pasque on 2010-02-13
> **Theoutdoorsman said:**
> What makes you say that it won't work? Am I missing something?
Yes, you need a video card and driver that offers certain features for Compiz to work. Your hardware could be capable, but Via's Linux drivers are very limited.

> Onboard Chipset is not going to power Desktop effects,you will need a Graphics card
Plenty of IGP's can power Compiz (but this isn't one of them).

---

### Post by Theoutdoorsman on 2010-02-14
What a bummer!!! It seems that every time I attempt to divert AWAY from Micro$oft, I wind up right back with them. I struggle with one hardware related issue after another, when it comes to Linux. I don't think I have ever owned a system that was FULLY supported. I really like the look and feel of things in Linux, but troubleshooting hardware related problems gets old in a hurry. On the other hand, a $40 video card sounds much better than $150 OS, let alone the cost of additional software programs. I suppose, since my only gripe with Linux is with hardware issues, I need to focus more on troubleshooting hardware. If anyone can point me to some helpful documentation, geared toward the beginner to test and troubleshoot these, it would be a blessing. The way I see it, if others can devote their time and energy into creating software that is free, I should do MY part in learning how to make use of it! Looks like I need to hit the books! Just knowing where to begin would be a major plus for me. Would anyone care to offer up some recommended reads? Thank you, so much, for all your help.

---

### Post by Theoutdoorsman on 2010-02-14
> **ssulaco said:**
> Depending on how old the computer is,you will need to determine if you need pci express,agp,etc...depending if you just want to get desktop effects working or you need a high end card,I believe this was the one I bought and effects work great..note,its an AGP,you have to figure out what you need.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130014](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130014)



Can you confirm this card will work right out of the box, or otherwise have drivers readily available? I do have an AGP 4X/8X expansion slot available. Thanks!

---

### Post by Yellow Pasque on 2010-02-14
I may have someone trying to sell an AGP GeForce 6600, which would be preferable to that card for a few reasons (it's flat-out faster and it supports OpenGL 2.1). Where are you located?

---

### Post by ssulaco on 2010-02-14
> **Theoutdoorsman said:**
> Can you confirm this card will work right out of the box, or otherwise have drivers readily available? I do have an AGP 4X/8X expansion slot available. Thanks!
I have an older Dell Optiplex,that just had integrated video,but it wasnt enough for compiz,yes,it was an EVGA,256mb,AGP 8X,Geforce 6200,and it worked right out of the box....Ubuntu picked it right up and installed the necessary drivers.
I cant exactly say if the link I provided is the exact same one,
you might want more horsepower but I wouldnt go any less,look at the reviews,you dont have to use EVGA,but I've had good luck with it,I would stick with Nvidia chipset.

---

### Post by Theoutdoorsman on 2010-02-15
> **Temüjin said:**
> I may have someone trying to sell an AGP GeForce 6600, which would be preferable to that card for a few reasons (it's flat-out faster and it supports OpenGL 2.1). Where are you located?

Find out what they're asking for it and post your findings. We might be able to work something out, depending on price of course. Can you confirm the card will work, as stated, right out of the box and that it hasn't been overclocked I will assume? Thanks again.

---

### Post by Yellow Pasque on 2010-02-15
Sorry, it was PCI-e, not AGP.

---

