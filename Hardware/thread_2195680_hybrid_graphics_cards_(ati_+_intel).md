---
title: "hybrid graphics cards (ati + intel)"
date: 2013-12-25
forum: Hardware
---

### Post by roma24ster on 2013-12-25
Hi
I understand ubuntu now supports hybrid graphics cards
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

I have a ati 7670 and a intel in my laptop. The instructions in the above article say that if i do ```
[COLOR=#666666][FONT=Monaco]sudo apt-get install fglrx fglrx-pxpress[/FONT][/COLOR]


``` then it the hyrbird graphics cards will work, my question is has anyone got this working with the newest fglrx 13.12 graphics driver on ati's website, rather than the version of fglrx from the repos.

I've already looked at [http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide) but it doesn't seem to have been updated in a while.
Thanks

---

### Post by Bucky Ball on 2013-12-25
Bumblebee is apparently the go for hybrid graphics, although I am not knowledge about the ins and outs having never used.

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Dig around a bit and there should be plenty of food for thought.

---

### Post by roma24ster on 2013-12-26
Hi, thanks for you reply. I think bumblebee is for nvidea graphics cards only

---

### Post by Mark Phelps on 2013-12-26
> I have a ati 7670 and a intel in my laptop.Then, look through the linked thread to see if anything there helps:  [http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics]("http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics")

---

### Post by Bucky Ball on 2013-12-26
Nice tip and Alexislavie you legend, but be aware that:

> Edit bodhi.zazen: Best check hardware compatibility before following this tutorial. If your hardware is not listed as supported, this tutorial will not help you. See [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware) 

---

### Post by caymus on 2013-12-26
You need to reboot each time you swap from ati to intel & vice versa or not? (i dont understand if this is going live or not).

> 
[FONT=Arial][SIZE=2]configure the Xserver (xorg.conf file) for the first time :
     Code:
     sudo aticonfig --initial -f 
Now reboot your computer.

Test the switch to the discrete card :
          sudo aticonfig --px-dgpu 
Then reboot again your computer.[/SIZE][/FONT]

PowerXpress: Discrete GPU is selected (High-Performance mode), please restart Xserver(s) for changes to take effect!

:rolleyes:

---

