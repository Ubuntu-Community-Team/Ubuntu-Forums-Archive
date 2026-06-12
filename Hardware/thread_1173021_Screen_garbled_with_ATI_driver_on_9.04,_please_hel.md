---
title: "Screen garbled with ATI driver on 9.04, please help"
date: 2009-05-29
forum: Hardware
---

### Post by BrownCoal on 2009-05-29
I need to use to proprietary driver because in need s-video out which the open-source driver doesn't do (even with the atitvout app).

9.04 Installs fine but has a garbled screen on first boot, see image: _[http://i626.photobucket.com/albums/tt348/89f5hb/garbled_ubuntu_904_jaunty_ati.jpg](http://i626.photobucket.com/albums/tt348/89f5hb/garbled_ubuntu_904_jaunty_ati.jpg)_

(mythbuntu screenshot, same problem with ubuntu)

how do I fix this?

[update: my card is a radeon 9600]

---

### Post by masux594 on 2009-05-29
Hi.. Well, i'm a newbie with ubuntu but, i had the same problem.. you have the ATI 9600, and i have the x1950PRO, newer but with the same problem.. The ati-catalyst releases of april and may [if u read the release notes], support ATI products from R600 [HD 2xxx] and newer.. Well, i solved this problem installing the RadeonHd drivers with [**this**** ****guide**]("https://help.ubuntu.com/community/RadeonHD")! The support for older graphic cards, comes every 3-4 months, but i'm not sure that it will support ubuntu Jaunty release!

Sysc A

---

### Post by arnoldus on 2009-05-30
I have the same problem. I have the X600 card (PCI version of the 9600). I didn't even installed the ATI driver, just the control panel that's listed in the package manager.
 
I saw the link to your fix, but as I can't get into the system, I don't know how to fix it? Is there a kind of commandline mode where I can do the things mentioned here?
 
(even while booting with 'xforcevesa' or 'vga=791 noreplace-paravirt' I can't get a clear image)

---
Can confirm it works after purging the drivers. Boot into the shell using the recovery console (or other methods) and purge the drivers out.

---

### Post by BrownCoal on 2009-05-30
I pieced together that ATI has stopped supporting the Radeon 9600, so their proprietary driver only supports some newer cards. Like masux594 said: the driver for old 'legacy' cards only comes a few months after the 'late-model' driver, if at all.

I think that the driver that was showing the garbled screen was the 'late-model' driver and not the 'legacy' one, and the changes in Jaunty mean that the legacy ATI proprietary driver for Intrepid Ibex doesn't function in Jaunty. So there isn't yet support for s-video on legacy ATI cards in Jaunty, so I cant use it to watch videos on my TV.

I haven't used the guide that masux594 used, I think I will try everything to get s-video output with the open-source ATI driver before I try it.

If you want to go to the command-line: start in 'recovery mode' from the bootup menu, wait for text to fly by, and then from the 'Recovery Menu' select "root - drop to root shell prompt", which is the regular command line. Afterwards if you want to try an start the GUI from the command-line, type 'telinit 3'.

---

### Post by Yellow Pasque on 2009-05-30
The radeonhd driver only works for X1k (R500) or newer. Don't follow that guide for a Radeon 9600.

---

