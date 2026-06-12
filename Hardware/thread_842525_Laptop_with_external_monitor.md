---
title: "Laptop with external monitor"
date: 2008-06-27
forum: Hardware
---

### Post by Bosnoval on 2008-06-27
* Total Ubuntu Newb *

I just installed Ubuntu 8.04 on a Dell Inspiron E1505 that has an NVidia 7300 Go video chipset.  Everything installed okay but I can’t figure out how to get an image to my connected LCD monitor (Samsung 226BW).  

The only info I’ve been able to find on the topic suggested installing the proprietary NVidia ‘new driver’ and then using the included NVidia utility.  I had already installed the driver but I can’t find a utility if one was in fact installed with the driver.  

The system menu does have a ‘resolution’ app that has ‘clone’ and ‘detect displays’ options but neither works.

---

### Post by starcannon on 2008-06-27
I don't have a "fix" for this, only a work-around that I use.

At post, or at the Grub screen I cycle my laptop through its connections using its FN key combo, I have several laptops each one is different. They all cycle similarly thought, as I click through I can have "Just the Laptop Monitor" or "Just the External Monitor" or "Both the Laptop Monitor and the External Monitor". Then I continue booting and it works fine, I would like to be able to toggle through the options from the desktop but have not put any time into finding out how as my work around takes care of it for me (yeah I'm a lazy piece of bass fecies lol)

Anyway hope that helps for now.

GL

---

### Post by Bosnoval on 2008-06-27
I gave this a shot and it worked somewhat at the “Grub screen” but only there.  I could shift the image back and forth between the monitors but not to both.  However, once I selected to boot into Ubuntu it defaulted back to my laptop’s screen and again turned off my other monitor.

Under every other OS I’ve used though the FN sequence has worked, so thanks for trying! 

Anyone else have a clue?

---

### Post by Bosnoval on 2008-06-30
Still unresolved and found similar thread:

[http://ubuntuforums.org/showthread.php?t=776671](http://ubuntuforums.org/showthread.php?t=776671)

I'm fairly certain Ubuntu is detecting my laptop's screen incorrectly too as it has it running at 50 Hertz instead of the Windows usual of 60 Hertz.  The "resolution" menu should just be removed if it's really this broken.

Thanks in advance to anyone that has a clue! =D

---

### Post by Bosnoval on 2008-07-16
Found this thread:

[http://ubuntuforums.org/showthread.php?t=848368]("http://ubuntuforums.org/showthread.php?t=848368")

Somewhat unrelated situation but tried out the command:

```

gksudo displayconfig-gtk

```

After seeing in the subsequent configuration messages that there was even an exact match for my external monitor, listed explicitly as a "Samsung SyncMaster 226BW (Analog)", I thought I would finally resolve this issue; nope!  The system rebooted and came back with only a black screen.  I had to reboot again and luckily the system came back normal on my laptop and even initialized my external monitor for the first time.  However, the external monitor must be set to some ridiculous resolution like 320x240 because the word "Application" in the top menu takes up the entire screen. So, I'm basically back to square one again.

---

### Post by Zensane on 2008-07-16
I have the exact same issue.  I have found that if I use the "NVIDIA" driver I can only use my laptop screen, but if i revert back the generic driver, everything works fine, but I cant use all the advance graphics with XGL without the NVIDIA drivers.

It has been a while since I have used any flavor of linux, but I know if has something to do with the configuration of one of the config.conf files, but not sure which.

---

### Post by rohan182 on 2008-07-17
im having the exact same problem except i cant get it to work at all.. im about to go try that sudo command see what happens. 

it sucks cause i barely use my laptop monitor as my laptop is more of a desktop replacement..

i have an Nvidia 9500M GS (512Mb).

i just want to use my external monitor :(

---

