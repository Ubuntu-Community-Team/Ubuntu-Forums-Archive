---
title: "How do I install stuff on my Palm OS pda?"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by turtlepaul on 2007-01-17
I have a palm T|X and would like to install new software on it. How do I do that?

---

### Post by CameronCalver on 2007-01-17
i have one of them to and i could never find an answer just bought a sd card and a card reader but i understand there is a program that makes your palm pda look like a thumb drive but i could never access the internal memory

---

### Post by turtlepaul on 2007-01-18
But can I install applications on the card without the Palm installer software?

---

### Post by thoman on 2007-01-18
Hello there

I do have TX as well, I kept wondering how do i kept my device sync ....

Newbie..

---

### Post by zvandiver on 2007-01-18
There are two main apps for syncing a Palm device, Kpilot and jpilot.  Jpilot most closely resembles the Windows Palm Desktop.
Zane

---

### Post by MoLE on 2007-02-03
> **zvandiver said:**
> There are two main apps for syncing a Palm device, Kpilot and jpilot. 

Don't forget the default one built into standard Ubuntu - gnome-pilot.

Briefly, to install a palm application using gnome-pilot, first set it up using the method described on [ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_PalmOS_Devices").

You have to enable the file conduit during the setup of the palm (using the applet).  Make sure everything is synching properly.

New programs can then be installed using the terminal command:
gpilot-install-file --now /path/to/prc/file.prc

You will then be prompted to hit the hotsync button.

We still have a long way to go before PDA synching works "out of the box" for Ubuntu.

---

### Post by turtlepaul on 2007-02-21
I've downloaded Jpilot and it looks pretty nice, but how do I get it to connect to my palm?

---

### Post by turtlepaul on 2007-02-21
Disregard that last post. What I *meant* was how do I use Jpilot to install new applications on my palm?

---

### Post by djcrash1981 on 2007-02-27
I have a T|X and i use the **gpilot-install-file** to install files on the palm and it works without trouble at all.

---

### Post by veloce on 2007-03-26
> **turtlepaul said:**
> Disregard that last post. What I *meant* was how do I use Jpilot to install new applications on my palm?

You use the "install" command in the "file" menu.  

I've got that far, but want to install to the SD Card - still searching for that functionality.

---

