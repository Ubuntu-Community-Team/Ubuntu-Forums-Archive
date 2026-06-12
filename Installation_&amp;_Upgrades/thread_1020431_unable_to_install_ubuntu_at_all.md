---
title: "unable to install ubuntu at all"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by spiked4life on 2008-12-24
I'm trying to install ubuntu 8.10 on a intel p4 system. It has a 250gb drive that I partitioned into 2 partitions, both Ext3 filesystem. 

I downloaded and burned the ubuntu 8.10 distro onto a cd and successfully started it as a live cd on a virtual machine on another system. However when I boot from it on the machine I want to install it from it doesn't work. I can get to the main boot menu where you first select language and then can choose to boot it s a live cd or if you want to install. I've tried booting it as a live cd and just plain trying to install it as well as trying the memory test option. They all produce the exact same result on this machine. What happens is that the screen turns black and then the a cursor starts blinking in the very top left corner. That's all I can get it to do with any of these options. I've had it sitting like that for a good 10 minutes and nothing continues to happen. There is no disk activity according to the leds on the front of the case and the cd spins down and just maintains a very slow rotation. 

I can just fine start a win xp installation on this machine but the ubunto cd won't do anything.

Just in case there is a problem with the cd drive I also formated a usb stick and put ubuntu on it using UNetbootin. I can get to the boot menu on here as well when I chose the default option it prints 2 lines of code and then that same cursor starts blinking and nothing further happens.

Any idea what is going on here? Any help would be appriciated.

---

### Post by gettinoriginal on 2008-12-24
There are many reasons brought out by many threads on this subject, most having to do with poor disk burns, MD5 Sums, etc.  The simplest thing to do is to burn a new .ISO from the Ubuntu site and make sure to burn it at the slowest speed.  Most errors in the CD are created by bad data due to speed of the burning.   If you do not want to burn a new CD, then google:  ubuntuforums.org cannot install ubuntu.   Good Luck :P

---

### Post by spiked4life on 2008-12-24
> **gettinoriginal said:**
> There are many reasons brought out by many threads on this subject, most having to do with poor disk burns, MD5 Sums, etc.  The simplest thing to do is to burn a new .ISO from the Ubuntu site and make sure to burn it at the slowest speed.  Most errors in the CD are created by bad data due to speed of the burning.   If you do not want to burn a new CD, then google:  ubuntuforums.org cannot install ubuntu.   Good Luck :P

I checkd the MD5 sums and they match perfectly. I burned a new disk at the slowest speed allowed and tested it on my machine. It also worked perfectly, just like the first one. I tried inserting it in the machine I want to install it on but it just produced the same result as before. It gives me the boot menu, I can choose language, but as soon as I choose to install or run the live cd nothing further happens other then a blank screen with a single blinking cursor. 

I have tried googling the issue but most of the returned results are about "unable to install program X in ubuntu" or they are about a very spesific error message. I get nothing what so ever so it is pretty difficult to debug the problem when I have nothing to go on.

If it is of any help I'm gonna list the machine specs here:
Mobo: ASUS P4P800
CPU: Intel P4 2.6 Ghz
Memory: 1Gb
GPU: Radeon 9600 GT 64 mb

---

### Post by gettinoriginal on 2008-12-24
If it works on one machine, but not on another, I feel it must be a hardware problem, but I do not know, so I will leave it to those with more knowledge,  Good Luck :confused:

---

### Post by spiked4life on 2008-12-24
> **gettinoriginal said:**
> If it works on one machine, but not on another, I feel it must be a hardware problem, but I do not know, so I will leave it to those with more knowledge,  Good Luck :confused:

Thing here is that windows xp works perfectly on this machine. At least it did 5 minutes ago until I reformated into Ext3. I've been googling some more and found this quote on another thread on here:

> This is a very common problem. That's the good news.
The bad news is nobody seems to know how to fix it!

If you amend the boot options (press F6 I think) and delete "splash" and "quiet" you will get verbose info on whats loading. It is likely to end with something like "can't resolve tty". If so your having the same problem as everyone else, but I haven't seen a solution anywhere. Try a different distro?

I didn't try what he suggested so I can't say for the "tty" thing but it seems like there are more people then me having this problem. I'm downloading the alternate distro now to see if that might hlp.

---

### Post by niklinux03 on 2008-12-24
Hi,

I had difficulties to install Ubuntu 8.04/8.10 on my Intel P4
machine as well, though not quiet the same as you.
The main reason was the dvd drive. But this problem occurred
after I entered the installation procedure.

In your case it looks like that the system isn't able
to load the initrd.gz and vmlinuz images.

Here is my workaround.
1.) I installed a command-line system of Debian/Etch.
2.) In the installation images of Ubuntu 8.04/10 there is a directory called, i.e. on the burned CD, 
```

install/netboot/ubuntu-installer/i386

```
There I found the linux and initrd.gz images.
3.) I created below the directory /boot in my Debian installation a directory called ubuntu.
In this directory I copied the linux and initrd.gz images from 2.).
4.) I edited the /boot/grub/menu.list.
I copied one of the existing entries and modified them so
that at the next boot there was an entry called Ubuntu Installer.
```

title		Ubuntu Installer
root		(hd0,2) 
kernel		/boot/ubuntu/linux
initrd		/boot/ubuntu/initrd.gz

```
Leave the root entry as it is in your case.

This procedure worked for my P4 PC.
Of course, a prerequisite is an existing Debian installation.
Cheers

---

### Post by gettinoriginal on 2008-12-24
Just for information, it is not necessary to partition your drive before installing Ubuntu, it includes a partitioner in the installation process.  Maybe if you gave the entire drive back to your windows application, then just insert the live CD, take it from there.  That way, everything has its correct partition and proper grub installed.

---

### Post by spiked4life on 2008-12-24
> **gettinoriginal said:**
> Just for information, it is not necessary to partition your drive before installing Ubuntu, it includes a partitioner in the installation process.  Maybe if you gave the entire drive back to your windows application, then just insert the live CD, take it from there.  That way, everything has its correct partition and proper grub installed.

I'm not dual-booting. I wiped the disk completely clean. There is absolutely nothing on there except two empty Ext3 partitions. I have tried the alternate ubuntu 8.10 distro but I got the exact same result. I also tried fedora 10 but it also halted with a blinking cursor with the last thing printed being: 

initrd0.img . . . . . . . . ready

And then that same blinking cursor.

@niklinux03: I also thought that it was the cd/dvd drive at fault, which is why I tried installing it from a USB drive, but I got the exact same result. I also don't have a previous Debian system so I'm not exactly sure how to try the things you suggested.

---

### Post by gettinoriginal on 2008-12-24
Are you turning your computer off after the disk is in and then restarting it so the computer boots from the CD ??  Make sure your bios are set to boot from CD first.

---

### Post by spiked4life on 2008-12-24
> **gettinoriginal said:**
> Are you turning your computer off after the disk is in and then restarting it so the computer boots from the CD ??  Make sure your bios are set to boot from CD first.

As I've tried explaining. I can boot just fine from the cd. Ubuntu even asks me to choose language and I am presented with the menu options of wheter I want to boot from the livecd or install ubuntu or a few other options. It is when I choose one of these options that the screen turns black and I simply get the blinking '-' on screen.

---

### Post by davidshere on 2008-12-24
When you see the blinking cursor, how long are you waiting?  Windows will do the same thing at startup sometimes.  Completely stop on a totally blank screen for 3-5 minutes. Give it 20 minutes.  Or 2 hours.

I also vote hardware problem.

I don't think you're having problems because partitioning your disk in advance .  The live CD should load whether you have a hard drive or not.

Have you tried the alternate installation (text only) installation CD?

---

### Post by gettinoriginal on 2008-12-24
Ok, doing some digging, I found these 2 things:

Some had "other" video equipment attached ie: TV tuner card, TV out cable, and disconnecting these solved the problem.

Second was this in another post:

- Booting from Ubuntu live install cd:
 * if you are in trouble with screen graphic user interface
   (usually the screen is black with a blinking cursor or screen out of range message):
- first try to dynamically change screen resolution please the press CTRL + ALT + "+" and/or CTRL + ALT + "-"
- Try to restart the graphic layer press CTRL + ALT + BACKSPACE
- Here the basic step required during install process [http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)

If you are still in trouble... please reboot your pc and starting with Ubuntu live cd please try to put some common Ubuntu kernel live cd options you can find the boot options howto here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Remove the "splash" and "quiet" options to see more boot infos message and/or errors.
Then try some commons parameters by putting them one by one or together:
noacpi nolapic nodma all_generic_ide pnpbios=off pci=noacpi

If this don't work i suggest you to download and burn on a cd at lower speed you can do (4x), here an howto [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Sorry, trying to help :P

---

### Post by Kevbert on 2008-12-24
It may be that your display adapter is the problem. Try the boot options link above and add vga=791 (you'll need to check the options for the exact number). Once you've installed you can use one of the restricted drivers for your card.

---

### Post by spiked4life on 2008-12-24
@davidshere: Waited 30 minutes. No change at all. The only way this is a hardware problem is if my hardware i not supported because windows xp worked just fine until I reformated earlier today. I also tried the alternate ubuntu distro if that is what you mean? Same result there. Just the single blinking dash on the screen.

@gettinoriginal: That machine does indeed have a tv card. Tried removing it but I still get the same issue with the blinking crash. 

I tried the F6 thing without quiet and splash. That gave me the attatched result but halted where shown. Can anyone make any sense of that?

I also tried the changing screen resolution keyboard shortcuts but they didn't seem to do much. I'll experiment some more with them though.

@Kevbert: I looked at the VESA modes table but I'm not sure why I should chose one over the other. I tried 791 which is 1024x768 16bit which resulted in a totally black screen with no blinking cursor at all. Could you perhaps explain a bit more on what you're getting at?

---

### Post by spiked4life on 2008-12-24
[SIZE="4"]acpi=ht[/SIZE]

That was the magic word. I'm now booted into the livecd and have started the installation. At one point it said that I hadn't defined a swap partition. I couldn't figure out how to do that. Is that something you can do later on? And if so, how?

---

### Post by spiked4life on 2008-12-24
Unfortunately, they joy was short lived. The installer rebooted at some point because when I came back to the computer it was stuck at a black screen. Won't have much more time to play around with the issue today, but I'll resume tomorrow. Until then, any suggestions would be greatly appriciated.

---

### Post by davidshere on 2008-12-24
> **spiked4life said:**
> I also tried the alternate ubuntu distro if that is what you mean? 
Depends on what you mean by "alternate ubuntu distro"... Ubuntu is a distro of Linux.  There are variations on Ubuntu such as Kubuntu and Xubuntu and Edubuntu.  I don't think they're referred to as being a different distro from ubuntu.  I could be wrong.

Ubuntu, straight Ubuntu without the K or X, has a regular CD and an Alternate Install CD.  They both install the exact same operating system (not a different distribution).  The regular install CD loads as a live CD first and then you an install from there.  The alternate install CD uses not GUI for installation and is text-only.

If you're having problems with video, which is likely from what you've described, The alternate install CD might get around them.  You can find more information about the alternate install CD here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Another thing that might be wrong is that you're using the 32 bit version CD and you actually have a 64 bit CPU, or vise versa.

---

### Post by spiked4life on 2008-12-25
> **davidshere said:**
> Depends on what you mean by "alternate ubuntu distro"... Ubuntu is a distro of Linux.  There are variations on Ubuntu such as Kubuntu and Xubuntu and Edubuntu.  I don't think they're referred to as being a different distro from ubuntu.  I could be wrong.

Ubuntu, straight Ubuntu without the K or X, has a regular CD and an Alternate Install CD.  They both install the exact same operating system (not a different distribution).  The regular install CD loads as a live CD first and then you an install from there.  The alternate install CD uses not GUI for installation and is text-only.

If you're having problems with video, which is likely from what you've described, The alternate install CD might get around them.  You can find more information about the alternate install CD here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Another thing that might be wrong is that you're using the 32 bit version CD and you actually have a 64 bit CPU, or vise versa.

Yeah, sorry, didn't mean alternate distro but alternate install cd of ubuntu. I have tried extensively both the one labeled desktop and the one labeled alternate and they both produce the exact same result. If I try to use the boot menu on either one of those versions I only get the black screen with blinking cursor. If I hit F6 and pass it the command "acpi=ht" the live cd will start successfully and I can use it normally. It will allow me to start the installation using the desktop shortcut, but at some point the installation reboots and when it does it is not able to boot back up, probably? because it no longer boots with the acpi=ht command. The system is definitely 32bit and I have only downloaded the 32bit distros.

---

### Post by spiked4life on 2008-12-25
Like I said previously I had some success with the "acpi=ht" command earlier with the dekstop version of the ubuntu 8.10. Today I also tried it with the alternate/NO GUI install version of ubuntu and amazingly it seems to have worked. I have now successfully installed and booted into the desktop for the first time after install. So far everything seems to be working but I'll have to do some more testing to be 100% certain that I got it right. I'll post back if I have some more issues.

---

### Post by Pumalite on 2008-12-25
I had 7.04 installed on a computer with the same specs. I just had to installl (on an empty drive formated ext3). Therefore I suspect your CD. Do md5sum on the iso, burn at 4x or less, do not use CD-RW, check CD integrity before install, clean the lens in your burner, try your CD in another computer. If you have to change your CD drive; do so.

---

### Post by davidshere on 2008-12-26
> **spiked4life said:**
> Like I said previously I had some success with the "acpi=ht" command earlier with the dekstop version of the ubuntu 8.10. Today I also tried it with the alternate/NO GUI install version of ubuntu and amazingly it seems to have worked.
Well that's a relief for me because I was fresh out of suggestions. :)

This should be a way you can add the **acpi=ht** option to boot every time.  (If you still are needing to do that)

1.  Applications>Accessories>Terminal
2.  Type ```
gksu gedit /boot/grub/menu.lst
```
3.  Before the line "## ## End Default Options ##" add the following:```
# Added by spiked4life
# acpi=ht
``` ** Do NOT uncomment the "acpi-ht" line.  **

4.  Locate the following equivalent lines in your file (won't be the same as mine):```
title		Ubuntu 8.04.1, kernel 2.6.24-21-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-386
```and change the line that starts with "kernel" by adding the **acpi=ht** directive at the end.

This should change your boot so that it uses this every time, and will still use it even after your next kernel update -- which, if you just installed and haven't done any updates, will be coming soon.  I think the last install of 8.10 I did had 222 updates after install.

---

