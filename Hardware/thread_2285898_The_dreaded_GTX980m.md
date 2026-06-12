---
title: "The dreaded GTX980m"
date: 2015-07-08
forum: Hardware
---

### Post by aaron92 on 2015-07-08
Hello Ubuntu Community,

I have installed Ubuntu 14.04.2 LTS and when I checked my hardware, I noticed that my graphics card (GTX 980m) was not recognized as a card at all. It seems as though Ubuntu is acting like there is not even a card in my card slot. The machine on which I am working is
Alienware M17x R4
14GB of 1600MHz RAM
Intel i7 3610QM 2.30GHz
1x 60GB SSD with Windows 8.1
1x 1TB SSD partitioned into two 500GB volumes. Ubuntu is installed on one of those volumes.
GTX 980m 

I have windows 8.1 working perfectly on this machine, and I installed Ubuntu on a second hard drive that is in my system. All hard drives are SSDs.

I don't know if I need a specific driver in order to get my 980m recognized or if I have to install Ubuntu again with some modification, hence why I am here asking the Community.

To be specific, my question is:
How can I get my GTX 980m to be recognized by Ubuntu so that I can run CUDA and take full advantage of the graphics power of the GPU.

Many thanks!

---

### Post by Bashing-om on 2015-07-09
aaron92; Hello;

The situation is that drivers for your card are not available in our software repository. But, are available in a trusted PPA.
To install the driver:
Activate a terminal and execute terminal commands:
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-352

``` The utility to control the graphics sets - nvidia-prime - will also be installed .

reboot the machine to see the effect.

[INDENT][INDENT]just my bit to try and help
[/INDENT][/INDENT]

---

### Post by aaron92 on 2015-07-19
Thank you, **Bashing-om** for your expedient reply to my post. I apologize that it has taken me this long to express my gratitude. 

**INITIAL RESULT:**
The code that you posted works. I am able to use my graphics card because Ubuntu now recognizes that it is present.

**ISSUES:**
There are a couple problems, though--one minor, and one major.

The *minor* problem is that the mouse skips across the screen and is not smooth like it is while running on the intel graphics drivers. I assume that the reason for this is because the nvidia drivers aren't perfect, and they still need a little refinement. I am okay with this. As I said, this is minor.

The *major* problem is that the drivers are very picky. After playing around a bit, I found out that if I go onto any screen that does not immediately use the nvidia graphics drivers installed on my account on this computer (particularly the "Switch Account" screen), I get a solid black screen. It is not a black screen with a cursor or anything. It literally seems like the computer does not recognize that any monitor exists. The back-light for the screen works fine, and the operating system works (I know this because the general state of the number-lock key is set to "off" during the login screen, but once I log into the operating system, it reverts to its general state in my account which is the "on" position. I have a black screen the entire time this is happening, I simply type in my password and hit the "enter" key and the number-lock key comes on right away.) The conclusion to which I have come is that the monitor recognizes that it is plugged in to something, but the computer does not recognize that anything is present. I have tried connecting an external monitor, and I get exactly the same result. I have even connected the external monitor and closed the lid on my computer, and I still get the same screen. I feel like the graphics drivers obtained some bug and now they do not work at all. 
I wish I knew of a way to learn more about graphics drivers so that I could contribute more to this issue, but I have no idea where to even start with learning that great skill. 

**HOW I ENCOUNTERED THE ISSUE:**
The way that I encountered this problem is by locking the computer, and then selecting the "Switch Account" item in the "Gear" (i.e. options) menu. As soon as I selected it, I no longer was able to see any GUI and all I see is the solid black screen. 
I am still able to access the Grub menu, and I still see the Ubuntu POST screen. 

If there is any solution to my Black Screen Issue, I would greatly appreciate the assistance as I have not deleted that Ubuntu operating system on that particular volume yet. I would like to not lose all of my already installed programs. If there is no way to solve this issue, then I guess I'll have to reinstall Ubuntu and start over again.

MANY thanks,
Aaron

---

### Post by Bashing-om on 2015-07-19
aaron92; Hummm ...

Progress made, but seems the system is not too happy with that graphics driver.
Let's try another - not so quite bleeding edge :
```

sudo apt-get remove --purge nvidia*
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-346

```
Reboot and let's see what the effect is .

[INDENT][INDENT]soon we will know more
[/INDENT][/INDENT]

---

### Post by aaron92 on 2015-07-19
I went into the advanced options from the grub menu and booted into the recovery mode. I then was able to obtain a terminal-type menu and I typed in all of those commands successfully. I then typed "sudo reboot" and attempted to boot back into the system normally and absolutely nothing has changed. I still get a solid black screen. Attached is a picture of my problem (it is a fairly basic picture).

[IMG]http://puu.sh/j5pUw/a0221d2d40.jpg[/IMG]

---

### Post by Bashing-om on 2015-07-20
aaron92; Well; ...

Here:
> 
I went into the advanced options from the grub menu and booted into the recovery mode. I then was able to obtain a terminal-type menu and I typed in all of those commands successfully.

In recovery mode the file system is mounted read-only; did you do step 1 and remount the file system read-write ?
```

mount -o remount,rw /

```
(Note there is no space after the comma.)

[INDENT][INDENT]a process in learning
[/INDENT][/INDENT]

---

### Post by efflandt on 2015-07-20
Actually, from recovery, you typically need to first chose something about Enable Networking first, which remounts the drive read-write. If that comes up with any errors about some hardware not recognized, wait until it goes back to the menu, then select Root Console. But if networking was not enabled or drive was read-only I would expect some error trying to install different drivers that were not accessible without networking.

Does your laptop have a visible way to tell which graphics is being used (my power LED is [COLOR=#0000ff]blue[/COLOR] for Intel and [COLOR=#ff8c00]amber[/COLOR] for Nvidia)? When you get a black screen can you get to one of the virtual terminals (Ctrl+Alt+F1 through F6) and is there a visible login prompt? Alt+F7 would take you back to wherever you were in X (or gui login screen) from there (or Ctrl+Alt+F7 if not sure where you are).

One thing someone mentioned was that for hybrid laptops with dual graphics **NOT** to use **nomodeset** kernel boot parameter during install, that is usually needed for desktop PCs that only have nvidia graphics. So I did not use that when installing 14.04 to mSATA SSD on my laptop. But it has older Intel HD 4600 / Nvidia GTX 765M which has been around longer (currently running nvidia-331-updates from normal repos). So I have not experienced the mouse and other issues you have, but have not tried logging in as a different user either. I have logged in as a different user on my desktop which has the new Maxwell chip in its GTX 750 Ti (but not dual hybrid graphics) running nvidia-352 from xorg-edgers ppa.

---

