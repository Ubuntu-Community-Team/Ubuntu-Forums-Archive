---
title: "Noob - Problems after install: blank screen when running Ubuntu."
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by escarf on 2009-04-19
I just installed Ubuntu 8.10.  I installed it as a dual boot with XP, which had been running on this computer for years.  The installation process seemed to run fine, including creating the partition.  When I turn on the computer, I now get a screen that allows me dual booting options, and XP runs fine.  Unfortunately, Ubuntu boots, seems to load the driver for the mouse, and then stops.  All I get is a working mouse and a blank screen - nothing more.  I've tried booting in safe mood and I receive messages saying that everything has loaded properly, and I've run the memory test, also without problems.

I'd appreciate any help anyone could offer.  Thanks.

---

### Post by upchucky on 2009-04-19
I just need to clarify what you said, did you mean you have been running ubuntu for years? or running windows for years? or both for years?

either way we need to know if the 8.10 live cd actually booted up to a graphical desktop before you actually did the install, I suspect it did not.

If in fact the live cd does boot up to a graphical desktop then you only need to experiment with resolution and display settings in your xorg.conf file.

you will need to find others that have the same hardware and use their settings, or use version 8.04 which in all likely-hood has the right settings for your hardware.

8.10 is not a long term supported release, where 8.04 is a long term supported release and so it most likely has everything it needs for most hardware.

---

### Post by escarf on 2009-04-19
Thanks for your message.  I only meant that XP has been running for years on this computer.  The Ubuntu is a brand new installation.  The live cd booted to the installation program, which was very easy to see and follow.  I went through each screen in the installation program until I received the message telling me that the installation was complete and the computer needed to be re-started.  When I restarted the computer, I never did see the Ubuntu desktop, beyond seeing "Ubuntu" across the screen and the orange bar showing the OS's progress in loading.

Are you suggesting that I install 8.04 instead of 8.10.  If so, can I install it over 8.10?

I've booted XP and checked the disk management.  It shows the partition that I created during the installation of 8.10.

---

### Post by JK3mp on 2009-04-19
I think what he want's is if you havn't already tried to boot to the live GUI, to try that now. NOT on your install , LIVE off the disc. If it does boot, its just your xorg.conf file. And its never a good method to install b4 doing a live boot first and figuring through all the issue's as far as hardware compatability etc.

---

### Post by The_SoDak on 2009-04-20
Help others help you! ;) 

The Code of Conduct says:
> Try to give information in the title of your post, instead of using a title like "it's broken," use a title that is specific, such as, "Unable to get sound to play in Firefox." A clear title will attract more views to your thread, as it gives a clear indication of the content of the post to the people that are willing to help you. Ultimately this will allow you to get more help of a better quality.

So please, use descriptive titles and provide as much information as possible. We are here to help, you just have to let us. Good luck!

---

### Post by tommcd on 2009-04-20
Escarf,
It does sound like your video (xorg) is screwed up. What kind of motherboard chipset and video card does your computer have?
Also, can you boot from the live CD, then open a terminal (applications > accessories > terminal) and run:
```
lspci
```
and:
```
lspci -v | grep -i vga
``` 
And post the output here. The first command will list your all your pci devices. The second command will give some detail about your video card.

You can also try to boot to recovery mode and run:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg
```
The first command will back up your xorg.conf. The second command will walk you through reconfiguring xorg.conf. You can likely select the chosen defaults if you don't know all the answers. It is helpful to have your monitor specs on hand when doing this.
Then just "sudo reboot" and see if you can get to the desktop.

And welcome to the Ubuntu forums!

---

### Post by bapoumba on 2009-04-20
I have edited the title of the thread.

---

### Post by escarf on 2009-04-20
I was able to boot from the CD and see the desktop and get to the applications, but only if I selected "safe graphics mode" at the start of the boot.  If I do not choose this option and boot from the CD, I only get an orange screen.

I ran the codes you suggested, and went through the sequence of configuring xorg.conf.  Unfortunately, this did not solve the problem.  Instead, I now don't see an orange screen or the mouse pointer when I boot from the hard drive - just a blank screen.

I also ran the codes to get the data on the board, chipset and VGA device.  Since the computer is not hooked to the internet, I can't cut and paste it into this message.  This an old inexpensive computer, so there's no video card, just integrated graphics: VGA compatible controller: Intel Corporation 82845G/GL [Brookdale G]/GE Chipset Integrated Graphics Device (rev 03).

The data from running lspci included: A number of USB controllers: Intel Corp 82801DB/DBL/DBM (ICH$/ICH4-ICH4-M).
PCI bridge: Intel Corporation 82801 PCI Bridge.  There was also information about the ISA bridge and the IDE interface, but I don't think that's relevant to this problem.

So, it appears that everyone is right about the graphics being the problem.  Any suggestions about where I go from here?  I really like what little I saw when I booted from the CD.  I'd like to get this OS up and running from the hard drive.

Thanks.

---

### Post by tommcd on 2009-04-20
When you booted to recovery mode and ran: **sudo dpkg-reconfigure xserver-xorg**, do you remember what video driver it chose? The Intel chipset and integrated Intel graphics should work ok in linux. Try booting to recovery mode again, choose the option to drop to a terminal, and run:
```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg

```
 Choose **intel** for the graphics driver. If it suggests **i810** instead of intel then go with that. Also, be sure to select valid horizontal and vertical refresh rates for your monitor. Then reboot.

If that does not work, then boot to recovery mode again and choose the option **xfix fix video**, or whatever it says. Then reboot.

---

### Post by bobidybob on 2009-04-21
I'm having the exact same problem as escarf. I also have the exact same graphics controller. when i run 

```
sudo dpkg-reconfigure xserver-xorg
```

all i get is a question about a framebuffer and a bunch of keyboard questions. it doesnt give me any options about picking a graphics driver.

EDIT: i've also tried all the suggestions in this thread with no success

---

### Post by escarf on 2009-04-21
bobidybob has it exactly right.  I never get an option that allows me to pick a graphics driver.  When I ran the strings tommcd suggested I received a message telling me that I needed to download certain wireless drivers, with the address of a website that contained the Broadcom wireless driver I needed.  Unfortunately,this appears to have nothing to do with my graphics problem.

Any suggestions?  

Thanks for the help, everybody.

---

### Post by tommcd on 2009-04-21
It has been a long time since I had to run "sudo dpkg-reconfigure xserver-xorg". As I recall, it used to include the option for selecting the graphics driver.

Try booting to recovery mode again and run the command as described in this link with the -phigh switch:
[https://help.ubuntu.com/community/XDisaster](https://help.ubuntu.com/community/XDisaster)
If that does not help, then boot to recovery mode again and choose the option "x fix fix video" or whatever it says.

---

### Post by escarf on 2009-04-22
Unfortunately, the -phigh switch did not work.  When I boot in the recovery  mode, I don't get a choice that allows me to select "x fix fix video" or anything similar.  In fact, when I boot to recovery mode, after it goes through recovery, I don't get any choices that allow me to run commands.

I guess it looks like I'm out of luck.  Too bad, because I'm sure tired of the nonsense Mr. Gates and the Redmond Crew foists on PC users.

---

