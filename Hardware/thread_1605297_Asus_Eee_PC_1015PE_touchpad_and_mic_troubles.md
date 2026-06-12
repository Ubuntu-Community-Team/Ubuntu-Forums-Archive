---
title: "Asus Eee PC 1015PE touchpad and mic troubles"
date: 2010-10-25
forum: Hardware
---

### Post by Tenzy on 2010-10-25
Hi,

I've got an Asus Eee PC 1015 PE and running linux Mint 9 (the problems are the same as with the Ubuntu 10.04 netbook edition) 
Got a bunch of problems but this is the biggest one.

There is no touchpad tab in the mouse settings so I cannot change anything. The touchpad doesn't turn off when typing.

With the mouse set to left-handed, a tap becomes a right click. Which makes the touchpad unusable for left-handed use. Using a mouse instead doesn't solve the problem because every time you accidentally touch the touchpad during typing it makes a right click and a context menu pops up. And that happens A LOT. Accidentally click on something in the context menu and you're really in trouble. 

The microphone and mic in don't work either. 

If anyone knows a fix for either, please help. The way the touchpad is right now, it makes ubuntu unusable for me.:(

Thank you.

---

### Post by lullabong on 2011-01-21
Hi,
Did you solve your problem? There is a software called TouchFreeze that freezes the touchpad when you use the keyboard... I am considering buying a netbook, and that one is the one I currently like the most. What other issues did you have with it?
Thanks!

---

### Post by Tenzy on 2011-01-22
Hi,

I'm now running linux Mint 10 (which is based on Ubuntu 10.10) on this netbook. All the issues have been solved with the latest version it seems.
I haven't tried Ubuntu Netbook 10.10 on it yet. I couldn't get the live USB to work on my main computer, but I'm not sure if I tried it on the netbook. I did briefly try jolicloud 1.1 though, which is also based on Ubuntu and made for netbooks and found the netbook to run very fast on it. You should definitely check that out as well. 

The touchpad on this netbook is nice and big, but also very close to the keyboad. If you are a fast typer it won't be a problem, but if you type slow, the build in function that makes the touchpad not work when typing might not always be enough.

On windows the battery life lasts longer. It has some sort of power management that doesn't let the fan turn on as often when running of battery power. With all the linux distros I tried the fan acts the same as when the netbook is plugged in with windows running. 

I haven't actually tested it but if I am to believe the taskbar/panel. Windows can last up to 10 hours and linux up to 7 hours. 

That said, windows 7 starter is absolutely horrible compared Ubuntu/Mint/Jolicloud.

---

### Post by N00b-un-2 on 2011-03-30
in order to fix the issue with the touch pad you will either need to install the elantech touchpad modules into your kernel, or if you're running kernel 2.6.34 or higher you will simply need to enable them.  For me, I'm running 10.04 on kernel 2.6.32-24-generic.  I installed kernel 2.6.34 and then add a line to the file
**/etc/modprobe.d/psmouse.conf**
```
sudo gedit /etc/modprobe.d/psmouse.conf

```
type
```
options psmouse force_elantech=1
```
and save.  Now if you go into mouse settings in the menu it should be recognized as a track pad.

The newer kernel did not agree with my system for some reason and popped up with errors at boot and caused lots of graphic artifacting with compiz enabled... dunno why, but my theory on Linux after breaking many a system is 'if it aint broke,don't sudo update-manager -d'

For my system I had to patch the psmouse kernel module, which was a new thing for me but simple enough.  If you have to do this, make sure you make backups!

If you're unsure which kernel version you are running, just type
```
uname -r
```
in the terminal.

There is a great tutorial [HERE]("http://ubuntuforums.org/showthread.php?p=9175201#post9175201") on the process.  Look at post #44.
A few caveats I encountered here -- first, make sure you're running the kernel you intend to patch otherwise it won't work and you'll have a broken mouse.
Second, if you modified your */etc/modprobe.d/psmouse.conf* file, you will need to undo any changes you made before trying to patch your kernel.
Third, the instructions seem somewhat incorrect to me in terms of context.  When you get to the part where you are supposed to un-bzip the kernel source I ran into errors.  I would open up nautilus and manually copy the /usr/src/linux-source-whateverversion.tar.bz into a folder in your home directory and unzip it that way.  It's big so it might take a minute or two.  After that, just follow the directions.
The last thing you will need to know is that when you get to step 5.5 which says **for Dell Mini Only**, you will have to perform those steps.  My first attempt to build the new psmouse module failed at this point so it's probably safe to assume that the Dell Mini uses the same touchpad.

As for the mic input issues, I had similar problems with sound.  I ended up installing alsa drivers from this repo
[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu").  This made the sound behave properly for the most part, enabling all the proper modes for sound.  One thing I've noticed is that if you reboot the computer without shutting down fully, sound will not work.  However if you shut down the computer properly and then power it back on, sound works properly, and this behavior is common to all 4 operating systems on my netbook (Ubuntu, WindowsXP, OSX and Android).  I've done a little digging and it seems as though the boot booster that resides on the first partition on the HD acts both a micro OS and also behaves as an EFI system (ie; what makes a Mac different from a PC).  Very interesting... Too bad I formatted the hard drive as soon as I unboxed the computer and lost that partition.  I'm looking into whether it's possible to get it back somehow.  I'll let you know what I find.

---

