---
title: "Kubuntu:  Futureproofing?  Disaster preparation?"
date: 2006-02-22
forum: Hardware &amp; Laptops
---

### Post by Qwertie on 2006-02-22
In the past I have needed to switch a hard drive to a new machine, either to upgrade or because the old machine died. In Windows, this is usually fatal, because Windows only keeps one IDE driver (from the old machine) on hand and will give an INACCESSIBLE_BOOT_DEVICE blue screen when you switch machines. However, if you follow certain steps in advance, you can avoid this problem and Windows will start OK.

What about Kubuntu? How will it react to a total hardware environment change? 

What if I have to switch to a small monitor for some reason? How can I make Kubuntu start at a low resolution? If some files become corrupt on the HD and Kubuntu refuses to start normally, how can I recover, or at least back up my files before reformatting? Does X Windows have a 'safe mode' if you mess up a config file and it won't start normally?

I ask because last time I installed Linux, I made a small but fatal change to X Windows' video card settings. Since my Linux distro always booted into X, which immediately froze the computer solid, I was totally screwed.

---

### Post by audax321 on 2006-02-22
> What about Kubuntu? How will it react to a total hardware environment change?

Not sure about this one, but I believe hardware is detected each boot. As long as you are not using a kernel that conflicts with the new processor it should be fine. However you may need to edit the xorg.conf file after booting if your video hardware and monitor have changed. This can be done at the prompt using the nano text editor or if you have to use a LiveCD using whatever text editor is available with it.

> What if I have to switch to a small monitor for some reason? How can I make Kubuntu start at a low resolution? If some files become corrupt on the HD and Kubuntu refuses to start normally, how can I recover, or at least back up my files before reformatting? Does X Windows have a 'safe mode' if you mess up a config file and it won't start normally?

The answer to all of this is LiveCD. LiveCDs can be used to access your hard drives without actually using them to boot off of. I usually prefer the Knoppix LiveCD for this. You just put the CD in, boot, mount your hard drives if they aren't automounted and access your files. The LiveCD will also let you modify files in your root partition so if you mess up a config file you can fix the problem here. If you switch to a smaller monitor and didn't change the resolution in your xorg.conf file prior to the switch you'll most likely need to use this LiveCD method. If you're lucky the X server will give you a prompt.. if not use the LiveCD.

In my opinion Linux has been far easier to fix than Windows just because there is no registry and everything is fixed using config files. It's much more straight forward IMO. And LiveCDs have to be one of the best recovery tools I've ever come across. Leaps and bounds better than safe mode.

---

### Post by Qwertie on 2006-02-22
Thanks for the info.  Speaking of Live CDs, I have a Kubuntu Live CD, but I couldn't mount the hard drives on it because that required root access and I didn't have a root password (or even a user password).

I tried a blank password and "root" as the password.  No luck.

What it the Kubuntu Live CD's root password?

BTW, that Live CD should probably inform users that the supposed hard drive on which / is mounted is fake (it must be a RAM drive) and that if they save any files, they aren't really getting saved!  Well I have plenty of advice for Kubuntu's developers but here isn't the place...

---

### Post by audax321 on 2006-02-23
The only LiveCDs I've ever really used are the Ubuntu ones and Knoppix. And I believe the Ubuntu and Knoppix LiveCDs do not have a root password so you just mount using sudo and it shouldn't prompt you, but if it does you just hit enter. I don't know much about the Kubuntu ones. Personally I find the Knoppix one's to be friendlier for recovery since they automount all the drives read-only at boot. Then to make the drives writeable, you just right-click the drive on the desktop and click make drive writeable. :)

---

