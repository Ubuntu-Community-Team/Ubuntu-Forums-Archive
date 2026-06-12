---
title: "Installed but no GUI"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by Outrak on 2009-04-11
Hey all,
Ive been having a problem installing ubuntu 8.10 on my laptop. I attempted to use the regular live cd however I could never see the GUI it would only boot into the ubuntu@ubuntu interface. 
I then tried the aleternate live cd and had a sucsefful installation, except when I boot into ubuntu from grub, again, it only boots into the root@user interface. 

I am running an acer aspire 6530 laptop. amd turion 64 bit processor. dual ati radeon HD 3470 with 256mb, and 3 gigs of ram. 

HELP ME PLEASE

---

### Post by lisati on 2009-04-11
I've had a look at your other thread [http://ubuntuforums.org/showthread.php?t=1118105](http://ubuntuforums.org/showthread.php?t=1118105)

Here are a few thoughts:
Did you use the "Desktop" edition or the "Server" edition? 
Did you burn the ISO file as a disk image (the best way) or extract the files first (not really necessary, see [here]("https://help.ubuntu.com/community/BurningIsoHowto"))?
Did you check the disks for errors?

---

### Post by Outrak on 2009-04-11
I installed the alternate iso,
I burned the iso to a disc
I checked the disc, and it was fine.

I have installed the actual system on my hard drive, it just doesnt boot to an actuall desktop. would the alternate installer do this?

---

### Post by Outrak on 2009-04-11
bump

requesting assistance!

---

### Post by albinootje on 2009-04-11
> **Outrak said:**
>  I then tried the aleternate live cd and had a sucsefful installation, except when I boot into ubuntu from grub, again, it only boots into the root@user interface. 

Are you getting a text prompt (something) like this :
adrian@ubuntu-desktop:~$ 

Or a "busybox" prompt ?

The alternate installation cdrom should give you a desktop, but perhaps there's an issue with the video driver configuration.
Can you boot with special boot parameters "noapic nolapic" ?
See here : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Outrak on 2009-04-11
it boots into the ubuntu@ubuntu. Specificaly redleader@outrak, 
It gets me to sign in even, inputing a username and a password.

When i added the boot commands noapic nolapic it had a series of errors and wouldnt boot. I also tried the xforcevesa command however the boot got stuck on starting powernowd, where it would just hang.

any other ideas?

---

### Post by albinootje on 2009-04-12
> **Outrak said:**
>  any other ideas?
Can you check whether there's enough free diskspace with this command in the "recovery mode" :
```

df -h

```

---

### Post by Outrak on 2009-04-14
ok! I believe that I have found the root of the problem. When I try to run startx in the interface, within the text that loads it says
Primary Device is not PCI
No device detected, using the file
/etc/X11/xorg.conf
so I assume that my videocard would be using a different port... perhaps pciexpress or agp(maybe... i know its old). 
so how do i get ubuntu to find my videocard?

---

### Post by Outrak on 2009-04-14
bump

---

### Post by pbpersson on 2009-04-14
I used to know this one

There is a way to tell the OS to reconfigure XServer from the command prompt


OK, I did a search.  Try this:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by pbpersson on 2009-04-15
The other thing you can do - Google your video card and see what other people have done to make it work.

The /etc/X11/xorg.conf file is plain text and you can manually change the contents IF you know what you are doing.

I you completely mess it up, you now have the command to use that will reconfigure it back to the basic setup.

When manually modifying config files, it is good to make a backup

```
cd /etc/X11
sudo cp xorg.conf xorg.mybackupMMDDYYYYHHMM
```

Of course, MMDDYYYYHHMM is the date and time.  At least that is how I do it

---

