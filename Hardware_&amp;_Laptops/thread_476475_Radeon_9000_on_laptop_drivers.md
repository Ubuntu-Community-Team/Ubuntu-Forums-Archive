---
title: "Radeon 9000 on laptop drivers"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by ravalox on 2007-06-17
Okay, I have an edgy eft install, I did a system update and it seems to have broken my 3d capabilities.  I've been trying to install the radeon 2.28.8 drivers with the installer on ati's website but it errors out.  So am I just confined to reinstalling Edgy Eft and never updating xorg if I want 3d?

---

### Post by Kubunteando on 2007-06-17
Try to follow this guide to install the proprietary drivers:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2)

I used the installation directly from ATI binaries, since the repos did not worked for me.
But that was 9 months ago...

I have the same card as you, and ATI Mobility Radeon 9000, and If you want a good advice use the Open Source drivers. You can get also HW acceleration, the performance is slightly lower, but I have compared as it is the same as in Windows (same Frames per Second in the game cube).

What are the advantages?

First, if there is a new version of the kernel you will need to reinstall the drivers again, that is most like what happened. This does not happen with the Open Source ones.

Second, your card (and mine) is out of support by ATI, so it means that the 8.28.8 are the last drivers, and those they don't seem to compile with the new kernels, so you cannot upgrade to latest kernels having more HW support. You can if you use the Open Source,

Third, the Open Source drivers still gives support for the Radeon 9000

But of course, the choice is of everyone.

---

### Post by teddybairs1 on 2007-06-21
Just wondering if there was any known issues with the ATI Radeon 9000 with the out of the box drivers for Ubuntu Feisty.

---

### Post by shizeon on 2007-06-21
Hello,  I have the same card and have been using the open source drivers the past year.   They work great.  The only downside that I have is that to get decent performance with a 3D desktop, like beryl and compiz, I've had to change my color depth to 16 (from 24).   Other than that everything works and I've had close to zero problems.  I'm (maybe naive) hoping that someday the 24 bit color issue will be worked out sometime in the future.  At least you know that updates are possible with the open source drivers, where with the closed source drivers you are stuck forever in 2.28.8 :(

---

### Post by Kubunteando on 2007-06-26
I am using an ATI Mobility Radeon 9000 with the Open Source drivers work grate in Feisty.
They work even better if you update MESA to the version 6.5.3 ([www.mesa3d.org](www.mesa3d.org)). I have tried also the version 7.0 but I have reverted to 6.5.3 as this seems to consume less CPU.

I haven't noticed any decrease of the performance using 3D application compared with the proprietary drivers. But I have noticed the Open Source are much more stable, and still supported!  Of course I had to do some fine tuning to boost the performance.

As an example I can play Doom 3 in a resolution of 800x600.

A first tip to increase performance: install "driconf" from the repositories, execute it and enable the HyperZ buffer, this should increase the performance noticeably.

I have a Pentium M 2GHz CPU and these are the applications I can run perfectly:

- Doom 3
- Regnum Online (very good 3D graphics MMORPG with Linux client, you need to use MESA 6.5.3)
- Google Earth
- Postal 2
- Sauerbraten
- Planeshift
- NeverWinter Nights
- ...

So far there is only 1 3D game I cannot run (it is damn slow...) and is Ankh 2.
Well World of Padman is also slow. But I think those are issue with the games themselves,since Doom 3 have better graphics, and runs smoothly.

And of course I cannot use the TV output.

---

### Post by dangermouse28 on 2007-07-16
Is there any way to enable the VGA out or TV-out?

---

