---
title: "Install stops at checking battery state"
date: 2008-11-11
forum: General Help
---

### Post by surfgeko on 2008-11-11
I am determined to play around with ubuntu (currently using vista) and possible switch to it after getting a larger hard drive.  Anyway, i installed ibex using wubi (note that a few months ago i installed heron with wubi with no trouble, but have since uninstalled it), and i am able to boon into ubuntu, it finishes the installation in what looks like a loaded gui, and when this is completed, a command line window is opened, it loads a few things but stops at "checking battery status".  I am able to ctrl-alt-f1 to a working terminal, and after some googleing, the stalling at seems to be caused by bad nvidia drivers often.  So i downloaded and installed EnvyNG, although i am not sure if it works in ibex as of now.  Anyway, i installed the nvidia drivers through envy, and restarted GDE, ctrl-alt-f7 back to the gui and............nothing.  After this i tried rebooting, and in the grub bootloader choosing the installer for video problems, notice that though i finished the install ALREADY, it still makes me finish the install, thus wiping envy from my install, and any changes it may have made.  The text-based installer works flawlessly, right and blasts right through the checking battery state into a nice open terminal window, a successful install. or so i thought. reboot, and low and behold, it wants to finish the install AGAIN.  i tried all of this with various tweaks in the order and i have gotten nowhere.  A funny quirk, if i choose to boot to a live desktop (essentially loading a live cd off of an iso on my drive) in the boot menu, it loads up just peachy, and i have a perfectly usable ubuntu desktop, with NO GRAPHICAL PROBLEMS.  werid. any ideas?:(

---

### Post by surfgeko on 2008-11-13
Anybody? i would really like to get ubuntu working.

EDIT: 102 views in 3 days and NO responses!?  c'mon people, any ideas?

---

### Post by ancientrustic on 2008-11-14
I have exactly the same problem. I did, an apparently successful, upgrade but on rebooting I was stuck with "checking battery state". I then tried a clean install and the live cd stuck at the same point. Alternate install cd seemed to work but on rebooting I was back with the same problem. My laptop is a Toshiba Satellite Pro with Radeon HD 2400 graphics. I have now reinstalled 8.04. Is there no one out there with a solution? This seems to be quite a common problem.

---

### Post by surfgeko on 2008-11-17
well this stinks...=/

---

### Post by ago on 2008-11-18
You might try booting with acpi=off, if you search the forum you might find other solutions, this is unlikely to be related to wubi per se

---

### Post by espycious on 2008-11-18
I also have a Toshiba Satellite with a Radeon HD 2400 graphics card. It is doing the exact same thing on both an upgrade from 8.04 and a clean install. Maybe the drivers are no good on Intrepid :(

---

### Post by surfgeko on 2008-11-20
if i boot with acpi off, i get a bunch of scrollling text, ending with soemthing about busybox and a prompt.  from this prompt i cant login, however i can reboot etc.

---

### Post by g_tune on 2009-03-23
My son attempted an Ubuntu 8.10 install on a 60GB SATA laptop HDD that he attached to his 400W PC with same result on bootup. Fixed the issue by removing one of the nVidea 8600GT 512Mb DDR2 SLI cards. I figure that this has worked because the 400W PSU is no longer "taxed to the max" so why don't you try reducing the amount of RAM allocated to your onboard Video Card & see if that helps free up the laptop PSU & battery pack.

---

