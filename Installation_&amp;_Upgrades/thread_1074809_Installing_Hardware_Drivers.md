---
title: "Installing Hardware Drivers"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by Klitsie on 2009-02-19
Hi,
I am new to ubuntu and want to install all my hardware drivers.

First question:
Where can i see an overview of my hardware? So i know witch ones i have.
A list of the ones i know:
Asus P5E motherboard
Intel e6400 cpu

Dont know my audio card
Dont know my wireless internet card

Second question: 
Can i find all the drivers on the manufacturers sites?


Ty

---

### Post by avtolle on 2009-02-19
Chances are, the two drivers you will need are for your video card and wireless card. From the command line (Applications>Accessories>Terminal) do ```
lspci
```and post the results. If you have either an ATI or a nVidia card, you should go to System>Administration>Hardware Drivers which will contain a list of possible drivers (and the same for certain wireless cards) with one recommended to activate. 

On going to the manuafacturer's website; maybe there will be a driver there, but let's take a look at what you might need first.

---

### Post by Klitsie on 2009-02-19
K thanx,
But the drivers for my motherboard (chipset and everything) and cpu are already installed? or not?
I have a soundcard that came with my P5E, the driver is on a cd, but its vista only :/

---

### Post by avtolle on 2009-02-19
The drivers for your cpu, mobo are likely already contained within the kernel. As to the soundcard, don't know, but you are correct about the Vista driver not being applicable in Linux. 

Have you installed yet? Or, have you run a Live CD session to see how things go?

---

### Post by Klitsie on 2009-02-19
> **avtolle said:**
> The drivers for your cpu, mobo are likely already contained within the kernel. As to the soundcard, don't know, but you are correct about the Vista driver not being applicable in Linux. 

Have you installed yet? Or, have you run a Live CD session to see how things go?

I installed ubuntu yes.
But its not an onboard soundcard. Its an pci card, from Asus.
It isnt installed, cause i dont hear any sound.
Also another problem:
[http://ubuntuforums.org/showthread.php?t=1066245](http://ubuntuforums.org/showthread.php?t=1066245)

Ty

---

### Post by avtolle on 2009-02-19
I don't have an ATI card, so I'll be of no real help on that problem; and I don't have a soundcard as yours, again I'll be of no real help there, either. Generally, on the graphics card, stay with the thread you have open; I note the error message advised running aticonfig. That would (obviously) be run from the command line; whether you would need to be root (sudo for our purposes) to run it I don't know.

---

