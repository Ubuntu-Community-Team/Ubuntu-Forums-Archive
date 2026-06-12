---
title: "Confused:  ThinkPad, Hybrid Graphics, and Bumblebee"
date: 2013-09-04
forum: Hardware
---

### Post by buzzingrobot on 2013-09-04
Here's a question about hybrid laptops, Bumbelee, and heat:

My new ThinkPad has the onboard Intel video, an Nvidia card, and can be set in BIOS to use either the Intel, the Nvidia, or run in Optimus mode.

I've seen several statements that both cards will be on unless Optimus/Bumblebee is used. Is that correct?

I have selected the discrete Intel in the BIOS.  Is the Nvidia turned off, or is it still on and generating heat?

If the latter, will installing Bumblebee, and leaving the Intel set in BIOS, mean the Intel will always be used and the Nvidia will always be turned off?

Or, to use Bumblebee, do I need to set the BIOS to Optimus, then tell all programs to use Bumblebee, or not, by launching via the terminal?  That's pretty inconvenient.

---

### Post by grahammechanical on 2013-09-04
Nvidia is yet to release a Linux driver for its Optimus technology. Such a driver is under development. This link is dated 08 August 2013. Other than that it is Bumblebee.

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

Note the references to Ubuntu Saucy Salamander (13.10)

Regards.

---

### Post by buzzingrobot on 2013-09-04
> **grahammechanical said:**
> Nvidia is yet to release a Linux driver for its Optimus technology. Such a driver is under development. This link is dated 08 August 2013. Other than that it is Bumblebee.

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

Note the references to Ubuntu Saucy Salamander (13.10)



Thanks. Still confused, though.  

 What I'm after is always using the Intel and being sure the Nvidia is always turned off.  I'm looking for confirmation that, in fact, that's the state of affairs when the Intel is selected in BIOS. (I've read articles about Bumblebee that suggest the Nvidia *is* on even if it is not selected in BIOS, and that I need to run Bumblebee to correct that.)  If not, how do I get there?

I don't run games, don't use multiple monitors, don't use the ThinkPad for movies, and short Flash videos run fine.

---

### Post by Linuxisfast on 2013-09-06
If you are worried use VGA switcheroo and blacklist nouveau and dont install nvidia proprietary drivers and only Intel will be used.

---

### Post by Yellow Pasque on 2013-09-07
I don't see why the nvidia card would remain on when you select Intel inthe BIOS,, but if you really want to be sure, here are the directions (again: [http://ubuntuforums.org/showthread.php?t=2169751&p=12766937#post12766937):](http://ubuntuforums.org/showthread.php?t=2169751&p=12766937#post12766937):)
1. Select 'Optimus' in the BIOS.
2. Install bumblebee (which will install bbswitch and keep the nvidia GPU off)

> Or, to use Bumblebee, do I need to set the BIOS to Optimus, then tell all programs to use Bumblebee, or not, by launching via the terminal? That's pretty inconvenient. 
You only need to "tell" programs that you want to run on the nvidia card. So from your description (not wanting to use the nvidia card), you don't need to do anything special once you have Bumblebee/bbswitch installed.

Oh, and I hope you use the nvidia GPU for something, even if not on Linux. Otherwise, you have yourself a relatively expensive paperweight...

---

