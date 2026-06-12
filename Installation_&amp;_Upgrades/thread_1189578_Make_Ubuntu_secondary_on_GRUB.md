---
title: "Make Ubuntu secondary on GRUB"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by coolgamer512 on 2009-06-16
Hey guys. I'm installing Ubuntu 9.04 (x64) on my new computer, but I want to keep the currently installed Windows 7 (x86) as the primary partition on GRUB, so the computer only goes into Ubuntu if I tell it to do so during the ten seconds that the boot menu is up. How do I keep Windows 7 as the primary?

In case it helps, here's the specs of my computer:


Core i7 920 processor overclocked to 4.2 GHz on Xigmatek S1283V Dark Knight cooler

EVGA X58 3X SLI Motherboard

Corsair Dominator 3x1 GB 1600 MHz

EVGA Geforce GTX 285

2x Sony Optiarc 24x Lightscribe DVD Burner

Super Talent INTAIN1MCR Media Reader

Western Digital Caviar Black 1TB Hard Drive

Cooler Master Storm Sniper case

---

### Post by merlinus on 2009-06-16
You need to edit /boot/grub/menu.lst and move the windows lines above the one that says:

### BEGIN AUTOMAGIC KERNELS LIST

You could change the default instead, but you will have to do this again every time there is a kernel upgrade.

---

### Post by presence1960 on 2009-06-16
Install startupmanager by running in terminal ```
sudo apt-get install startupmanager
``` or install it thru Synaptic Package Manager by going System > Administration > Synaptic Package Manager. Set the default OS in startupmanager.

then to let it start the default OS unless you hit Esc to bring up the GRUB menu open a terminal and run ```
gksu gedit /boot/grub/menu.lst
``` That is a lowecase L in .lst. 

To forego the GRUB menu unless you hit escape comment out hiddenmenu like the example below and set the default time to the amount of seconds before the default boots:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

## hiddenmenu
 Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

I believe you can do this in startup manager as well, but it is always good to learn some terminal ways of customizing also.

---

### Post by raymondh on 2009-06-16
posting a screenshot of startup manager as a reference to what presence1960 was saying....

---

### Post by merlinus on 2009-06-16
So what is the advantage of using startup manager as opposed to editing menu.lst and using grub?

---

### Post by presence1960 on 2009-06-16
no advantage, one is GUI and the other is terminal. Two ways to do same thing.

---

### Post by merlinus on 2009-06-16
So startup manager writes its settings to menu.lst automatically?  And does grub still appear when using it?

Obviously things have changed since 5.x!  I guess I am still from the terminal and manually editing files days.  No boot up scripts, just command outputs for troubleshooting.

Guess I'll go kayaking instead... 

I actually loved DOS.  You either learned the commands, or could not use the computer.  None of this gui stuff...   :p

---

### Post by raymondh on 2009-06-16
> **merlinus said:**
> So what is the advantage of using startup manager as opposed to editing menu.lst and using grub?

Nothing I can think of.....even when a new kernel comes around, we either have to re-edit menu.lst or re-select the preferred option in startup manager. 

Can I say ... "I'm just being lazy"?  :)

---

### Post by presence1960 on 2009-06-16
> **merlinus said:**
> So startup manager writes its settings to menu.lst automatically?  And does grub still appear when using it?

Yes startup manager writes it's settings to menu.lst. GRUB still appears. Startupmanager is a good tool for those newbies who are still afraid of or have no knowledge of terminal. I try to suggest both that way learning  how to do the same thing two ways shows how good Linux really is.

---

### Post by merlinus on 2009-06-16
Thanks for the info.  Guess I am the curmudgeonly sort - I recall when windows 1.0 appeared.  Its only function was as a front end for using PageMaker!

If you teach mouseclicks and menus, then when the gui and wimps are gone, the folks are lost.  Learn the CLI and you can run commodore 64s!

---

### Post by u-slayer on 2009-06-17
You could set it up like I have it on my laptop. Windows 7 is installed as the default operating system. When you boot the computer its the first thing that pops up without any GRUB menu at all. If you want linux, You have to insert the usb drive that contains my /boot partition with grub to load the fully encrypted Linux Partition. Good for airport security.

---

### Post by coolgamer512 on 2009-06-17
Well thanks for the help guys. I used startup manager to do the trick. Windows 7 is now set as the primary, Ubuntu being secondary.

---

### Post by presence1960 on 2009-06-17
> **coolgamer512 said:**
> Well thanks for the help guys. I used startup manager to do the trick. Windows 7 is now set as the primary, Ubuntu being secondary.

Great enjoy Ubuntu! When you get some time look at your menu.lst file and see if you can spot the changes you made with startupmanager. You can open menu.lst by running in terminal ```
gksu gedit /boot/grub/menu.lst
``` You will be better equipped to use Linux if you learn some terminal stuff. For now the GUI is ok. Also when helping someone else they may have a different desktop and their GUI may be different than yours. It is so much easier to type or paste a command in terminal rather than follow directions such as click on this, select the xyz tab and click edit. In terminal all is the same .

---

