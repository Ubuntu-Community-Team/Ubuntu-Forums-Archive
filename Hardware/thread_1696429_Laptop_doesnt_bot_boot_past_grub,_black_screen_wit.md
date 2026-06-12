---
title: "Laptop doesnt bot boot past grub, black screen with blinking cursor"
date: 2011-02-27
forum: Hardware
---

### Post by wardy277 on 2011-02-27
I booted up my laptop this morning but it refused to boot. Now this happens from time to time and just needs rebooting and all is well. But not on this case.

I have just Ubuntu 10.10 running so the only options in grub are all the ubuntu kernels and recovery options. No matter which ones i choose i always get the same result, a blinking cursor after a few seconds. I have tried running in recovery mode, i get a load of text then it stops. i have attached a few pictures as it stops at different times.

I have tried booting from live cd but that does the same, blinking cursor after the ubuntu boot menu (with the purple background).I have dried removing both the hard drives(it has to bays), unplugged everything usb, i even removed the wifi and the ram one by one.

I have tried running an old windows commander which did the same thing. Are there any wasy to get into the command line from a live cd? i cant even do ctrl+alt+f1. 

Is my laptop completely broken?

Its a HP dv9700, 4Gb Ram, Nvidia graphocs card running Ubuntu 10.10

---

### Post by wardy277 on 2011-02-28
Anyone any ideas?

---

### Post by wardy277 on 2011-02-28
Bump

---

### Post by altometer on 2011-02-28
This happens to me when the boot device is slow. 

1) where is Ubuntu installed?
2) how long have you allowed it to stay at this screen?
3) when did you install
4) What version of ubuntu did you install?
5) can you boot the live cd to command line?

---

### Post by wardy277 on 2011-02-28
I have ubuntu installed in the primary hrive with a seperate partition for /home
I have tried leaving it at the screen or over an hour and it didnt change
I installed ubuntu over a year ago, i upgraded to 10.10 when it came out and it it has been working fine since. It even worked no problem the day before.
It is currently runnign Ubuntu 10.10 64Bit (as is the live cd)
I cannot boot to command line through the live cd. I tried advance options and removed the splash and quiet btu it get stuck as the same screen as booting from the disk

It wont even reboot with ctrl+alt+delete, same as any key combinations i can think of, it just does nothing.

---

### Post by altometer on 2011-02-28
Can you boot to mini-xp via hiren's boot cd?

Can you try the following;
1)Remove both Hard Drives
2)Change the bios settings to reflect this
3)Plug in a USB drive that is atleast 4 GB in size.
4)Attempt to boot to the live CD

If you have another computer, try re-downloading and burning a copy of the live CD.

---

### Post by wardy277 on 2011-02-28
BINGO! Mini-Xp actualy booted!

It cant see the drives as they are both ext4 but the device manager does pick them both up under their correct model numbers

what can i do now to see why ubuntu didnt boot?

I have tried 2 dirrefent live cds that do worth on other pcs

---

### Post by altometer on 2011-03-01
okay, so mini xp booted. That "can" be telling us several things.

It's not the motherboard,cpu,memory,or a wierd fan issue. 

Do you have another cd/dvd drive available? 
What method was used to create your boot disc? 

If possible, can you try creating a usb-install disc for ubuntu?
"use [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/")"

So far, I am not sure what is stopping you from being able to log into ubuntu, but we are working on getting you at least, in a linux environment.

---

### Post by FoxEWolf on 2011-03-01
Is this the first attempt booting up after install? It is a different problem if you were able to boot into 10.10 before, but if this is the first time it may just be the result of an error during installation. If possible try booting and restoring via LiveCD.

---

### Post by wardy277 on 2011-03-01
Thanks for your help with this. I managed to boot into the mini xp via cd so i am sure the cd drive is fine, but just incase i did dig out an old laptop dvd drive and switched them, but only go the same message.

I tried booting, ubuntu, linux mint and damm small linux, all from usb, all of which failed in the same way.

I dont know if this effects anything, but i do remember before it breaking i was running ubuntu with a usb mouse, i put it intp standby. later i removed the usb mouse and then resumed ubuntu. it did work for a few hours fine but then when i turned it off (shutdown) and then booted up thats where i got the problem.

I have 3 usb ports on my laptop. When i boot the live cd and remove quiet and splash, i see the console output as in the pictures above. Every time it boots it seems to stop at [2.9...], but when i boot from usb and the usb is in the same usb port as the mouse was (probably coincidental) it gets to [3.0....] before frezing. I took the laptop apart and found out that this usb port was corrected by a 4 pin plug connecting to the motherboard. on a long shot i unplugged it and tried to boot but got the same issue.

oddly the above pictures are booting from the hdd which only got to [0.7...] but the live cd gets to [2.9...]. i guess these numbers represent boot levels? what happens at 3? is some sort of hardware activated?

---

### Post by altometer on 2011-03-02
not sure. How odd that you can't even boot to usb though :/ see if there is a new version of your bios available and use mini-xp to install it.

I am on aim all day, so if you want you can message me.

---

### Post by wardy277 on 2011-03-02
thank you for your help. I have tried to upgrade the bios but it doesnt seem to work within mini xp

the download is:
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-90466-1&lc=en&dlc=en&cc=uk&os=228&product=3263330&sw_lang=](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-90466-1&lc=en&dlc=en&cc=uk&os=228&product=3263330&sw_lang=)

i tried running it from a usb drive and installing it to b:/ but when it ran it said "windows can not open this file b:\Temp\quanta.vbe, then asks me to browse for the program to open it. if i click the x it bring up the flash program but says: "The input file "BIOS.WPH" can not be found. A valid filename must be specified to continue"

any idea? can i flash the bios via command line or a hp boot disk? i did notice the other option in minixp to boot from cd, which gave a load of command line programs, can i do it through there

---

### Post by wardy277 on 2011-03-02
OK scratch that, i amanager to upgrade the BIOS to the latest version. I havd to manualy find the WPH and move it to the bios flash directory.

So, now i have the latest BIOS, i still get the same problem. Very frustrating now. Would taking it to a laptop repair shop be worth it? would they be able to do anything more than what we are doing?

---

### Post by wardy277 on 2011-03-02
I have tried installing some other isos to the usb drive, Gparted didnt boot bast [0.7...] but damn small linux did boot into a graphical enviroment. The mouse didnt work, and i couldnt manage to mount any partitions but it did boot, which was strange.

I have noticed that the side USB ports have stopped working completely, do you reacon that it could be related?

---

