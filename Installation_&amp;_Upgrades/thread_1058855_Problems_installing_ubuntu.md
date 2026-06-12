---
title: "Problems installing ubuntu"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by ricardopleal on 2009-02-03
I have a Asrock motherboard p4i65GV with a agp graphics card (geforce 6200 256mb). I'm trying to install ubuntu 8.10 but when is starting the installation (the screen with ubuntu logo and the orange progress bar, freezes in the beginning and i have to reset the pc. I tried to start the live cd and happens the same. I also try chose the F4 option in the boot and chosse secure graphic mode (or something like this).

If i remove the graphics card and use onboard graphics it installs and work fine, so i thing that the problem is something related with geforce 6200 (In windows Xp works fine)
I want to use the 6200 and ubuntu 8.10 so if someone can help me i'm pleased.

Thanks for your time

---

### Post by sonu 1807 on 2009-02-03
With my nvidia GEforce 7150M same thing happens with ubuntu 8.10 (intrepid) and not with ubuntu 8.04 (hardy). The installation will proceed normally if u keed pressed any button for some time. I am running 8.10 and it gives no hassles other than this. You have to keep any button pressed for a few seconds every time you boot. This won't be the case with hardy.

---

### Post by ricardopleal on 2009-02-03
i tried to press any button for some time and the system don't start. It frezzes exactly in the same point

---

### Post by icanfly0307 on 2009-02-03
When you the progress bar freezes, press Ctrl+Alt+F2. This should give you a log of error messages. Post them back here.

---

### Post by ricardopleal on 2009-02-03
> **icanfly0307 said:**
> When you the progress bar freezes, press Ctrl+Alt+F2. This should give you a log of error messages. Post them back here.

ctrl + alt + f2 doesn't work.

---

### Post by avtolle on 2009-02-03
For my clarification, you have installed with the graphics card removed, using the on-board graphics only. Your problem occurs with trying to install with the graphics card inserted.

You also mentioned that you had tried installation in safe-graphics mode. While you did not indicate this in your post, I presume you had the same problem in safe-graphics.

From memory, there are some old threads on the Forum involving installation with on-board graphics only, then installing the card with the system up, and then loading the correct driver for the card. You might want to see if a search will uncover one or more of these.  Good luck.

---

### Post by avtolle on 2009-02-03
Or, you could download the alternate cd iso and, after burning it to disk, use it to try to install. I've used it (alternate) since 7.04 to install, as the Live (Desktop) CD has issues on my hardware. Sometimes, use of the alternate is the only way to install when a graphics card causes trouble with a Live CD install.

EDIT: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate) to get the alternate iso.

---

### Post by Paoletta_Portenti on 2009-02-03
Just want to report the same apparent problem here. BIOS gives two choices: onboard graphics, or "auto", which allows the PCI geforce 6200 to override the onboard graphics. 
I can boot into the CD when BIOS is set to 'onboard', but not when using the PCI 6200 (note that this is indeed PCI, not PCI-E).
Have tried a 7.04 CD I still had in a drawer, Slax, LinuxMint, and the bootable CD version of GParted, which I also had around. All of them freeze at some point, with no cursor, nothing, and a hardware reset the only way to get out. Have tried safe graphics mode, no luck.
Distros that are more verbose than Ubuntu report panic at the moment of freezing. I could write down what they report right before that. 
Note that this type of issue with the PCI geforce 6200 has shown up before, but I have not seen a solution yet.
Please let me know if this belongs here, or if it ought to be a separate thread.

Thanks

---

### Post by Paoletta_Portenti on 2009-02-03
I just gave a try to 8.04 (Hardy Heron), and the CD boots perfectly using the 6200 card!
Again: 7.04 and 8.10 freeze, 8.04 does not. 
This was suggested in another thread regarding PCI geforce 6200 issues. 

So then, what would be the logical install path?

Install 8.04, then update? 
Install 8.04, update nVidia drivers, then update to 8.10? 

Can RicardoPleal tell if 8.04 works for him?

I hope we can sort through this. It is the only thing that still stops me from migrating to Ubuntu from Windows.

---

### Post by icanfly0307 on 2009-02-04
Why not just stick with 8.04? 8.04 is a long term release which means that you can keep it until 2011 and it'll recieve security updates till then. 8.10 will get off the road in 2010 and there's no guarantee that things will work if you upgrade. So my suggestion: stick with 8.04.

---

### Post by tneva82 on 2009-02-04
Hum. I have similar problems(though I'm not sure is freeze right word. CD keeps turning from the sound it makes but nothing seems to happen). I have radeon 4870 though as graphic card. No built-in card in the motherboard though so can't test with it.

Assuming alternate cd doesn't solve issue what else could be causing it?

---

### Post by icanfly0307 on 2009-02-04
The alternate install cd *will* solve the issue since it doesn't need the graphics card to work. nVIDIA needs propritery drivers to function properly and those aren't available until the installation is complete. So all you have to do is install using the alternate install cd and enable restricted hardware drivers to get it to work.

---

### Post by trash on 2009-04-27
I had to buy myself an ASROck p4i65gv today and so far the only version to give me any joy was an old 5.10 live cd i had from days gone by.
Booted up no problem using onboard graphics... will keep looking for the 5.10 install cd.
Has anybody else made any progress?

---

### Post by trash on 2009-04-27
5.10 installed without any trouble what so ever!!

Now if i were to upgrade because there are no repositories for 5.10 anymore... which would you guys recommend I try upgrading to? version to version IE. 6.10->7.10->... or just jump directly to hoary.. or even jaunty?


EDIT:doing a dist-upgrade to jaunty... figured i might as well try the latest first and work my way backwards till I find an upgrade that works lol.
EDIT2:no joy with jaunty(libc6 hell and a cryptic install 'lenny kernel')
Breezy->Dapper went well Dapper-> Hoary FAILED with dependency issues..

This is retarded! I'm now trying to install 9.04 commandline system and hopefully apt-get a desktop...

---

### Post by trash on 2009-04-28
WE HAVE JAUNTY JOY!!!

install 9.04 commandline system and then apt-get a ubuntu-desktop.

good luck!

---

### Post by alvilsb on 2011-01-12
Easy folks.

This mainboard is goddamn crappy, as it does not have a "real" AGP port, but the "AsRock Graphics Interface" (AGI), also known as "poor man's AGP" instead. It works just with select video cards. Nevertheless, cards that are not supported in general do not get "recognized" at all. If the BIOS video output goes through your add-on card, it will perhaps work. Except for the fact that due to the inability to completely turn off the embedded Intel Extreme Graphics 2 chip, most Linux flavours get stuck here. In general, the errors you will see will be something about problems with your CD/DVD drive, hard drive, or USB devices. To remedy these issues, you have to do the following:
1. Remove your add-on card.
2. Install Ubuntu (or any GNU/Linux flavour you like anyway)
3. Blacklist the agpgart (not needed, since that's not a "real" AGP and this driver is one of those "f**king things up") and intel_agp drivers (kernel modules, anyway). In Lucid, this is done in the following way:
sudo gedit /etc/modprobe.d/blacklist.conf
Add the following two lines in the end of your blacklist.conf:
blacklist agpgart
blacklist intel_agp
Then, run the following command:
sudo update-initramfs -u

Then, shut down your machine, add your video card and enjoy! For ATI/Nvidia cards, it's recommended to install the non-free driver though to get full 3D performance.

Hope this helps.

---

