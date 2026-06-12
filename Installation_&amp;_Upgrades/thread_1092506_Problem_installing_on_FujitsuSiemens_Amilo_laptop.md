---
title: "Problem installing on Fujitsu/Siemens Amilo laptop"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by vangelisf on 2009-03-10
Hello everyone! I've posted this message on Laptop section too.

I am new to the board and I want to install ubuntu to my laptop. I have seen that Linux is light years ahead of Windows and I want to switch to this operating system. As for the window games etc I think I'll just use VirtualBox with Win XP but that's just in case.

Anyway, I'd like to get straight away into my issue instead of spending your time... 

My laptop is the:

Fujitsu/Siemens Amilo Pa 3553
AMD Turion X2 64
ATI Radeon HD 3470 Hybrid x2

I tried to install Ubuntu 810 Ultimate Edition 2.1 (for x86 systems) and I got a message about a problem regarding the X server configuration about the graphical interface. There was an option to view a long log file etc.

I then tried to install it on an Acer laptop with Intel Core 2 Duo T7200 and NVidia GeForce and went completely fine.

So, is the hardware my problem or should I do any configurations to run it? Should I download the 64 edition of Ubuntu Ultimate from the beginning?

I would be grateful if you could help me because I really want to get rid of Windows....

Thank you very much in advance for your time!

Vangelis

Edit:

I tried it again and have written down some of the messages if that helps...

The first message is:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"


The 1st output had some lines about the Linux version etc and in the end had these among some other code lines:

"Primary device is not PCI.

No devices detected.

Fatal server error:
no screens found."


The detailed output had the following lines again among some other code-like lines:

"VESA: driver for vesa chipset: vesa
Primare Device is: (nothing here)

Falling back to old probe method for vesa.

No devices detected.

Fatal server error:
no screens found."

Thanks again!!!

---

### Post by Slameth on 2009-03-28
:KS BUMP :KS

Can anyone help with this? I've got the same problem, though I have dual nVidia cards. Xserver finds both but gives the same error Vangelisf here is getting. This right after I update. The first boot of Ubuntu UE 2.1 works fine, after that, I can't get back into the OS. I've done much searching, and found it's the updated Xserver-xorg-core, as it was happening on Suse and many other distro's. What I haven't found is the methods of "fixing" the problem with Ubuntu that will work. I'm still a linux/ubuntu beginner and don't know what comes as second nature to some of you. :)

I've done: >sudo dpkg-reconfigure xserver-xorg
I get: absolutely nothing about video other than one buffering option (wich didn't work iether). Every other config question was about the keyboard.

I also found this that some say will fix the problem. 
>>sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10.4
>>sudo shutdown -r now

But it goes reading - (un)packing - then fails at the last part. I don't understand the last part of the first entry line. Is it installing the Xserver-xorg-core as 1.0.2-0ubuntu10.4 file name or is that the core file name that it installs from. Perhaps I have the file name incorrect. Alas, it fails.  

Any help for a newbie enthusiast?

---

### Post by Mark Phelps on 2009-03-28
I have a fujitsu tablet PC and my recent upgrade from Hardy to Intrepid did not go well.  Stuff that used to work in Hardy just fine no longer works in Intrepid.  Among the things they changed was how xorg.conf works such that virtually NONE of my tablet functions worked anymore.

It's discourgaging when they update things and don't provide any sort of conversion routine for that.  I spent a lot of time getting my tablet functions working in Hardy.  Don't know that I want to invest that much time just to get the same functions in Intrepid.

So, since you have a siemens-fujitsu laptop, you might try loading Hardy instead.

---

