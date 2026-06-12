---
title: "Is it possible to boot into Ubuntu without a boot loader?"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by NeonBible on 2009-01-11
Basically I share my PC with my dad, and he would find it quite annoying if he saw a boot loader everytime he turns the PC on.

Is it possible to not have a boot loader and use a Boot CD or something to go into Ubuntu (which is installed on the HDD)?

---

### Post by flytripper on 2009-01-11
i take it this means you are dual booting xp?
i think there is a way to set xp as default boot but sorry i dont know how offhand.

---

### Post by NeonBible on 2009-01-11
Yes sorry, dual booting with WinXP.

I don't want to see a menu at startup.

I want to boot into Ubuntu through other means, either by Floppy or CD.

Also I don't really want to mess with the MBR.  Are there any dangers with this?

---

### Post by MadsRH on 2009-01-11
sorry, misread your post!

---

### Post by DeMus on 2009-01-11
> **NeonBible said:**
> Yes sorry, dual booting with WinXP.

I don't want to see a menu at startup.

I want to boot into Ubuntu through other means, either by Floppy or CD.

Also I don't really want to mess with the MBR.  Are there any dangers with this?


Why not make XP the default OS to boot in the Grub list so XP starts automatically after let's say 2-3 seconds. This will give you time to change the boot of the OS you want to start, which I presume is Ubuntu.

DeMus

---

### Post by melojo on 2009-01-11
Have a look at the link below!
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

---

### Post by NeonBible on 2009-01-11
> **DeMus said:**
> Why not make XP the default OS to boot in the Grub list so XP starts automatically after let's say 2-3 seconds. This will give you time to change the boot of the OS you want to start, which I presume is Ubuntu.

DeMus

I guess we can live with this.  So writing to the MBR is not going to mess with my XP install?

> **melojo said:**
> Have a look at the link below!
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

Looks like what I need! but this is assuming I have installed Ubuntu already and have already modified the MBR with grub.  How do I not modify the MBR all together?

---

### Post by frost151n on 2009-01-11
Reinstalling the Win MBR and then telling it that Ubuntu exists is a complicated process.
I'm guessing you have GRUB, in which case boot into Ubuntu and from add/remove programs install the StartUp-Manager. From there you can set XP as the default boot and have the OS selection screen show for 2sec.

..after install it'll be in System>Administration

---

### Post by caljohnsmith on 2009-01-11
As melojo all ready suggested, you can create a Grub boot floppy, or if you have say a USB stick, you could put Grub on there and use that instead to boot Ubuntu (assuming your BIOS supports USB booting). Or you could make a custom Grub boot CD and use that, so there are lots of options. If you want to use those methods, you don't have to modify your Windows MBR; in order to make it work, when you go to install Ubuntu, click on the "advanced" button near the end of the installation, and specify to have Grub installed to whichever is the Ubuntu partition (/dev/sda3 for example). If you do that, Grub will be installed to the boot sector of the Ubuntu partition, leaving your Windows MBR untouched. Then if you want I can help you make a Grub USB stick, CD, or whichever you prefer. 

If you would like some help with it, then once you've installed Ubuntu, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and what it will take to boot Ubuntu from floppy/USB/CD.

---

### Post by NeonBible on 2009-01-11
> **caljohnsmith said:**
> As melojo all ready suggested, you can create a Grub boot floppy, or if you have say a USB stick, you could put Grub on there and use that instead to boot Ubuntu (assuming your BIOS supports USB booting). Or you could make a custom Grub boot CD and use that, so there are lots of options. If you want to use those methods, you don't have to modify your Windows MBR; in order to make it work, when you go to install Ubuntu, click on the "advanced" button near the end of the installation, and specify to have Grub installed to whichever is the Ubuntu partition (/dev/sda3 for example). If you do that, Grub will be installed to the boot sector of the Ubuntu partition, leaving your Windows MBR untouched. Then if you want I can help you make a Grub USB stick, CD, or whichever you prefer. 


Sorry I am quite new to Linux.  I have had it before but pretty much performed standard installs.

So when I come to install Ubuntu, I will choose a partition which is actually on the same physical HDD as Windows. I thought a MBR is per hdd and not per partition? So even if I write Grub to the the Linux partition, it will still need to modify the MBR of the HDD?

I have been doing a lot of googling and I tend to read that Grub settings are only configurable with the 'alternative Cd' version. Although they could be out of date.  Is this still true of 8.10 desktop edition CD?

I might just go ahead and add Grub and set it to a 2-3 second wait at startup, but I would like to know my options first.

SO just to clear things up, here is what I can do..

1) (i)Install Ubuntu, install Grub with default settings (which will write to Windows MBR?)
   (ii)Boot into Ubuntu and install Start-up Manager and edit Grub to make WinXP default and wait for 2-3 seconds.

2) (i) Install Ubuntu, install Grub with default settings
   (ii) Create Grub boot floppy
   (iii) Boot with Windows XP CD into recovery and fixmbr to restore my original mbr and not to have Grub menu at startup
   (iv) Use Grub floppy to boot into Ubuntu.

Are both these options viable and are they correct way to do things?

---

### Post by caljohnsmith on 2009-01-11
> **NeonBible said:**
> Sorry I am quite new to Linux.  I have had it before but pretty much performed standard installs.

So when I come to install Ubuntu, I will choose a partition which is actually on the same physical HDD as Windows. I thought a MBR is per hdd and not per partition? So even if I write Grub to the the Linux partition, it will still need to modify the MBR of the HDD?

You're right, the HDD has only one MBR (Master Boot Record), and that happens to be the first sector of the HDD. But each partition has what some people call a PBR (Partition Boot Record), also known simply as the boot sector of the partition, and that's the first sector of the partition. If you install Grub to the partition boot sector, you are not touching the MBR, so your computer will continue to boot straight into Windows as though you had not installed Ubuntu. But then you could use a Grub boot floppy/USB/CD to boot Ubuntu if you want. 
> **NeonBible said:**
> 
I have been doing a lot of googling and I tend to read that Grub settings are only configurable with the 'alternative Cd' version. Although they could be out of date.  Is this still true of 8.10 desktop edition CD?

That info must be out of date, because if you use the settings under the "advanced" button during the installation from the 8.10 Desktop Edition CD, as I mentioned in my previous post, you can specify there where Grub gets installed to.
> **NeonBible said:**
> 
I might just go ahead and add Grub and set it to a 2-3 second wait at startup, but I would like to know my options first.

SO just to clear things up, here is what I can do..

1) (i)Install Ubuntu, install Grub with default settings (which will write to Windows MBR?)
   (ii)Boot into Ubuntu and install Start-up Manager and edit Grub to make WinXP default and wait for 2-3 seconds.

2) (i) Install Ubuntu, install Grub with default settings
   (ii) Create Grub boot floppy
   (iii) Boot with Windows XP CD into recovery and fixmbr to restore my original mbr and not to have Grub menu at startup
   (iv) Use Grub floppy to boot into Ubuntu.

Are both these options viable and are they correct way to do things?
The first scenario you outlined should work just fine, but the second case you list you don't have to accept the default settings, have Grub installed to the MBR, and then have to fix it afterwards by doing a "fixmbr" from the Windows Install CD; that's the point of changing the settings under the "advanced" button during the installation, so Grub doesn't have to overwrite your MBR. It's up to you how you want to do it, but if you want my opinion, I would recommend just going with the first case you list above (like DeMus suggested) since it is easy and works well for most people. Let us know if you run into problems or have more questions.

---

### Post by NeonBible on 2009-01-11
Ok, I think I will go for option 1.

thanks all for the help.

---

