---
title: "Someone please help me!!"
date: 2008-10-13
forum: General Help
---

### Post by lostfate on 2008-10-13
I just got my Ubunta CD a few weeks ago and I have spent many restless nights just trying to figure out how to format my pc and install Ubunta over Windows XP because my Windows XP has a virus... I do not have the CD to it -_- so I am stuck with a large brick if I do not figure out how to boot from CD...

I already know that you stick the CD in your CD drive but how in the world do you boot from it?...

Someone please help me!! Thanks

---

### Post by Ryadt on 2008-10-13
Boot your pc and press either f2 or delete to enter BIOS. Then change the boot option inthere to cd rom first and then save and exit.

---

### Post by shawnrgr on 2008-10-13
you need to change to boot order in your bios to boot cd before hard drive. when you boot up you may also have the option (sometimes f11, it will say it in the corner at first boot) to select boot. then choose cdrom drive. you could also check the manufacturers website for your pc model, it should tell you how to change this with your specific bios.

---

### Post by lostfate on 2008-10-13
I've tried entering my bios by pressing f2... it takes me to the bios but I don't really understand anything in the bios... much less how to make my cd drive bootable... what do you mean by delete?

Also shawnrgr; my pc model is mostly IBM and INTEL

I set my DVD-R & CD-R burner to "Cable Select" when I installed it... would that affect anything?

---

### Post by Liv3dN8as on 2008-10-13
Try F12 during boot and then select CD from the list.

---

### Post by namegame on 2008-10-13
The delete key is another possible way to enter BIOS however your computer enters BIOS by pressing F2. Delete is probably irrelevant here.

Depending upon your BIOS manufacturer, somewhere you should see a menu about Boot-order or Boot device priority. You'll need to change this so that the CD-ROM drive first in the list.

---

### Post by lostfate on 2008-10-13
Liv3dN8as I will try f12 and I will be back in a few minutes

My pc model is custom but its mostly made up between IBM and Intel parts..

---

### Post by shawnrgr on 2008-10-13
Look for something like this... (see screenshot)

[IMG]http://files.powersp00n.nl/zepto-bios/DSC00094.JPG[/IMG]

---

### Post by cariboo on 2008-10-13
Depending on your BIOS, when you have the the menu up the second choice on the left is usually where the boot order is located. Use the arrow and tab keys to navigate through the menu. In most cases pgup and pgdn change the values. Once you have changed your boot order. press F10 to save and exit.

Don't worry about making a mistake as you can always go back and undo what you did. If worse comes to worse you can always reset the bios and start over again.

Because there are some many different BIOS menus it might be worth it to dig out the owners manual for your motherboard and read up on the bios in the manual.

Jim

---

### Post by lostfate on 2008-10-13
> **shawnrgr said:**
> Look for something like this... (see screenshot)

[IMG]http://files.powersp00n.nl/zepto-bios/DSC00094.JPG[/IMG]

Mine doesn't have a boot setup in my bios... :(

I will take a screenshot of it...

and when I press delete it does nothing;

When I press f12 it got my hard drive as the only bootup option

---

### Post by Liv3dN8as on 2008-10-13
> **lostfate said:**
> When I press f12 it got my hard drive as the only bootup option Sounds like your cd drive isn't being recognized. Check the connections inside the pc, make sure everything is connected tight.

---

### Post by lostfate on 2008-10-13
The only tabs in my Bios "IBM Setup Utility" is "Main, Devices, Startup, Advanced, Security, Power, and Exit" those are all the tabs in my Bios "IBM Setup Utility" nothing about boot or booting... :(

Yesterday I just installed my CD-R & DVD-R burner... There is three jumpers on the back... "Master, Slave, and Cable Select" settings, I went with "Cable Select" would that have any affects on anything?...

Because my CD drive works great in Windows itself...

---

### Post by Liv3dN8as on 2008-10-13
It would most likely be under Startup. Look for some way to move around the devices to make the cd be on top. You might have to press something like the spacebar to enable the device. Not sure if cable select would make much differance.

---

### Post by lostfate on 2008-10-13
hummmmm.... I am going to check and see if its under startup and I will be right back

---

### Post by lostfate on 2008-10-13
YES! I DONE IT! HAHAHA NOW I AM RUNNING THE POWER OF UBUNTU!!! HAHAHA It took me forever to find that... Now, I have two questions... how in the world do I install Adobe Flash Player to Ubuntu and how do I install a anti-virus/spyware to it?

---

### Post by Liv3dN8as on 2008-10-13
You can install Adobe Flash Player from this [Adobe](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) site.
I'm not sure about anti-virus programs for Ubuntu.

---

### Post by Ryadt on 2008-10-13
Install ubuntu restricted extras. Go in the terminal and type this ```
sudo apt-get install ubuntu-restricted-extras
```

Anti-viruses and anti-spywares are not required in linux. You can install one, like clamav which is in the repos, if you intend to share files with a windows system.

---

### Post by lostfate on 2008-10-13
One last question... on the adobe site... which version do I download and what is the terminal... how can I access it?

---

### Post by Liv3dN8as on 2008-10-13
> **lostfate said:**
> One last question... on the adobe site... which version do I download and what is the terminal... how can I access it?

I would d/l the .rpm version. and the terminal can be found in Applications -> Accessories -> Terminal

---

### Post by mrblanco101 on 2008-10-13
check the conections to your disk drive, it should b with your hard disk on that options menu

---

### Post by Ryadt on 2008-10-13
Applications > Accessories > Terminal should give you the terminal.
Here is a guide for the terminal: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Look here if you want to install adobe flash: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

By the way we don't mind the questions. Ask as many as you want, but just start new threads for different questions and mark them solved when you get your solution. ;)

---

### Post by lostfate on 2008-10-13
I am completely new to the linux os but it seems pretty neat... but my Ubunta OS is saying that the .rpm version is not supported... I will try the others

---

### Post by Ryadt on 2008-10-13
Don't use .rpm pakages if you are only starting. Use the synaptic to install packages. 
System > Administration > Synaptic Package Manager.
You might want to install flashplugin-nonfree. Look for it in synaptic and click to install it.

---

