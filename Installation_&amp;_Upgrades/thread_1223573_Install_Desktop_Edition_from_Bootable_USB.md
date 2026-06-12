---
title: "Install Desktop Edition from Bootable USB?"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by Angura on 2009-07-26
Hi there,

i'm having certain troubles installing ubuntu on my notebook.
It has trouble reading DVDs (for a while) and therefore the installation of the desktop edition eventually fails with an I/O error.
However, the installation of the netbook remix via bootable stick doesn't work either. After choosing to install ubuntu Busybox opens and nothing else happens. Although I found some other threads with a similar problem, I haven't found a solution. (Probably because I'm totally new to Ubuntu / Linux operating systems)

So since the Desktop Edition seems to be installable, but fails because of my DVD-Rom, an installation of the Desktop Edition from a bootbable USB would be pretty nice. Is there such a thing? If not, what else could I do to install ubuntu?

Thanks a lot,
Angura

---

### Post by Sef on 2009-07-26
What is your computer and its specs?

---

### Post by Angura on 2009-07-26
It's a Toshiba Satellite A210 (AMD Turion X2 1.9 GHz, 2GB RAM, ATI Radeon HD 2600)

---

### Post by phnhat1984 on 2009-07-26
Maybe this topic can help [http://ubuntuforums.org/showthread.php?t=1223483](http://ubuntuforums.org/showthread.php?t=1223483)

---

### Post by wfvoogd on 2009-07-26
When you have a working ubuntu jaunty desktop on an other computer (or ability to run a live disk), you can use that to create a bootable usb via system->administration->usb startup disk creator. Just point it to a live disk iso image and you're in business. If you don't have another computer, i wouldnt know, i fear...

cheers,

Willem

---

### Post by presence1960 on 2009-07-26
> **wfvoogd said:**
> When you have a working ubuntu jaunty desktop on an other computer (or ability to run a live disk), you can use that to create a bootable usb via system->administration->usb startup disk creator. Just point it to a live disk iso image and you're in business. If you don't have another computer, i wouldnt know, i fear...

cheers,

Willem

not exactly true...

you can do it from windows as long as you download the Ubuntu iso. use [unetbootin for windows]("http://unetbootin.sourceforge.net/")

---

### Post by moster on 2009-07-27
Unetbootin like presence said. I install it every time like that. Just format stick to fat32 and everything will be Ok. Do not just delete everything. Format.

---

### Post by Angura on 2009-07-27
Ok, made a bootable USB of the Desktop Edition with unetbootin.
Unfortunately I still end up at the Busybox command line, so I guess it's a general issue of installation via USB :(

---

### Post by moster on 2009-07-27
Delete everything from USB stick, make new fat32 partition on it. Right click in gparted, manage flags check "boot". Everything in gparted. Then make usb with ubuntu cd or unetbootin program. It must work, I do it all the time. Even vista can install in that way.

edit:
Ok, I see I was not clear enough. Boot with Ubuntu cd. Then plug in USB stick. Open partition editor from system>administration. Then delete partitions and make new one, fat32. Then right click on it select "manage flags" and check "boot". Now save. I think you now must unplug and then plug in back to ubuntu mount it again. Only NOW you can make your USB by running "USB startup disk creator" or untebootin prog.

Wish luck :D

---

### Post by Angura on 2009-07-27
Sorry, but it still doesn't work...

The installation program starts, I can choose to install ubuntu and after a while the loading screen disappears and leaves me with Busybox and [initramf] command line. 

If i wasn't already from the beginning, I'm pretty clueless right now^^

---

### Post by moster on 2009-07-27
It is not DVD and USB :( It is some incompatibility with Ubuntu and your laptop. I understand now.

I will look into it little and edit this post... maybe you need some boot parameters, but huh.. it not feels good.

---

### Post by lisati on 2009-07-27
> **presence1960 said:**
> not exactly true...

you can do it from windows as long as you download the Ubuntu iso. use [unetbootin for windows]("http://unetbootin.sourceforge.net/")

Um errr huh? Since when has booting the live CD used Windows?

Boot up from the Live CD, select "Try Ubuntu without making changes to your computer", and use System->Administration->USB startup disk creator.

---

### Post by moster on 2009-07-27
> **lisati said:**
> Um errr huh? Since when has booting the live CD used Windows?

Boot up from the Live CD, select "Try Ubuntu without making changes to your computer", and use System->Administration->USB startup disk creator.

His USB and CD are fine, he has some other errors. I would check for hardware/memory errors. Load ubuntu cd rom and "test computer" for about an 1 hour. If no errors then I do not know what to say.
This guy said it work.
[https://wiki.edubuntu.org/LaptopTestingTeam/ToshibaSatelliteA210-19B]("https://wiki.edubuntu.org/LaptopTestingTeam/ToshibaSatelliteA210-19B")

---

### Post by NexusZA on 2009-07-28
When you get to the menu screen to chosoe to Install Ubuntu, look for the extra options at the bottom and you should be able to find one to add boot parameters. What you want to add is probably to prevent acpi being loaded. In the boot parameters add at the end of the line:

noacpi acpi=off

I can't check right now how to do it since I am at work and don't have the disk handy to help but that should sort you out.

If you are interested in knowing, older laptops tend to have unique power management features that sometimes aren't so well supported and those boot parameters will tell Ubuntu not to try and load those modules.

---

### Post by presence1960 on 2009-07-28
> **lisati said:**
> Um errr huh? Since when has booting the live CD used Windows?

Boot up from the Live CD, select "Try Ubuntu without making changes to your computer", and use System->Administration->USB startup disk creator.

I was responding to the below quote which told the OP he must have a working Ubuntu install to create a bootable USB:

> When you have a working ubuntu jaunty desktop on an other computer (or ability to run a live disk), you can use that to create a bootable usb via system->administration->usb startup disk creator. Just point it to a live disk iso image and you're in business. If you don't have another computer, i wouldnt know, i fear...

cheers,

Willem

That is so incorrect, you can create a bootable usb with unetbootin on windows: [see here]("http://unetbootin.sourceforge.net/")

maybe reading the progression of posts to this thread will clear that up! Um errr huh? 

P.S. for boot options read this: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Hit F4 at boot and select the appropriate one.

---

### Post by Angura on 2009-07-29
With

noacpi acpi=off

it still didn't work and got additional error messages about some bios-compatibility issues.
I grasped the last straw and installed ubunti with Wubi as a Windows program and it works fine. I think this will be sufficient for me.

Thanks anyway for your hints and advice :)

---

### Post by moster on 2009-07-29
In future, when you got some error you extensively describe what exactly happend. We were obviously headed in wrong way here. If boot post some error of APIC or ACPI, that is totally different from not able too boot from USB or something else.

---

