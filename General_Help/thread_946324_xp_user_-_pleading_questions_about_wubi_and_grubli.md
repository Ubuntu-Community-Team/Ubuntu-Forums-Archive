---
title: "xp user - pleading questions about wubi and grub/lilo installation"
date: 2008-10-13
forum: General Help
---

### Post by mgguy on 2008-10-13
A friend suggested that I install a version of Linux called Wubi over my XP OS. 

I first defragged my large hard disc several times.

I went to a Wubi site and down loaded same. Now, in searching my list of programs I do see several files and a folder with titles including Ubuntu so something must have happened.

I followed the install directions to a T.

I rebooted and ended up not seeing a "choice screen" that would allow me to choose which OS I wanted to use. I have rebooted several times. In fact, where as I once watched the passing of a series of black and white screen with lots of esoteric information as the boot process occurred before Windows opened I do not see that now.

I have searched high and low for help, including posting a thread here a day or so ago, but I have become even more confused.

As of very late someone asked if I had loaded Lilo or Grub? I didn't know what they were until I Googled them and found out that they are boot loaders, and I didn't know in the beginning that I even needed a separate boot loader.

I tried to down load Grubb and Lilo but in the midst of the downloads a screen appears that tells me that my trial version of WinZip is done and that I have to buy it. I have never used it and I do not want to buy any more software now, so when I hit the X button the notice disappears and it looks like the Grub/Lilo download has been terminated.

What am I missing here? I would really like to come to the Linux party as I hear the drinks are great and the food is wonderful, but I can't stand out here in the rain forever. A step by step tutorial for a complete fool on how to get the thing working would be greatly appreciated.

Jack

---

### Post by bumanie on 2008-10-13
Not exactly sure what you mean by installing wubi over xp. 
Wubi installs inside and is regarded by windows as a 'normal' program and can be removed via add/remove in control panel. Essentially, if you have the 8.04 version of ubuntu, you open the disc whilst windows is running and choose to install it inside windows. I have only ever done one wubi install and it worked perfectly. May be you could go to add/remove and remove it and then try to install again. Otherwise there is dedicated wubi help [here]("http://ubuntuforums.org/forumdisplay.php?f=234")

---

### Post by Orange_and_Green on 2008-10-13
Hello mgguy. Welcome to the Linux world and please, please, step out of the rain and come in :)

You are not the first one to have problems with Wubi (a Linux-within-Windows type of installation). Common consensus in the forums (as far as I can tell) is that it is usually best to grant Ubuntu a tiny portion of your hard drive so that it can be on its own.

For starters, please go to this site,

[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

download a copy of Ubuntu and burn it to a CD. Then, reboot your computer and from BIOS / Boot menu select to boot from CD. This will give you several options, including "Try Ubuntu without making a change to your PC". The OS will be loaded only to memory so you can try using it a little (mind you, running from RAM alone will make it a little slower), make sure you like it and everything runs fine (including hardware detection).

Next, if you have a partition on your disk you can spare (by backing up the data and/or moving it to somewhere else), you can free it up and install Ubuntu onto it. You won't lose windows by doing so and, in fact, you will be able to access all your windows data from Ubuntu.

If you have a single-partition system, you will have the option to shrink it to make room for Ubuntu (some 10GB will be enough for a start, see also [this thread]("http://ubuntuforums.org/showthread.php?t=946210")).

I wish you the best of luck, :KS

---

### Post by Sef on 2008-10-13
Moved to WUBI forum.

---

### Post by stalkingwolf on 2008-10-13
I also have only used the wubi install once. It worked fine for me.
As stated above I used the live CD to install from within windows.
I believe that 8.04 is the first to offer this choice.  

It has been my experience that when possible installing software for ubuntu
it is easiest and best to use the methods provided by Ubuntu, IE: Synaptic,
Add/Remove, or the live cd.  Rather than from a net source.

---

### Post by mgguy on 2008-10-13
Okay Guys!  :=)  Just came back from my morning three miles and found your responses. Thanks loads!

I think that I will try an uninstall first and then go back to the retrieval process as noted. 

So, all along I thought that Linux was Linux. Now it seems that Linux is Wubi and Leniux is Ubuntu, right?

Anyway I'll get to it after fixing breakfast for "the woman that expects it". 

Jack

---

### Post by Paqman on 2008-10-13
> **mgguy said:**
> 
I followed the install directions to a T.


The best thing to do might be to burn yourself a LiveCD of Ubuntu and use it to test your system. Sometimes hardware manufacturers cut corners, and it causes problems with Linux. Go to the main Ubuntu site, download a LiveCD image of Ubuntu 8.04, burn it to a disk and boot up into it. It will run a full version of Ubuntu off the CD, and we can use it to start troubleshooting your problem. It may be as simple as adding a line of text to the boot options.

---

### Post by Orange_and_Green on 2008-10-13
Linux -> Big family of Unix-based, open source Operative Systems (examples are Red Hat / Fedora, OpenSUSE, Mandriva, Debian, Ubuntu Gentoo, PCLinuxOS, Slackware, and many others)

More properly, Linux is the Kernel (the core program) of all these Operative Systems.

Ubuntu -> Our favourite Linux "flavour" (actually called "distribution")

Wubi -> Program that allows you to install Ubuntu from windows.

---

### Post by ago on 2008-10-13
It's always better to understand what the problem is before driving people away from wubi:

1) If the issue is not Wubi specific, such as ACPI, software raids, video drivers etc, using the Live CD is not going to help as the very same issue will be there when using the Live CD, and if anything it will make users more annoyed.

2) If the issue is Wubi specific, it is either known and there is usually a workaround, or unknown and then it is a bug that has to be flagged to the devs (i.e. me).

A good start is to read the WubiGuide: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by mgguy on 2008-10-13
Okay, back again...

Down loaded Ubutu and burned it to a CD.

Rebooted the system "to complete the installation" and then came back to this forum.

Now what?  :-)

Jack

---

### Post by Orange_and_Green on 2008-10-14
> **mgguy said:**
> Okay, back again...

Down loaded Ubutu and burned it to a CD.

Rebooted the system "to complete the installation" and then came back to this forum.

Now what?  :-)

Jack

Hi Jack, welcome back :)

I think the first thing to do is pop the CD into the drive and set up your PC to boot from the CD (go into BIOS boot menu or BIOS setup by pressing a key combination right after powering up the PC - the very first screen will tell you what the key combination is for your particular system).

Then, I'd suggest you select to "Try Ubuntu without making changes to your computer" so you can get a basic feeling of how it works, and see if all of your hardware gets detected without problems.

If everything is OK, you might consider installing.

Please post again if you encounter any problems, or if you need help installing.

Good luck :KS

---

### Post by mgguy on 2008-10-14
Thanks O&G!

I have tried all that I could think of to get the screen to display the sequence of machine information as it cold boots but I came up with nothing. The screen is still going directly to the display that asks me to press a button in order to finish the boot with my preferences installed.

I suppose that what you are saying is that a boot choice can be obtained at the old black and white text information stages.

I use to get that but after trying the Ubuntu install I don't.

Do you recall what key strokes or what keys to hold down during the boot from cold that would bring me to the black and white text information screens?

If you are out there right now and reply quickly, I have to duck out and do my three miles so I will get back on line a little later.

Thank you for your patience with this. I am determined to see what Linux is like!  LOL

Jack

---

### Post by Orange_and_Green on 2008-10-14
Hi, enjoy your jogging!

For most bioses, it's a combination of some keys among F2, F10, ESC, DEL, F1, shift and alt. When I'm desperate, I often hold all these keys pressed simultaneously right after powering up the PC.

Pressing CTRL+ALT+del at the screen that asks you to continue setup should reboot the computer... for more blind pressing around ;)

Hope this helps... It really depends though, every BIOS has their own key combo it seems...

Here's a few sites that report some usual combinations.

[http://www.computerhope.com/issues/ch000192.htm](http://www.computerhope.com/issues/ch000192.htm)
[http://www.michaelstevenstech.com/bios_manufacturer.htm](http://www.michaelstevenstech.com/bios_manufacturer.htm)

Good luck :KS

---

