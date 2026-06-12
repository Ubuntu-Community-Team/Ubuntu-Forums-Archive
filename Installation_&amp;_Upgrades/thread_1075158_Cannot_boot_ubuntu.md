---
title: "Cannot boot ubuntu"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by jkimball on 2009-02-20
Hi,

I've been scanning the forums for some time now and haven't come across a similar problem to mine.

I have installed a dual boot system with the first OS being Windows XP (existed) and the second being ubuntu. 

Every time I try to run ubuntu from the CD, or install it, my computer will restart right after the loading screen reaches 100% (the screen with just the ubuntu logo and the progress bar). I've tried two discs with two fresh installs and neither worked.

I've successfully installed ubuntu using the text-based installation (8.10-alternate) and it processed all the way. I still get the same problem when I try to boot. I CAN get to the command prompt though using the recovery mode boot from the grub. 

I'm not sure where to go from here. Something with the xorg.conf file maybe? (not sure how to open/edit it with out graphics display - I'm new to linux :D ).

--Computer Specs--
GPU: NVIDIA GeForce 8800gt
RAM: 2g
Processor: Dual Core AMD Opteron 170 (~2.8GHz)
Ubuntu Partition space: 10.2gb

Thanks for all of your input/advice!

p.s. I'm going to bed now so I won't be tending to this post for another 9 hours.

---

### Post by staf0048 on 2009-02-20
It sounds to me your graphics card is causing the problems and it may very well be fixed by changing the Xorg.conf file, but that is becoming less and less common.

So, if I were you I'd check to see if anyone else with the exact same graphics card has posted information on their Xorg.conf file configuration in either these forums or on the net.  

If you find something, print it out and boot your computer into the command prompt and type

Code:
sudo nano /etc/X11/xorg.conf

The file should open in the command line and you can arrow through the document to find what information needs to be changed.  Use Ctrl-x to save and exit.  Then try rebooting and see if it works.

---

### Post by jkimball on 2009-02-20
Great! I will hunt around and try to find a solution. 

Thanks for the advice!

---

### Post by staf0048 on 2009-02-20
If that doesn't work you could try getting an updated driver directly from nVidia's website.  

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

If you use your Windows side of the computer it should automatically detect the proper card, just make sure to switch the operating system to Linux instead of Windows.  

Download the file and copy to CD or USB.  

Note the instructions on how to start the installer.

Back in Ubuntu, get to the command line and type

```
cd /dev
```

This will get you to the directory where your CD-ROM/USB connects to the filesystem.

If you type:

```
dir
```

or 

```
ls
```

it will give you a listing of all the devices connected to your computer.  Depending on which media you used to copy the driver just use the "cd" command to now change to that directory.  Such as:

```
cd cdrom
```

Be sure to enter any numbers after "cdrom" if they're included, like "cdrom0."  If you only have 1 drive it should be fairly easy, but if you have two or more you'll have to use the "dir" or "ls" commands again to make sure your in the drive that has the new driver.  If you need to back up to get to a different drive type:

```
cd /dev
```

That will get you to where you need to be to start the installer.  Follow nVidia's instructions from there and hopefully it will fix your issue.

---

### Post by jkimball on 2009-02-22
Ok, so heres an update on my situation. I used 
```
sudo nano /etc/X11/xorg.conf
```
to open up my xorg file and it was empty. This morning i just turned on my computer and went away for about 20 minutes so the comp must have been repeatedly booting into linux (since its the first choice on the grub menu) and it actually started on one of the tries. 

It must have taken about 10 tries because I tried recreating the event by trying to boot 5 times but it still kept restarting. The problem I had when it did start was that the mouse and keyboard didn't work (1 is on a USB port and the other is on a PS2). 

Does this spark any ideas?

---

### Post by staf0048 on 2009-02-22
Hmmm - when you tried to bring up your xorg.conf file to you captalize X11?  Linux is cases sensative, so /etc/X11/xorg.conf is different than /etc/x11/xorg.conf.  If you used the lowercase "x" you will get an empty file.

What happens if you boot the system without your mouse and/or keyboard atatched?  I don't know if this would cause your system to act like it does, but it is possible that either one or both of the devices are causing errors.  I doubt it will make a difference, but it's a place to start.  I honestly have never run into this type of issue before.

---

### Post by linux_tech on 2009-02-22
If you look in /etc/X11/   there are usually a few different 
xorg.conf files.  Often you can rename a different xorg to xorg.conf
to make it the current xorg  and use it

---

### Post by karthie on 2009-02-22
hi
i got the new version ubuntu 8.0 from the web i have got it installed successfully.
when i tried to configure my ekiga soft phone it siad that i have a problem with sound driver so i tried to un install the default sound driver in ubuntu 8.0 and reinstall it but when i uninstalled it i could not get back in to the GNOME screen of the ubuntu i have even tried the recovery mode.I came across this post an now posting my problem which is similar to what jkim have mentioned in his post i can get in to the command prompt and work i even tried to get connected to internet through the command prompt but in vain. The moment i boot my system it is telling that GRUB lloading stage 2 and then displays the hard drive details. After that it says cannot find the image for normal boot and then getting me to the command prompt (terminal window).I have also tried to reistall ubuntu through the cd i have with me no use if any ideas just let me know it would be helpful. But the thing is when i type startx command in the terminal window after login it takes me to the server editon GNOME window. For your information i dont have dual boot i have one hard drive assigned completely to linux ubuntu.
thank you 

thank you

---

### Post by staf0048 on 2009-02-22
To jkimball,

If none of the options listed gets you anywhere, you'll need to take a look at whats going on during the boot process to see if you can identify what's wrong.  I can't think of a way for you to post a log file here with only command line access to the system though.

To see what the system is doing, once you get to the initial Ubuntu splash screen (just after grub) type Alt-F2.  That will let you see what is happening during boot.  On the left of the screen are the services the system is trying to start and on the right there is normally [OK] after all of them.  Hopefully this will help you pinpoint where the system is breaking.

For even more verbose information you can try booting in recovery mode, but this can be difficult to read because the text goes by really fast.

Keep at it and good luck!

---

### Post by staf0048 on 2009-02-22
To karthie,

You can try anything you've see here to help get more information on your issue, but if you had it working fine at one point, then a totally fresh install should have got you back up and running.  I'm at a loss of ideas as to why it didn't, unless something went wrong with your hardware in the intirum.  You could try re-installing again as it is possible that something went wrong on the 2nd go round.

---

### Post by karthie on 2009-02-23
hey 
thanks i tried to re install a fresh copy but when i change my boot mode and boot through the cd is not booting from the cd is loading in similar way one just the screen with grub boot loading then it says image not found for normal boot and entering in the terminal. i have tried to doenload a fresh copy and did it from ubuntu site. But that copy also has the same files as in my CD is there any special procedure to install a fresh ubuntu on existing one if so kindly point me the link
thank you

---

