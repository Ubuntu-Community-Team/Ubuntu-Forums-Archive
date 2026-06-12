---
title: "[SOLVED] what to do after install ubuntu?"
date: 2008-11-22
forum: General Help
---

### Post by ecom on 2008-11-22
i checked the guides on the internet but i'd like to hear from u guys. what do u guys do immediately after installing ubuntu 8.10?

how do i install my drivers? the driver cd wont auto-run.

generally, i'm asking u guys what to do after installing since i'm still a newbie to ubuntu.

---

### Post by philinux on 2008-11-22
Click the medibuntu link below and follow the instructions. Be sure to use copy and paste.

Install ubuntu-restricted-extras.
[RestrictedFormats - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RestrictedFormats")

Enable your graphics driver.

System>admin>hardware drivers.

---

### Post by ecom on 2008-11-22
wow thanks. i guess i missed that guide.

what else do u guys do?

in windows, its:
1.install windows
2.check device manager
3.insert driver cds
4.install drivers
5.install microsoft office
6.install antivirus or security software
7.install multimedia apps
8.configure internet connection
9.install printer
10.other stuff

what do u guys do immediately after installing ubuntu?

---

### Post by oilchangeguy on 2008-11-22
> **ecom said:**
> wow thanks. i guess i missed that guide.

what else do u guys do?

in windows, its:
1.install windows
2.check device manager
3.insert driver cds
4.install drivers
5.install microsoft office
6.install antivirus or security software
7.install multimedia apps
8.configure internet connection
9.install printer
10.other stuff

what do u guys do immediately after installing ubuntu?

first, please spell all words "u" is not a word. second, by now the updates are available icon should be flashing. click on it, and install all updates. then check out all of the menu's and see what's there. don't play with commands, or make any changes, unless you're sure about what you're doing. ask here first. last, ENJOY UBUNTU!

---

### Post by malachi on 2008-11-22
Here's a good article.

[http://www.knowliz.com/2008/09/20-things-to-do-after-installing-ubuntu.html](http://www.knowliz.com/2008/09/20-things-to-do-after-installing-ubuntu.html)

---

### Post by ugm6hr on 2008-11-22
Use it.

No need for driver CDs, applications etc.

---

### Post by ecom on 2008-11-23
thanks very much. 

would you guys recommend compiz fusion? or ubuntu beryl?

what antivirus would you guys recommend? what multimedia apps?

---

### Post by dexter on 2008-11-23
> **ecom said:**
> 
would you guys recommend compiz fusion? or ubuntu beryl?


Compiz and Beryl have been merged into Compiz Fusion. It's installed by default, you can enable it in System->Preferences->Appearance->Visual Effects tab. Note that you need a driver that supports all the 3D stuff. (Ubuntu will probably tell you if you don't have a valid driver installed)

> **ecom said:**
> 
what antivirus would you guys recommend? what multimedia apps?

I've used linux for quite some years now and never installed an antivirus program. Most viruses are targeted at window so they just don't run a linux. There are very few linux viruses and linux is safer anyhow so an antivirus program is not necessary.

---

### Post by lisati on 2008-11-23
> **ecom said:**
> i checked the guides on the internet but i'd like to hear from u guys. what do u guys do immediately after installing ubuntu 8.10?

how do i install my drivers? the driver cd wont auto-run.

generally, i'm asking u guys what to do after installing since i'm still a newbie to ubuntu.
One of the first things I usually do is check for and install updates - this can sometimes fix problems. When I first started using *ubuntu (v7.04), this fixed a problem with the sound (or lack thereof) on my older laptop, and thus saved a lot of time searching for a solution.

EDIT: as for anti-virus, it's up to you: most of the time it only matters if you interact with Windows machines and want to avoid sending something nasty to them.

---

### Post by Paqman on 2008-11-23
Some handy packages you might want to install:

[list]
[*]**ubuntu-restricted-extras**
This installs multimedia codecs, fonts, Flash, Java, etc
[*]**ntfs-config**
If you have a Windows partition this will set it up so that is always available
[*]**startupmanager**
Allows you to tweak the Grub menu (eg: specify which OS is the default to boot)
[*]**vlc**
A much better video player than the default one
[*]**amarok**
Probably the most popular music player
[*]**Any of the Nautilus plugins**
Nautilus is the file browser, and there are loads of good plugins for it that will let you do things like resize images, open terminals, and open files as an administrator from a right-click.
[*]**Medibuntu**
Not a package, but a whole extra repository full of good packages. Mostly multimedia type stuff.
[/list]

Some things you won't need to install are a firewall and antivirus suite. On Linux, security is built-in. You don't need to add it yourself like you do with Windows. As long as you keep current with security updates, only use software from Add/Remove or Synaptic and don't mess with your firewall settings then you've got a very secure machine.

---

### Post by zh^eee on 2008-11-24
Hello.
I'm new to Ubuntu.
After the install, I've spent two hours to fix refresh rate but other than that, I've installed apps I use:
Opera, X-chat, Amarok, MPlayer, TrueCrypt and Firestarter.
Third day on Ubuntu, third day of life without windows. So far, so good.

---

### Post by linux_tech on 2008-11-24
Install dvd support, audio and video codecs, flash and java

In terminal enter this command:

```
 sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 
```

---

### Post by decard_pain on 2008-11-24
i would also recomend wine and dosbox so you can run old dos programs and a huge amount of windows programs.
these are mosty for gaming.

---

### Post by eeeek on 2008-11-24
The first thing I do after an install is head to the Synaptic Package Manager and install other stuff that I want. For me, this is one of the very coolest things about Linux, in general. 

I usually install Wincodecs and the mp3 codecs (can't remember the name) so I can play .wmv and .mp3 files. 

Then again, I have very simple needs from Linux up to this point.

---

### Post by linux_tech on 2008-11-25
Make a backup of all your important files, always a good idea before 
they get altered that way you can always go back to the original
First create a folder to put them in, then copy the files to that folder-
```

sudo mkdir /etc/orig_files
sudo cp /etc/apt/sources.list /etc/orig_files
sudo cp /etc/sudoers /etc/orig_files
sudo cp /boot/grub/menu.lst /etc/orig_files
sudo cp /etc/fstab /etc/orig_files
sudo cp /etc/hdparm.conf /etc/orig_files
sudo cp /etc/ssh/ssh_config /etc/orig_files
sudo cp /etc/X11/xorg.conf /etc/orig_files

```

---

### Post by ecom on 2008-11-27
many thanks to all!!! my dad will be happy when he gets out of hospital and sees what i've done with the pc.

i'll do everything u guys said. thanks for helping a kid (newbie to linux but not computers) get his ubuntu up and running.

---

