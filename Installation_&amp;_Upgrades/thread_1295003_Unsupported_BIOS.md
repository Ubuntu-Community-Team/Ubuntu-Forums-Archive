---
title: "Unsupported BIOS"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by taminrob on 2009-10-19
Looking for a bit of help here.  I just completed my upgrade to 9.10 and most of it went without a hitch, but I get a note during boot that my BIOS is not compatible and is unsupported.  Just to clarify, my system does work.  It is however, very slow at startup (over a minute to boot) and seems very sluggish to open programs, so I'm hoping that updating my BIOS to a current version will have a positive effect and get me closer to the boot times and smooth operations that 9.10 is supposed to bring.  
After some looking around, I found that the BIOS on my computer was from 2006, and that there is an updated version available from 06/2009.  
Now, I know that there are posts about flashing your BIOS the Ubuntu way, but to be honest, I did not understand what was required of me to get it right.  So I'm hoping that someone will have the patience to walk me through the process...now for the Tech info that I'm sure will help make more sense of my situation.

Acer Aspire 5672 wlmi
Phoenix BIOS - v1.3221 released on 02/24/2006
Latest Available BIOS from Acer for my 5670 series - 3239 released 06/2009
BIOS 3239 is a .zip
Inside the .zip are the following files -
BIOS_3239/mfc42.dll
BIOS_3239/msvcp60.dll
BIOS_3239/msvcrt.dll
BIOS_3239/Phlash9X.vxd
BIOS_3239/PHLASH.INI
BIOS_3239/PHLASH.LOG
BIOS_3239/PhlashLc.dll
BIOS_3239/PhlashNT.sys
BIOS_3239/SWinFlash.exe
BIOS_3239/winhlp32.exe
BIOS_3239/WINPHLASH.HLP
BIOS_3239/WinPhlash update SOP XP.pdf
BIOS_3239/ZB1_3239.wph

I know it wants me to run it with WINPHLASH, but that obviously doesnt work in Ubuntu.

Thanks in advance for helping me.

---

### Post by dstew on 2009-10-19
Usually only the boot loader uses BIOS in Linux. What boot loader are you using? Is it grub 2?

---

### Post by Mark Phelps on 2009-10-19
The presence of a WinFlash program indicates that what you downloaded is most probably an ACER-provided app for flashing your BIOS using MS Windows.

My own experience in flashing BIOSs for years is to use the program provided by the BIOS vendor, in this case, that would be ACER.

So, do you NOT have MS Windows installed?

IF not, my advice would be to check the ACER website to see if they have an alternate method for flashing the BIOS.  For example, my ASUS motherboard comes with an alternate booting method that allows for flashing the BIOS without starting MS Windows.

---

### Post by taminrob on 2009-10-19
I really don't know what grub I'm using, I just ran the install usb and did a fresh total install of 9.10.

I don't have windows installed, but I believe that I have an old drive that may have vista on it.  If that is the better way to do it, then that is what I will do.

In your opinion, will my updating my BIOS help at all with the sub-par performance that I am experiencing with 9.10?  The only real issue that I was expecting to have come up was with my ATI graphics card.

---

### Post by Mark Phelps on 2009-10-20
> **taminrob said:**
> I don't have windows installed, but I believe that I have an old drive that may have vista on it.  If that is the better way to do it, then that is what I will do.

I wouldn't install MS Windows, especially Vista, just to do a BIOS update.  As I suggested, check the ACER website, and your machine documentation, to see if they have a way of doing BIOS updates without running MS Windows.

> In your opinion, will my updating my BIOS help at all with the sub-par performance that I am experiencing with 9.10?  The only real issue that I was expecting to have come up was with my ATI graphics card.

BIOS update will have NOTHING to do with ATI graphics problems.  So, if that's the only reason you're trying to do the update, don't waste your time.

According to Google, your ACER Aspire has an ATI Mobility x1400 chipset -- for which there are NO ATI restricted drivers that will work with any Ubuntu version newer than 8.10 due to incompatibility with the Xorg server. Since you're getting video, you are using the open source drivers -- which is all that you have available with 9.04 or 9.10.

---

### Post by taminrob on 2009-10-20
Thanks for the reply.  I did not mean to install windows on this drive, i was just going to swap drives, flash the BIOS and then swap drives again...
this drive has never had anything but Ubuntu on it and I intend to keep it that way.  

As far as my other concerns go, I may have been unclear, I am aware of the problems that I will have with my ATI graphics and did not mean to imply that i thought that would cause any issues.  My system is just running very sluggish with 9.10 installed vs. the previous versions of Ubuntu, and being fairly inept, I wondered if having the BIOS updated would have any effect on overall system performance or even just boot performance.

---

### Post by taminrob on 2009-10-20
Just a quick update, I just swapped HDD's to one with Windows installed.  Flashed BIOS, went off without a hitch.  Swapped back to my Ubuntu 9.10 drive and upon restart I noticed a significant improvement in my startup time (probably better than half of what it was prior to updating my BIOS), and the other other sluggishness seems to have improved as well, though not as noticeably as I had hoped...perhaps upon final release some missing factor will be put in place to get me running nice and fast again.

---

### Post by Mark Phelps on 2009-10-21
Glad to see that worked for you.  Happy Ubunting!!

---

