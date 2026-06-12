---
title: "Messed up fresh installation of 8.04"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by hevdaze on 2009-06-23
I own a dell mini 10v, and I was trying to do a fresh installation of 8.04 with a CD I created using the .iso file I downloaded from the Ubuntu site.  I am using an external iomega cd drive, which connects via usb.  I started the mini and booted with the cd, and all went well.  then, as the system was installing, I minimized the installation progress window and could not get it back.  Soon after, the mouse froze, so I held down the power key to turn it off.  Thinking i could simply restart the installation as I had before, I turned on the computer and selected CD drive from the boot options list.  However, instead of getting the Ubuntu installation screen as I had before, I now get MBR: FA.  I tried pressing A and then 1, however, that did not work.  I am afraid my Mini 10v is just going to become a block.  Is there any way to get Ubuntu back up and running??

---

### Post by mk1w86 on 2009-06-24
Make sure your computer is set to boot from the CD first.

---

### Post by hevdaze on 2009-06-24
I made sure I selected boot from CD/RW on the boot menu, however, the screen still shows the MBR:FA command.

---

### Post by starcannon on 2009-06-24
I think it may still be attempting to boot from the hdd/ssd, I would likely unplug, pull the battery, push the power button with battery out and power disconnected, wait 5 minutes, reboot, go into boot order screen (generally rapid firing *Esc* on most computers right after you turn it on) Choose the External USB Device your using, and try again.

[http://ubuntuforums.org/showthread.php?p=6974386](http://ubuntuforums.org/showthread.php?p=6974386)

I'll do some more googling, but I don't think your bricked, maybe a tedious solve, but I think your mini10 will be fine in the end.

Edit:
I'll continue to add more links on this here:
[http://stezz.blogspot.com/2007/11/debian-etch-on-thinkpad-x31-via-usb.html](http://stezz.blogspot.com/2007/11/debian-etch-on-thinkpad-x31-via-usb.html)

From:[http://www.entropicblur.com/dectop/guide.html](http://www.entropicblur.com/dectop/guide.html)
```

**The Installation Process**

  Installing Xubuntu to the decTOP is much like installing on any other PC and the process is much simpler under 7.10 than under 7.04, but there's still one quirk to work around. This is explained below.
  After the decTOP completes its self-tests, you'll see this prompt:[INDENT]MBR FA:[/INDENT]Press the "a" key and the prompt will change to:[INDENT]MBR 1234F:[/INDENT]Press the "1" key and the system should boot into the text-based installer.
  Follow the prompts to start the installation. The process is fairly self-explanatory and the Ubuntu team has good documentation available [here]("https://help.ubuntu.com/7.04/installation-guide/i386/"). Everything should go smoothly up until the kernel installation stage.
  Eventually, the installer will complain that "No installable kernel was found in the defined APT sources" and will ask if you want to continue without a kernel. Instead of answering the prompt, press Alt+F2 to switch to a console. Press Enter to activate the console, and then:[INDENT]chroot /target
apt-get install linux-generic[/INDENT]Once the kernel installation is complete, exit twice, once to leave the chroot and again to leave the console. Press Alt+F1 to switch back to the installer. Answer "Yes" to the "Continue without installing a kernel?" question. The installer picks up where it left off and eventually gives you the option of installing the Xubuntu desktop package; go ahead and install it.
  The rest of the installation is smooth sailing; just sit back and wait until the installer tells you to reboot. Be sure to disconnect the flash drive so the system starts up from the hard drive.

```Okay after reading a bunch of posts on the subject, I think its not recognizing the CD, and then attempting to boot the next in line; in this case, the failed install from the hdd/ssd. My advice is to rinse repeat until the media in the external CDdrive is recognized, or build a bootable USB Key; I've personally got 2 computers that can be a bit finicky about booting from an External USB CD/DVD drive, though they always seem to boot from a bootable USB Key, go figure.

---

### Post by hevdaze on 2009-06-25
Thank you for all you help.  However, none of this seems to be working.  I created a usb boot key with the .iso file from the Ubuntu website, however, the Mini will not boot from it, it says operating system not found.   I also tried removing the battery, waiting, and then trying again with the cd, but that is not working.  I have made some short videos which hopefully will explain my situation in better detail. They are posted to this blog, and it may be better to view thm from bottom to top: [http://www.fixmymini.blogspot.com]("http://www.fixmymini.blogspot.com/")
Hopefully these videos help will explain my situation

---

### Post by starcannon on 2009-06-25
When you made your usb key, did you first format it to fat16? I do that by default for mine now, results may be identical with fat32. Have you tried burning another CD? Perhaps the one you've been using has an imperceptible defect, allowing it to boot intermittently. I think getting the no OS found error was actually a sign of stepping in the right direction.

---

### Post by philcamlin on 2009-06-25
usb keys can be tricky when holding os'es like ubuntu 

mine didnt want to boot for its life but then i used unetbootin :popcorn:

---

### Post by hevdaze on 2009-06-25
It is no longer saying no OS found when i use my usb.  My only other machine is a mac, from which I cannot use unetbootin.  I have used the diskutil method on my mac for creating the bootable usb drive.  Now, it says the drive is read-only and I cannot erase or restore it.

---

### Post by hevdaze on 2009-07-01
Ok, so now I think I may have messed up the partitioning of the hard drive.  When I first tried to do my fresh installation, I selected the option to use the entire hard drive for the new installation.  I had no important data on the drive, and I was planning on wiping it and freshly installing Ubuntu.  However, now it will not boot from a cd or usb drive.  I am going to try burning another boot cd to see if that works.  If that doesn't work, I don't know what I'll do.

---

