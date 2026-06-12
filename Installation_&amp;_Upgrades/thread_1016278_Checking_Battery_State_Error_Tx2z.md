---
title: "Checking Battery State Error Tx2z"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by Rcommander on 2008-12-19
Okay sorry if this is a repost but I couldn't find anything recent and specific to me.

I have a HP touchsmart tx2z
AMD ZM84
6GB Ram
ATI 3240? Whatever is the standard one...there aren't any options for the graphics card.

I have tried to install IBEX several times but the live and the install both hang up on "CHECKING BATTERY STATE" after the install. I have tried the LiveCD and Install with acpi=off and noacpi but neither works. HELP!!

---

### Post by Favux on 2008-12-21
Hi Rcommander.

The 32-bit or AMD 64-bit install?  Did you try the alternate install iso?

---

### Post by oceanexplorer on 2009-01-02
Hi,

I have had the same issue with a ATI HD2400 card, however it seems the system does not hand, if you hit alt + f2 (or alt + f4 i can't remember which) it should drop you to a command line.

It was here that I was able to type startx to load the GUI, but it returned errors, suggesting it did not like my video card.

So I connected the laptop to my network with a cable (this way it will automatically connect as my wireless in encrypted) and issued the following commands:

sudo apt-get install xorg-driver-fglrx jockey-gtk

Then press Y when asked and hopefully it should connect to the Ubuntu Repo and download the driver.

Once done type sudo aticonfig --initial

this should overwrite your xorg.conf with a default setup.

Then type startx and hit enter...with any luck you should now see the GUI.

Paul

---

