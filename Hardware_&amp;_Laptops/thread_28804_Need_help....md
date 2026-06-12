---
title: "Need help..."
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by urbaneezer on 2005-04-21
I purchased a new 80G HD today, installed it, set it as slave.  My machine is running Win2K on the master drive...I want to install Ubuntu on the new HD and be able to select which OS I want to boot into upon restart.  I have the v4.10 install disc.

Anyone have some easy directions for a newbie?

Thanks in advance!

---

### Post by XDevHald on 2005-04-21
Most deffinently get Grub, this will give you a startup list with both Windows and Ubuntu listed for you to choose from.

If you don't like Grub, then check out LILO :)

**Edit$~> **Just a quick note, if you're unsure of how to install Grub or LILO. Goto: 

**System > Administration > Synaptic Package Manager **

And you can also make it really easy for yourself by going to the **Search **tool and use it to your own advantage. If anything else comes up, let us know :)

---

### Post by urbaneezer on 2005-04-21
Doc...thanks for the tip on Grub...but I need instructions on how to install Warty onto my new HD without distrurbing everything that is on my master HD.  

Grub will just allow me to select which OS to boot into at startup...right?

---

### Post by Gary Powers on 2005-04-21
As you boot off the Ubuntu disk, it will eventually  take you to the partitioning screen.  Partition manually and install Ubuntu on hdb rather than hda (which is your Windows drive C::).  Let GRUB install where the master boot record goes (MBR) which should be the default.  Might be a good idea to go into setup before you install and make sure your main HD is set to LBA rather than auto.  Just to save some potential confusion after installation.

Ubuntu is a great OS!  Enjoy!

Gary

---

### Post by urbaneezer on 2005-04-21
Just to clarify...
[I]
**Partition manually and install Ubuntu on hdb rather than hda (which is your Windows drive C:**[/I]

If I put in my 4.10 install disc and reboot, will I get an option for which drive to install on?
[I]
**Let GRUB install where the master boot record goes (MBR) which should be the default. Might be a good idea to go into setup before you install and make sure your main HD is set to LBA rather than auto.**
[/I]
So I should download GRUB before trying to install Warty?  Which f-stop key gets me into setup at startup?

---

### Post by urbaneezer on 2005-04-21
Apparently GRUB is now legacy and the download link for it is either not working or I don't know how to download it.  

Will LILO do the same thing?

---

### Post by urbaneezer on 2005-04-23
OK...so I got Warty and GRUB installed and can boot into either Win2K or Ubuntu at startup...no problem there.

Just a few more questions have arisen though.  

-What is the deal with the fuzzy resolution in ubuntu?  When web browsing all my fonts and images seem to be less 'crisp' than they do when running windows.  Is there a fix for this?

-When I tried to play a cd in my cdrw drive...no sound.  When I played it in my dvd drive...sound.  I am assuming this is a driver issue.  How do I verify and fix?

-When I booted from Ubuntu back over to Windows the clock had changed to four hours ahead.  Also, my screen resolution had changed.  Any way to prevent one OS from affecting the other?  

-Now this is a real idiot question here (and I apologize in advance)...what is the process for adding a plug-in to Foxfire?  I went to a website for a rock band that requires the flash plug-in, but I have no idea where the browser plug-ins are located.

Anyway, thanks for any and all help that anyone can provide!  It is much appreciated!  

-urb

---

### Post by nigel on 2005-04-23
regarding Flash try the tips [here](http://ubuntuguide.org/4.10/index.html)

---

