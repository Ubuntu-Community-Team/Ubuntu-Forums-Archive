---
title: "Install freezes (~72%) after reboot?"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by Zyzzyva100 on 2005-12-16
I have been trying to install Ubuntu on my fiancee's computer all night now without any luck.  First I was trying to install on her 80 gig WD SATA drive so that her new 300 gig maxtor drive could just be mass storage.  The install went ok until the reboot, and then I got an "error loading operating system" message.  I tried twice, but no go.

So then I tried installing on the new maxtor drive (which is true sata, ncq etc, not just an ide drive with a convertor built in).  Now this worked through the reboot, but at 72% it always freezes.  First it would freeze right after "installed xset", and if I rebooted I would get the message that I had stopped install, and i may be missing packages.  Well I tried to continue, but since xserver install was screwed up, I just got the shell prompt, which was frozen anyway.

So then I reburned the cd (though the first one installed on my laptop fine), and checked the md5sum again, and it was ok.  Then I installed again, and it gets to acpi support, and the screen gets corrupted and it freezes.  I really have no other ideas on what to try.  They only other install experience with ubuntu I have had is on my thinkpad, but it "just worked", no problems.  I would have figured that a desktop would be easier.  I am a gentoo user on my desktop, so I am a bit inexperienced troubleshooting ubuntu.

The computer is running a s754 sempron 64 processor on an NF4 motherboard.  I saw another thread similar to this in which similar hardware seemed to cause the same problems, but there were no solutions in it, and it seemed dead.  So, anyone have any ideas?

---

### Post by cdhotfire on 2005-12-16
Pop in the cd, then it should show ubuntu screen saying
```

boot:

```
at bottom, now type in server and press enter. Finish the install, then after you log in without the gdm, meaning with the white letters and black background, do
```

$ sudo nano /etc/apt/sources.list

```
then check to see you have ubuntu repositories there, if youd like uncomment the universe and sorts. Then finish up with a 
```

$ sudo apt-get install ubuntu-desktop

```

That should set it up just fine, after it finishes reboot, and behold.

---

### Post by Zyzzyva100 on 2005-12-17
Thanks for the info.  I am still getting used to apt-get (since I am used to using emerge through portage).

The advice will have to wait though.  Apparently during the last hang, a good portion of the southbridge died, as none of the 4 serial ata ports now work.  The entire controller must have died, so maybe it was on the fritz the whole time, and thats what was causing my problems.  Anyhow, time to RMA to newegg.

---

### Post by cdhotfire on 2005-12-17
[QUOTE=Zyzzyva100]Thanks for the info.  I am still getting used to apt-get (since I am used to using emerge through portage).

The advice will have to wait though.  Apparently during the last hang, a good portion of the southbridge died, as none of the 4 serial ata ports now work.  The entire controller must have died, so maybe it was on the fritz the whole time, and thats what was causing my problems.  Anyhow, time to RMA to newegg.[/QUOTE]

Well, good luck with that. Don't know what else to say.

---

### Post by Zyzzyva100 on 2005-12-17
Well I managed to get the motherboard working again by clearing the cmos for about half an hour.  Tried the server method of install, but it still doesn't work.

First there are errors regarding fontconfig (there are other threads on here about it, but no replies or fixes).  Then I manage to get to the xserver config screen, and it loses the keyboard.  The keyboard completely freezes up, I can't use any buttons or turn caps lock on or off or anything.

I tried with both a usb keyboard (and bios usb keyboard support on and off) and with a ps2 keyboard.  Same results everytime.  Something is just not compatible with the ubuntu installer and this hardware.

I was installing ubuntu to try and save time over installing gentoo, but as it turns out, I could have easily installed gentoo in the time I have tried to get ubuntu to work.  Oh well, back to the drawing board.

---

### Post by cdhotfire on 2005-12-17
Hmmm, when I do server install, it also tells me errors about fonts, but that does nothing.  I guess its a piece of hardware thats screwing everything up.  This happened to me once, it was my motherboard, and it apparently resutled to be broken, and so I had to buy a new one. I don't know how else I could help, but atleast x comes up with server install.

---

### Post by Zyzzyva100 on 2005-12-17
Well I guess its not ubuntu thats the culprit.  I decided to try SUSE 10 as well, and I was able to get through the entire installer, only to have the same thing happen.  The graphical login would just freeze, and when I tried failsafe mode to login via the shell, again I was without keyboard.

Something about the (seemingly 2.6.x in general) kernel doesn't like this motherboard.  Its made by DFI, so its not like its some unknown brand or anything.  It was even reccomended by Anandtech not long ago for budget systems, which is why I got it.  Guess we will have to get a different motherboard in the future if we want to try linux on that machine again.  Thanks for the help though!

---

### Post by cdhotfire on 2005-12-17
If its the kernel, you could try installing Warty, then upgrade through repos.

Install it, then go into Synaptic and search for "linux", locate the linux-image-*,  linux-restricted-modules-*.  Then click on one of them and press Package -> Lock Version, then do the same for the other, then close synaptic and do
```

$ sudo gedit /etc/apt/sources.list

```

Leave only the main ones, meaning dont add the universe and multiverse, change where it says warty to breezy.

something like this
```

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted

deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted
 
deb http://us.archive.ubuntu.com/ubuntu/ breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy main restricted

```

Then do
```

$ sudo apt-get update
$ sudo apt-get dist-upgrade

```

That should upgrade everything but the kernel. :)

After its done, reboot, and add the universe and multiverse if youd like
```

$ sudo gedit /etc/apt/sources.list

```
```

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse

```
And these extra ones if youd like. :P
```

deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

```

Then do
```

$ sudo apt-get update
$ sudo apt-get upgrade

```

And behold your new system. :)

Note:If you dont live in the US, delete the us. in some of the repositories.

Gl, hope this helps.

---

