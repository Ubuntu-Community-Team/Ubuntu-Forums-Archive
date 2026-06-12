---
title: "HP PSC1210 Strange Issue with USB Detection"
date: 2005-08-30
forum: Hardware &amp; Laptops
---

### Post by Zachs23 on 2005-08-30
First off, as you can tell by my post count, im a linux newbie, so be nice  :) .
I have a HP PSC1210 printer. I followed the directions exactly as the instructions on [http://hpinkjet.sourceforge.net/](http://hpinkjet.sourceforge.net/) for Debian. The point is, all of the drivers are installed correctly (To the best of my knowledge). Since I cannot use the CUPS web configuration in Ubuntu (is this a personal problem, or is it disabled for some reason?), I tried using the Gnome Printer Manager to add the printer. I tried it a few different ways. The printer was never automatically detected, so I tried selecting each usb port manually, then selected PTAL DEVICE NOT FOUND. Each time, it "adds the printer successfully", but does not print or communicate at all. Now here is the interesting part, when typing "lsusb" in the terminal (which, to my knowledge, lists all of the usb ports) here is the output:
```

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c01d Logitech, Inc. (My Mouse)
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0451:e001 Texas Instruments, Inc. GraphLink (The Printer)
Bus 001 Device 001: ID 0000:0000

```
Obviously, my printer is not a texas instruments graphing calculator. So this is where I am stuck, and ask for your help. What is the issue? Would enabling the CUPS web interface make any difference? If so, how would I do that?
Thanks A Lot

---

### Post by matthew on 2005-08-30
I have the same printer you do. I was able originally to get the printing to work, but not the scanning. I am now able to do everything. Here's the thread where my problems got solved. Maybe it will help you out.

[http://www.ubuntuforums.org/showthread.php?t=49288](http://www.ubuntuforums.org/showthread.php?t=49288)

---

### Post by Zachs23 on 2005-08-30
Thanks for the reply, but I havent even gotten printing working yet. What did you have to do (If anything) to get printing to work with your system?

---

### Post by matthew on 2005-08-30
Use Synaptic to install these:
hpijs
hplip
hplip-base
hplip-data

It may say that something else needs to be removed (like hpoj). That is okay. hplip is the driver that I am using as well as the driver that is recommended on the HP web site you noted earlier.

Once these are installed, just for good measure turn the printer off and restart your computer.

After the computer has finished booting, turn the printer on. It should work. To test it open your favorite word processor and print something small.

If that works for you (I think it will), then we can get the scanner to work.

---

### Post by Zachs23 on 2005-08-31
Thanks for the reply, here is what happened:
I followed your directions exactly, except for the fact that I could not find a "hplip-base" in Synaptic. I then turned the printer off and shut down the computer. After turned on the computer and logging in, I turned on the Printer again. Here, do I have to install the Printer using the Gnome Printer Manager (I'm assuming yes)? So frist I tried printing without installing it, it obviously did'nt work. Then, I tried installing it, but it was still not automatically detected. I selected the usb port that the printer was plugged into (still showing up as Graphlink when I type lsusb). I notice there is now no driver for my model. So, my question is, how do you set up the printer after the driver is installed?

P.S. I will be out of town for a few days, I don't know if I will have internet access. If not, I will reply to your response in a few days.

---

### Post by matthew on 2005-08-31
Sorry, it's been a few months since I got this up and running and so I'm trying to recreate the process...yes, we will have to install the printer. By the way, the Hplip Toolbox (that probably installed in your System->Preferences menu has never worked for me and still says that there is no printer installed. Just ignore the toolbox program.

Try this:
1) Make sure you have the extra repositories enabled as shown here: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2) try again in Synaptic to install the hplip-base (it's in the backports) as well as hpijs (which I apologize for having forgotten the first time...this is probably going to be the key)
3) reboot (probably not needed) and turn the printer off and back on.
4) System->Administration->Printing will open the Printers dialog box.
In it select Printer->Add Printer The printer should have detected this time and it should be in the list ready to be set up.

If it isn't, select File->Add Printer. If the printer is plugged in to the usb port and if it is on it should be detected and listed. Select it and click next and then find PSC-1210  in the list.

It should be pretty self-explanatory from there. I'm sorry I forgot the hpijs driver last time. That is probably all you need. If you can't get hplip-base I wouldn't worry about it, it probably isn't being used. I just took a look and gave you a list of everything I have installed since my psc-1210 is working.

---

### Post by mbjbdc on 2005-08-31
hpoj works good too
after installing run terminal sudo ptal-init setup reboot and ptal device should be the unplug printer also make sure xsane is installed
also hplip will not work unless xsane is installed

---

### Post by Zachs23 on 2005-08-31
Thanks for the reply. I am out-of-town, so I don't have access to the printer. I did, however, add the backports, and install hplip-base. I will try installing the printer on Sunday.
Thanks for all of the help!

---

### Post by matthew on 2005-09-01
You are welcome. Hope you have a good trip and we will hear from you when you get back and have time to try it out.

---

### Post by Zachs23 on 2005-09-04
Hi, I'm back. Unfortunately, it still does not work. Same errors as in the first post.

---

### Post by matthew on 2005-09-04
Bummer. This must be getting frustrating for you. I'm really not sure where to go from here. Let me think for a bit and see if I can think of anything else that might help. In the meanwhile I would invite anyone else who has an idea to please contribute it.

---

### Post by Zachs23 on 2005-09-04
Thanks for the help anyway, and let me know if you think of anything else.

---

### Post by matthew on 2005-09-04
Here are some links I found, maybe something will stick out to you.

This guy got his working with Ubuntu...about halfway down the page:
[http://usalug.org/phpBB2/viewtopic....bb5351ff0653fe9](http://usalug.org/phpBB2/viewtopic....bb5351ff0653fe9)

Here's a link to setting up a psc1210 at a page dedicated to linux printing:
[http://www.linuxprinting.org/show_p...num=HP-PSC_1210](http://www.linuxprinting.org/show_p...num=HP-PSC_1210)

You have probably seen that this page says it should work for scanning and printing with no special configuration...obviously that isn't the case for you right now.
[https://wiki.ubuntu.com/HardwareSup...ponentsPrinters](https://wiki.ubuntu.com/HardwareSup...ponentsPrinters)

Say, that makes me wonder, what is your setup? Tell me everything you can about hardware.

---

### Post by Zachs23 on 2005-09-04
Here are my comp specs:
Vaio Notebook PCG-FRV31
Video: Radeon IGP 345m (using default ati driver, 2d acceleration only, i've been trying to get 3d acceleration in ubuntu for a while, worked in suse, but not ubuntu)
512 RAM (Shared with video card)
2.4 Ghz Processor
40 GB HD (Only Ubuntu, no dual-booting)
Wireless Networking:
Linksys WPC11 Ver. 4 Using NDISwrapper
Thats all I can think of for now, thanks.

---

### Post by matthew on 2005-09-04
Okay, I don't see anything unusual or rare in your setup that could cause conflicts. I hate to admit it, but I am fresh out of ideas. Hopefully someone else will jump in here. Sorry.

---

### Post by matthew on 2005-09-05
With no more ideas of my own I thought you might appreciate a referral...maybe someone in these forums will be able to figure out your problem.

[http://www.linuxprinting.org/forums.cgi?group=linuxprinting.hp.general](http://www.linuxprinting.org/forums.cgi?group=linuxprinting.hp.general)

---

