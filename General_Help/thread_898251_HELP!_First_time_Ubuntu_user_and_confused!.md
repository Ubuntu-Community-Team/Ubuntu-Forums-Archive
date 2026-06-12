---
title: "HELP! First time Ubuntu user and confused!"
date: 2008-08-23
forum: General Help
---

### Post by IDK312 on 2008-08-23
Hey guys/girls! 

Im new to the forum and new to Ubuntu at the same time. I  am having difficulty installing Ubuntu after the installation set up wizzard and after the reboot. Once i reboot i have two options to boot my pc in 1-Windows 2-Ubuntu. I click on 2 and i wait till Ubuntu loads, after it finish loading i get this command thing where i have to type in something i guess (sorry not really an expert on computers). It says i can type in help for a command list and i type in help, but i dont know what to do after that! I need an answer A.S.A.P. because i need this to work before the end of this week (Very important)! 

Also how come in all these youtube vids i see people just doing the install wizzard and reboot their pc it runs perfectly except for me?!?! :( 

Thx!

---

### Post by Ryadt on 2008-08-23
Type in```
startx
```

---

### Post by lisati on 2008-08-23
> **IDK312 said:**
> Hey guys/girls! 

Im new to the forum and new to Ubuntu at the same time. I  am having difficulty installing Ubuntu after the installation set up wizzard and after the reboot. Once i reboot i have two options to boot my pc in 1-Windows 2-Ubuntu. I click on 2 and i wait till Ubuntu loads, after it finish loading i get this command thing where i have to type in something i guess (sorry not really an expert on computers). It says i can type in help for a command list and i type in help, but i dont know what to do after that! I need an answer A.S.A.P. because i need this to work before the end of this week (Very important)! 

Also how come in all these youtube vids i see people just doing the install wizzard and reboot their pc it runs perfectly except for me?!?! :( 

Thx!

Which edition of Ubuntu did you install - the "desktop" edition, or the "server" edition?

---

### Post by IDK312 on 2008-08-23
> **lisati said:**
> Which edition of Ubuntu did you install - the "desktop" edition, or the "server" edition?

I installed the desktop edition.

Also i typed in startx it didnt find the file?

---

### Post by Ryadt on 2008-08-23
> **IDK312 said:**
> I installed the desktop edition.

Also i typed in startx it didnt find the file?

Can you do ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by IDK312 on 2008-08-23
> **Ryadt said:**
> Can you do ```
sudo dpkg-reconfigure xserver-xorg
```

i typed in (initramfs) sudo dpkg-reconfigure xserver-xorg and it came up with /bin/sh : sudo: not found.

Is there maybe a list of codes that i could try or i did something wrong installing ubuntu?

---

### Post by unca.paka on 2008-08-23
You sure you installed the Desktop version? After you boot the live cd, its all automated, X should get installed and boot you into Gnome after the install.

Was there a UI and everything when you installed?

**Also**
Might be a good idea to check the disk integrity, make sure you got a good burn. Not sure why it wouldnt install X, but you never know.

---

### Post by IDK312 on 2008-08-23
> **unca.paka said:**
> You sure you installed the Desktop version? After you boot the live cd, its all automated, X should get installed and boot you into Gnome after the install.

Was there a UI and everything when you installed?

I didnt get a livecd i used Daemon tools to read the ISO file. Unless thats where i did wrong!

---

### Post by mb_webguy on 2008-08-23
> **IDK312 said:**
> i typed in (initramfs) sudo dpkg-reconfigure xserver-xorg and it came up with /bin/sh : sudo: not found.

Is there maybe a list of codes that i could try or i did something wrong installing ubuntu?

Um, something's definitely not right here.  He shouldn't be getting an initramfs prompt...

---

### Post by xnostradamusx on 2008-08-23
if he downloaded the hardy heron desktop version and installed it its fully automated already i suggest making a fresh install and backup your files  so if you messed up anything you wont lose your important files.

---

### Post by IDK312 on 2008-08-23
> **xnostradamusx said:**
> if he downloaded the hardy heron desktop version and installed it its fully automated already i suggest making a fresh install and backup your files  so if you messed up anything you wont lose your important files.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) i got the desktop version.

Already tried uninstalling ubuntu and reinstalling it.

---

### Post by unca.paka on 2008-08-23
If I'm understanding you correctly, you installed ubuntu while running windows, using daemon tools? If so, I think you just found the problem.

---

### Post by Ryadt on 2008-08-23
Can you check your disk for any errors, and then check the md5sum of the iso.
Follow this link on how to check the md5sum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by mb_webguy on 2008-08-23
> **unca.paka said:**
> If I'm understanding you correctly, you installed ubuntu while running windows, using daemon tools? If so, I think you just found the problem.

Ditto.

You need to burn the iso to a disk using something like Nero or MagicISO, reboot your computer, and boot from the disk to install Ubuntu.  If you do that, then everything will be like on the YouTube videos. :wink:

---

### Post by 16777216 on 2008-08-23
I would burn the ISO to a real disc and reboot to it.
Using a drive emulator ( Damon tools ) was likely the cause of your troubles.

Burn the disc and put in the CD drive and restart your computer.

If your computer starts with Ubuntu it is running from the CD, it should have a desktop with icons and everything and you can install from there.

If it comes to a text only ( quite DOS looking ) screen with install options and other such options of the like you likely have the server disc which has no desktop because it was made for servers that usually have no screen during normal use.
You may want to download the "desktop edtion" CD and try a reinstall.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

If your computer reboots back to the "choose windows or Ubuntu" type screen it did not boot to the CD.

If this is the case you may need to change an option in your computer's BIOS this is usually done by pressing and holding a button when your computer first turns on this button is usually escape ( esc ) or delete ( with the insert and home and page up/down keys ) 

When you turn on your computer you may see at the bottom of the screen a message like "Press esc to enter setup." or "Press delete to enter setup."
Press that key then, you will enter the computer's hardware setup.
**[COLOR="Red"][SIZE="3"]I suggest you look up your computer and/or motherboard information on the net or in the manual if you have it before you do anything in the BIOS because you can make it where you computer sill not start, so don't change anything that you are not sure what it does.( It is kinda hard to really "break" anything here but if you make a boo-boo you may have to open your computer and "short a jumper" which is a little piece that goes on some little wires sticking out of your motherboard to reset the BIOS. )[/SIZE][/COLOR]**
The option you are looking for will be for the "boot order" this tells the computer what devices to look for an OS on and in what order.
You want to make the CD drive first So that your computer will boot from CD if A: There is a CD in the drive and B: That CD is bootable otherwise it boots from the hard drive like normal.

If any one wants to add to this or correct me feel free.

---

### Post by mb_webguy on 2008-08-23
It's rarely necessary to change the BIOS settings.  There's usually a key that will bring up a boot menu.  On my Dell it's F12...

By the way, while there are many others on the Internet, I have a fairly detailed tutorial on my blog (see the link in my signature below) on installing Ubuntu, with a focus on dual-boot installations.  You might find it helpful.

---

### Post by 16777216 on 2008-08-23
> **mb_webguy said:**
> It's rarely necessary to change the BIOS settings.  There's usually a key that will bring up a boot menu.  On my Dell it's F12...

By the way, while there are many others on the Internet, I have a fairly detailed tutorial on my blog (see the link in my signature below) on installing Ubuntu, with a focus on dual-boot installations.  You might find it helpful.

I can hold F9 t get a boot menu on my "frankenputer." (Biostar motherboard)
But yes, you are correct.

---

