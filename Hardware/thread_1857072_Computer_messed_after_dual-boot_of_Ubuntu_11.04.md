---
title: "Computer messed after dual-boot of Ubuntu 11.04"
date: 2011-10-09
forum: Hardware
---

### Post by Davidtk7 on 2011-10-09
Don't know if this is the right place to put, too confusing for me at this moment because I'm too annoyed which I'll explain why.
 
First of 
I have Acer Aspire M3910-2 Desktop Computer
 
My problem is:
When I had dual-booted Ubuntu 11.04 with Windows 7 which I went through the installation and when it restarted it gave me the grub loader, I try and load windows 7 it loads the boot animation but then the computer just restarts and goes back to the grub loader.
 
I can load Ubuntu which I installed but its horribly wrong
 
my resolution was suppose to be 1440x900 but 1028x 768 is the highest the screen is not positioned correctly, this os looks like a netbook version.
 
Could anyone tell me ....I found under about the os saying..
 
Nautilus 2.32.2.1 - is this a desktop OS or netbook made OS????
 
I SERIOUSLY NEED HELP!!!!! PLZ
PLZ
PLZ
 
And guess wot I try and load the windows 7 disc guess wot, it goes to setup is starting and does nothing else and there seems to be a black boarder on the right side of my screen. Could I made mistake of installing the netbook version!!!?

---

### Post by oldfred on 2011-10-09
Welcome to the forums.

Nautilus is just the name of the file browser.
man nautilus
nautilus - the GNOME File Manager

Man is the command line tool to help with info.
man man
man - an interface to the on-line reference manuals

What video card do you have, with nVidia the proprietary driver works better.

To see if your windows partition is there or what the issue may be run this from Ubuntu or the liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Davidtk7 on 2011-10-09
I have Intel Core i3 - 550
5GB DDR3 Ram
Ati HD 5450

---

### Post by Davidtk7 on 2011-10-09
I actually managed to boot the Ubuntu CD, what can I do to remove the Ubuntu and Grub loader, which is preventing me from using the windows cd  to type
 
bootrec.exe /fixmbr so it follows the boot sequence for windows boot manager.

---

### Post by Davidtk7 on 2011-10-09
Could you please tell me, which Ubuntu I should have downloaded.
 
I have intel CPU which is on my desktop Acer Aspire M3910-2.

---

### Post by oldfred on 2011-10-09
Are you in BIOS or UEFI mode?  Boot script will help tell what is where, you can run from liveCD. The newest systems actually have both and Windows can be installed either way, but it changes a lot of things on how to install Ubuntu.

I usually recommend the 64 bit version for any newer system and more that 2 or 3 GB of RAM. There are only a few speciallized apps that supposedly still only work in 32bit. I use 64 bit on both my 4GB RAM dual core Desktop & 1.5GB dual core 4 year old laptop.

---

