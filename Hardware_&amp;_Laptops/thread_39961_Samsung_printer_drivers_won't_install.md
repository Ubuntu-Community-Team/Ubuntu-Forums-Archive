---
title: "Samsung printer drivers won't install"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by g-joey on 2005-06-07
Hi,

I have bought a "Samsung CLP-500" color laser printer which has Linux drivers included. Unfortunately, the driver installation program relies on "GTK+ 1.2 libraries", while my Ubuntu has GTK+ 2.0... Thus the installation fails right after the start.

Is it possible to have GTK+ 1.2 installed parallel to 2.0? Or is there a workaround how to get the installer to work?

TIA, Joe

---

### Post by rmjokers on 2005-06-07
I also have a samsung printer (ML-1740).  The printer driver installer also relies on having admin priviledges to do some modifications to the cups configuration using the web interface (localhost:631).  Unfortunately, Ubuntu's version of cups has been compiled without support for administration through the web interface so the installer cannot be used to set up the printer.  My printer works without the official samsung driver, but the margins are off slightly so that it almost runs over the end of each page.  I dont know if your printer will use the same samsung installer, but if it does you will also have to deal with this issue as well.  Good luck.

---

### Post by rwabel on 2005-06-07
I've the same color printer from samsung and I did never achieve to use it. I've it plugged on a windows machine. I don't think that this is the problem, because the HP LaserJet is working fine.

I've installed the drivers. You can just use either kde printer configuration tool (kinda better than the gnome one) or the gnome one and choose the appropriate driver. Ubuntu also finds the printer on my windows xp machine, but I always get an error. I can't remember the error message I get when I want to print..I gave up on the whole Samsung printer stuff

If someone achieves to print on that damn printer, please let me know

---

### Post by g-joey on 2005-06-10
> You can just use either kde printer configuration tool (kinda better than the gnome one) or the gnome one and choose the appropriate driver.
So this means I don't need the Samsung drivers at all? Okay, I'll give it a try...

 > I've it plugged on a windows machine. 
Well, I just have switched from Windows 2000 to Ubuntu Linux :?

Maybe if Devolo finally manages to deliver their new "ethernet over the household power circuit" adapter I'll connect the printer to my other PC (Windows XP) two floors above :wink:

//Joe

---

### Post by rwabel on 2005-06-10
I wrote, that I've installed the driver. Either you install the whole samsung stuff or you then choose the driver when asked for while installing a priner via gnome or kde printer.
I got one packed file which I did extract and then I got somewhere there the driver file which I then gave the kde or gnome printer setup. It then installs the driver.

---

### Post by g-joey on 2005-06-11
> I wrote, that I've installed the driver.
Sorry, I meant "I don't need the Samsung driver **installation program**", because that is the part that doesn't work on my machine.

//Joe

---

### Post by rwabel on 2005-06-11
[QUOTE=g-joey]Sorry, I meant "I don't need the Samsung driver **installation program**", because that is the part that doesn't work on my machine.

//Joe[/QUOTE]
 right, u only need the driver file from the archive you downloaded.
let me know if you could install the driver. if the printer will work is another thingk, at least for me ;-)

---

### Post by g-joey on 2005-06-21
>  let me know if you could install the driver 
Sorry for answering so late, I just had not enough time for the PC...

The driver was installed without any error (message), but, as you had already guessed, it doesn't work.

Sine I needed the color pages urgently I have installed an old Windows 98SE on a small partition of the PC and, well, it *just worked.*

Thanks anyway, Joe

---

### Post by timczer on 2005-06-24
I also have a ML 1740 and by following the instructions in the last couple of posts in this thread [http://www.ubuntuforums.org/showthread.php?t=31796](http://www.ubuntuforums.org/showthread.php?t=31796)  I was able to get the drivers to load.

---

