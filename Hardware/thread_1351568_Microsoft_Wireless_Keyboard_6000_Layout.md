---
title: "Microsoft Wireless Keyboard 6000 Layout"
date: 2009-12-10
forum: Hardware
---

### Post by milliman on 2009-12-10
I recently purchased a Microsoft Wireless Keyboard 6000 to make working with my Ubuntu 9.10 machine easier.  The keyboard fired right up and works well with the Microsoft Wireless Keyboard 7000 layout except for some of the buttons that X does not recognize.  The layout of the 7000 is nearly identical except the 6000 has buttons for zoom, 5 customer buttons, and Areo Flip.  I would like to utilize those buttons.  I know that there is not a layout for this keyboard so how do I go about making a layout for it? xev doesn't recognize the keys so is there a program that scans for the keycodes that I can run to determine the keys?  Once I have the keys, how do I add them to the 7000 layout to make a new layout?

---

### Post by LinuxDeal on 2009-12-21
You realize you have to position your mouse cursor over the little box in xev, right?
If xev doesn't detect the keypresses, the only thing that will save you is a driver.

And you realize you said you "purchased a **Microsoft** Wireless Keyboard 6000 to make working with [your] **Ubuntu** 9.10 machine easier." (emphasis added) ???
Just making sure.

---

### Post by RockMan81 on 2012-05-03
Old post, i know, but I have an answer...
I a very similar keyboard, and i noticed that the events for these special keys are sent to /dev/usb/hiddev0. So i started making a tool for reading them. It's still in early stage, but working. You can find it here: [http://github.com/rockman81/Touche](http://github.com/rockman81/Touche)
Any feedback is welcome :)

---

