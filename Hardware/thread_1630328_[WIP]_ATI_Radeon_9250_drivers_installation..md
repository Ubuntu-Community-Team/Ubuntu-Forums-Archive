---
title: "[WIP] ATI Radeon 9250 drivers installation."
date: 2010-11-25
forum: Hardware
---

### Post by Tekno.Statik on 2010-11-25
Well, I have been trying to get my drivers for my graphics to work since 7:00pm and it is currently 1:00am. To be honest I have no idea on what I should have done, I had so many different options I didn't know where to start, although I learned a few tricks on Terminal.

First off, how do I make sure that ATI is off my PC? I've done so many different things; I've downloaded from the Synaptic manager, gotten 3 different drivers on ATI.com, and I believe I've even gone as far as to search on the Ubuntu Software Manager for anything related to ATI. When I search for Additional Drivers my PC finds nothing (Jockey KDE & GTK on Synaptic). I have no idea if I have the xFree of xOrg, the CHECK.SH that ATI had on their site won't open either on the Terminal or as a program.

I also wasted a lot of time going through all the CHMOD that I might have to change to rwxrwxrwx for each individual folder and moved all the corresponding file from a .RPM driver that I extracted...

On the bright side I got to install the .RUN file I d-loaded from ATI, but this next step won't work: ```
aticonfig --initial -f
``` I get this: ```
aticonfig: No supported adapters detected
```

I Googled that error code, and I got this if this helps anyone else: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver).

Will keep you guys posted on this specific driver, seems like I might have to erase all possible ATI drivers and start from scratch.

---

### Post by mastablasta on 2010-11-25
what seems to be the problem? can you see picture on your monitor? if so your drivers are already loaded.
 
Linux is not windows.
 
And also ATI dropped support for these cards on newer system (last supported ubuntu was 8.04 i believe) so you will have to make do with the open source driver which is already installed by default.

---

### Post by Fafler on 2010-11-25
You should have started with checking if the 9250 is actually supported by the closed source ATI drivers...

I'm sorry, but you'll have to do with the opensource driver you are already using.

---

### Post by dandnsmith on 2010-11-25
That's a good thought fafler.

As an addition I'd like to add that I've recently tried 2 different flavours of 9250 (AGP, PCI) on a couple of systems I was re-configuring, and had no problems using whatever Ub 8.04 had provided (no specific ati driver package). I've used them on a VGA connection and also DVI (since the monitors had both) and, apart from noting the DVI gives a better display, there's been no problem.

---

### Post by Tekno.Statik on 2010-11-25
> **mastablasta said:**
> what seems to be the problem? can you see picture on your monitor? if so your drivers are already loaded.
 
Linux is not windows.
 
And also ATI dropped support for these cards on newer system (last supported ubuntu was 8.04 i believe) so you will have to make do with the open source driver which is already installed by default.

Well, I was happy with my screen, until... OH! yes, I decided to get the Software Upgrade; and my screen res changed to only 3/4 of my monitor size... eventually I was able to switch it back, but then NONE of my compizConfig features worked, I couldn't enable any kind of minimal animations. Not only that, but I forgot to mention that since Monday, I've been getting frozen blocks of images on my screen, areas where the monitor won't refresh and display the changes. Now I have my monitor on non-wide screen (3/4), The graphics glitches have stopped, but I can't change the resolution at all.

I'll continue by uninstalling every possible ATI driver and install the Open Source. I didn't know that 10.10 was not supported.

You said it as if Windows was the ultimate system. I like the challenge that Ubuntu brings, ok? I was just seeing if I could get a little help here. Thanks though.

---

### Post by Tekno.Statik on 2010-11-25
> **dandnsmith said:**
> That's a good thought fafler.

As an addition I'd like to add that I've recently tried 2 different flavours of 9250 (AGP, PCI) on a couple of systems I was re-configuring, and had no problems using whatever Ub 8.04 had provided (no specific ati driver package). I've used them on a VGA connection and also DVI (since the monitors had both) and, apart from noting the DVI gives a better display, there's been no problem.

Oh, ok. =/ I seriously didn't give it a thought at all about officially getting the video drivers and installing them myself, until the screen resolution changed and was unable to change it to any other size. and when I finally did, the glitches came in, and a lot of desktop features were not working; Ubuntu Tweak desktop corners, Application switcher was lagging way too much, (even in its SIMPLEST form), Mouse Roll-up window bar to hide temporarily, and then the glitches came whenever I opened a menu and would be on my screen for over an hour =/.

When I made the thread I assumed all of those issues would be resolved after fixing the driver compliance issue, so that's why I decided not to go into too much detail with the issues and focus more on what I've done to try to fix it.

Good to know this though, so you're running the Radeon 6250 PCI on Ubuntu 8.04?

---

### Post by Tekno.Statik on 2010-11-25
> **Fafler said:**
> You should have started with checking if the 9250 is actually supported by the closed source ATI drivers...

I'm sorry, but you'll have to do with the opensource driver you are already using.

Roget that! =]

---

### Post by dandnsmith on 2010-11-25
> Good to know this though, so you're running the Radeon 6250 PCI on Ubuntu 8.04?

Yes, that's confirmed. On that particular system, with rather old motherboard, I couldn't use the AGP version.

---

### Post by Tekno.Statik on 2010-11-29
Thread Solved. =D Thanks!

---

### Post by mastablasta on 2010-11-29
> **Tekno.Statik said:**
> You said it as if Windows was the ultimate system. I like the challenge that Ubuntu brings, ok? I was just seeing if I could get a little help here. Thanks though.
 
No it's an expression from the "famous" article found here: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
 
It's about the fact that systems just work in a very different way. ;-)
 
Enjoy the opensource drivers. if you have problems i believe there is a newer, testing version out there.

---

